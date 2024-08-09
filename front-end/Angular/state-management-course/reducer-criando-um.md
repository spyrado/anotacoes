### Como criar um reducer e o que significa cada parte do código abaixo:

```typescript
export const authFeatureKey = 'auth';

export const initialState: AuthState = {
  user: undefined
}

export interface AuthState {
  user: User;
}

export const authReducer = createReducer(
  initialState,
  on(AuthActions.login, (state, action) => {
    const { user } = action;
    return { user }
  })
);
```

### Explicação Simples

1. **authFeatureKey**
   - Define o nome do recurso de autenticação no estado global.
   - Útil para acessar a parte de autenticação no armazenamento de estado.
   - Essa chave ajuda a segmentar diferentes partes do estado da aplicação e é útil quando se utiliza o Redux com várias funcionalidades ou módulos.

2. **initialState**
   - Define o estado inicial da autenticação.
   - `user` começa como `undefined` (nenhum usuário está autenticado inicialmente).

3. **AuthState Interface**
   - Descreve como o estado de autenticação deve ser.
   - Contém um campo `user` que representa o usuário atual.

4. **authReducer**
   - Gerencia as mudanças no estado de autenticação.
   - Quando a ação de login (`AuthActions.login`) é executada, atualiza o estado com o usuário autenticado.
   - Usa `createReducer` para definir como o estado muda quando ações específicas ocorrem.

### Resumo

O código é parte de um sistema que gerencia o estado de autenticação. Ele define como armazenar o usuário atual e como atualizar esse estado quando alguém faz login.
