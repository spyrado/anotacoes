# Ver qual vai ser o titulo

1. crie um arquivo chamado app.routes.ts dentro de `workspace/projects/shell/src/app`
2. cole o conteudo abaixo:
   ```
   export const APP_ROUTES: Routes = [
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
3. o typescript vai ficando dando erro no 'mfe1/Module', pois ele é apenas um caminho virtual apontando para outro projeto, ele não existe no shell.
4. para dar um bypass nisso crie um arquivo com o nome: `decl.d.ts` dentro de `projects/shell/src/decl.d.ts`
5. cole esse conteúdo dentro, ele vai falar para o typescript que o import 'mfe1/Module' existe.<br>
   `declare module 'mfe1/Module';`
6. e pronto o erro vai sumir.
7. Além disso, precisamos informar ao webpack que todos os caminhos que começam com `mfe1` apontam para outro projeto. Isso pode ser feito no workspace/projects/shell/`webpack.config.js` gerado:

   ```
   const { shareAll, withModuleFederationPlugin } = require('@angular-architects/module-federation/webpack');

   module.exports = withModuleFederationPlugin({

     remotes: {
       "mfe1": "http://localhost:4201/remoteEntry.js",
     },

     shared: {
       ...shareAll({ singleton: true, strictVersion: true, requiredVersion: 'auto' }),
     },

   });
   ```

8. explicação: A seção `remotes` mapeia o caminho mfe1 para o microfrontend compilado separadamente - ou para ser mais preciso: para sua entrada remota. Este é um pequeno arquivo gerado pelo webpack ao construir o controle remoto. O Webpack carrega-o em tempo de execução para obter todas as informações necessárias para interagir com o microfrontend.
9. agora vamos voltar para o `mfe1`
10. crie um arquivo chamado app.routes.ts dentro de `workspace/projects/mfe1/src/app/app.routes.ts`
11. cole esse conteúdo dentro do arquivo:
    ```
    export const APP_ROUTES: Routes = [
        { path: '', component: HomeComponent, pathMatch: 'full'}
    ];
    ```
