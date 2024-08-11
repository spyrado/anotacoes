# Porque criar um createFeatureSelector ?

Ao criar um seletor utilizando o metodo `createFeatureSelector` estamos colocando um `type safe` no nosso seletor, exemplo:

#### sem feature selector

```typescript
export const isLoggedIn = createSelector(
  state => state['auth'], // por não ser tipado acessamos assim
  (auth) => !!auth.user
);
```

#### adicionando o `type safe`

```typescript
export const selectAuthState = createFeatureSelector<AuthState>('auth');

export const isLoggedIn = createSelector(
  selectAuthState,
  (auth) => !!auth.user
);
```

**explicação:** ao adicionarmos o `createFeatureSelector` estamos falando como parametro que o nome da feature a ser acessada é o auth dentro da estrutura do estado da nossa aplicação, e que o retorno de auth é do tipo `AuthState`, com isso, podemos remover o mapping que estavamos fazendo de: `state => state['auth']` por: `selectAuthState`, o retorno do nosso feature selector é o usuário.