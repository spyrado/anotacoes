# Dicas para otimizar os selectors no NGRX


Ao utilizar um subscribe global do store, nós estamos ouvindo por mudanças a todo momento que acontecer QUALQUER disparo de ação na aplicação, porem muitas das vezes você só queria verificar quando o usuário faz o login e quando ele faz o logout.

e você acaba que coloca a sua lógica dentro do store global, com isso sua funcionalidade vai ficar executando e executando ao longo da vida da aplicação, mas o login e logout só acontece 2x na aplicação e nada além disso.

#### ao invez de fazer algo como o exemplo abaixo que é `BAD PERFORMANCE`:

```typescript
private listenForStoreChanges() {
  this.isLoggedIn$ = this.store
    .pipe(map(store => !!store['auth'].user));

  this.isLoggedOut$ = this.store
    .pipe(map(store => !store['auth'].user))
}
```

### DICA 1:
---
substituir o `map` pelo `select` do `@ngrx/store`, ele vai identificar se o valor anterior é igual ao atual, caso for ele não vai emitir esse valor, com isso paramos de ficar emitindo valores adoidadamente.

```diff
private listenForStoreChanges() {
  this.isLoggedIn$ = this.store
-  .pipe(map(store => !store['auth'].user))
+    .pipe(select(store => !!store['auth'].user));

  this.isLoggedOut$ = this.store
-    .pipe(map(store => !store['auth'].user))
+    .pipe(select(store => !store['auth'].user))
}
```

#### **POREM**, como estamos lidando com o `global state` da aplicação se o estado mudar de: 

```JSON
{
  "auth": {
    "user": {
      "nome": "Fulano"
    }
  }
}
```

#### para

```JSON
{
  "auth": {
    "user": {
      "nome": "Fulano"
    }
  },
  "cursos": []
}
```

a nossa lógica dentro de `store => !store['auth'].user` que só era pra validar quando auth mudar, continuará a ser executada, pois se o `global state` mudar ele vai passar a executar a lógica dentro do `select`, e se a lógica for mais complexa que uma simples conversão de boolean a performance da nossa aplicação será afetada por conta disso.

> .pipe(select(`store => !store['auth'].user`)).


### DICA 2:

Para melhorar o cenário anterior, podemos utilizar um `createSelector()` que vai colocar em cache o valor anterior executado dentro de sua lógica e se esse valor não mudar ele não vai disparar novamente o selector, com isso temos uma dupla validação, tanto do `select` quanto do `createSelector()`.

em resumo irá ficar assim:

`auth.selectors.ts`

```typescript
import { createSelector } from "@ngrx/store";

export const isLoggedIn = createSelector(
  state => state['auth'],
  (auth) => !!auth.user
)
```

`app.component.ts`

```typescript
this.isLoggedIn$ = this.store
  .pipe(select(isLoggedIn));
```

agora além dele emitir eventos apenas quando o estado geral da aplicação mudar com o uso de `select` nosso `createSelector` nomeado como `isLoggedIn` vai executar a lógica e guardar em memória, e ele só irá disparar o evento novamente caso o resultado for diferente do anterior guardado em memória.