# Dicas para otimizar o NGRX


Ao utilizar um subscribe global do store, nós estamos ouvindo por mudanças a todo momento que acontecer QUALQUER disparo de ação na aplicação, porem muitas das vezes você só queria verificar quando o usuário faz o login e quando ele faz o logout.

e você acaba que coloca a sua lógica dentro do store global, com isso sua funcionalidade vai ficar executando e executando ao longo da vida da aplicação, mas o login e logout só acontece 2x na aplicação e nada além disso.

#### ao invez de fazer algo como:

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
substituir o map pelo select do @ngrx/store, ele vai identificar se o valor anterior é igual ao atual, caso for ele não vai emitir esse valor, com isso paramos de ficar emitindo valores adoidadamente.

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

#### a nossa lógica dentro de: 

`store => !store['auth'].user`

continuará a ser executada, pois se o `global state` mudar ele vai passar a executar a lógica dentro do `select`, e se a lógica for mais complexa que uma simples conversão de boolean a performance da nossa aplicação será afetada por conta disso.

.pipe(select(`store => !store['auth'].user`)).
