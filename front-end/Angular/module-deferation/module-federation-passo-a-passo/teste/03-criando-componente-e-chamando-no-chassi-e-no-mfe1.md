# Criando componente e chamando tanto no chassi(shell) quando no mfe

## MFE1

1.  entre em `cd workspace`
2.  digite `ng g m flights --route=flights --module=app --project=mfe1`
3.  remova a rota de flights que gerou no `app-routing` do `mfe1`
4.  remova da pasta /flights os `.html`, `.scss` `.spec.ts` e por ultimo o `.component.ts`
5.  deve ficar apenas os arquivos: `flights-routing.module.ts` e `flights.module.ts`
6.  remova o `FlightsComponent` de dentro de `flights-routing.module.ts` e `flights.module.ts`
7.  acabamos de criar a estrutura base para receber componentes referente a flights
    - a estrutura deveria ficar assim:
      ```
      /flights
        - flights-routing.module.ts
        - flights.module.ts
      ```
8.  agora vamos criar nosso componente que será reutilizado dentro do nosso chassi.
9.  o nome dele é `flights-search`
10. entre em `cd workspace`
11. digite `ng g m flights/flights-search --project=mfe1`
12. digite `ng g c flights/flights-search --project=mfe1`
13. entre no `flights-search.module` e exporte `FlightsSearchComponent`
14. adicione essa rota em `flights-routing`:
    ```
    {
      path: 'flights-search',
      component: FlightsSearchComponent
    }
    ```

## SHELL

1. vamos carregar `FlightsModule` do `mfe1` utilizando lazy-loading
2. primeiro vá até `app-routing` e adicone essa rota:

   ```
   const routes: Routes = [
     // {
     //   path: '',
     //   component: HomeComponent,
     //   pathMatch: 'full',
     // },
     {
       path: 'flights',
       loadChildren: () => import('mfe1/Module').then((m) => m.FlightsModule),
     },
   ];
   ```

   - ignore a rota comentada por enquanto, vamos ajustar depois.
   - **IMPORTANTE** seu modulo `mfe1/Module` vai dar o erro `Cannot find module 'mfe1/Module' or its corresponding type declarations`, pois o typescript não consegue identificar como um módulo, para resolver isso precisamos criar um arquivo
     - passo a passo para resolver o problema:
       1. crie um arquivo chamado decl.d.ts dentro de `projects/shell/src/decl.d.ts`
       2. e dentro dele cole isso: `declare module 'mfe1/Module';`
       3. e pronto o erro vai parar de exibir o type agora consegue identificar o modulo.

3. Além disso, precisamos informar ao webpack que todos os caminhos que começam com mfe1 apontam para outro projeto. Isso pode ser feito no webpack.config.js que foi gerado, localizado em : `workspace/projects/shell/webpack.config.js`
4. provavelmente ele já está configurado certo, mas caso não esteja segue uma foto de como ele deveria ficar:
   ![](./imagens/webpack-config-js.png)
