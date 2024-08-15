## Como configurar o time travelling debugger para captar os redirects da página?

1. Devemos importar o modulo no nosso app.module.ts  para que ele comece a disparar eventos de navegação:

    **arquivo:** app.module.ts

      ```typescript
        StoreRouterConnectingModule.forRoot({
          stateKey: 'router',
          routerState: RouterState.Minimal
        })
      ```

2. Após importar o modulo ele começara a disparar ações de navegação, porem isso não é o suficiente, precisamos utilizar o reducer para captar essas ações e armazenar essas mudanças dentro do nosso store, como no exemplo:
    **arquivo:** app/reducers/index.ts
    ```typescript
    export interface AppState {
      router: ActionReducer<BaseRouterStoreState, Action>
    }

    export const reducers: ActionReducerMap<AppState> = {
      router: routerReducer
    };
    ```
3. aplicando essa simples configuração o seu time travelling debugger já vai estar apto a identificar e redirecionar para as rotas.
   
> **`PONTOS IMPORTANTES`**

### a propriedade declarada no `reducer` deve ser a mesma declarada no `stateKey`, ou seja, no `stateKey` foi declarado como `router` então nosso reducer tem que estar mapeado como `router` também.

