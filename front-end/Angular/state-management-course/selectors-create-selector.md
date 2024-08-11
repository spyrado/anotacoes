### Como funciona um `createSelector`?

Um `createSelector` é uma função poderosa que permite criar selectors no `NgRx`. Veja o exemplo abaixo:

```typescript
export const isLoggedIn = createSelector(
  state => state['auth'],
  (auth) => !!auth.user
);
```

Podemos criar várias funções dentro do `createSelector`, mas a última função é sempre a `"project function"`. Esta é a função que dispara o resultado final do selector.
### Reutilizando selectors para criar outros selectors

Selectors podem ser reutilizados em outros selectors para compor lógicas mais complexas. Veja o exemplo a seguir:

```typescript
import { createSelector } from "@ngrx/store";

export const isLoggedIn = createSelector(
  state => state['auth'],
  (auth) => !!auth.user
);

export const isLoggedOut = createSelector(
  isLoggedIn,
  loggedIn => !loggedIn
);
```

O primeiro selector verifica se o usuário está logado e retorna `true` ou `false`.

O segundo selector reutiliza o primeiro para verificar se o usuário está logado e então inverte o resultado. Se o usuário não estiver logado (`loggedIn` for `false`), o `isLoggedOut` retorna `true`, indicando que o usuário está deslogado.

Esse formato facilita a compreensão dos conceitos e reutilização de selectors no `NgRx`.