# Runtime Checks


## Dicas do que não fazer para não quebrar o nosso runtime check

1. Nunca devemos alterar o `state` e retorna-lo, sempre devemos retornar um novo `state`, segue exemplo:

`EXEMPLO ERRADO:`
  ```typescript
  on(AuthActions.login, (state, action) => {
    state.user = action.user;
    return state;
  }),
  ```
  - **explicação:** seguindo dessa forma alterando o proprio estado e retornando ele nós perdemos alguns beneficios:
    1. quebra nosso time trevelling debugger, não poderiamos voltar no tempo, pois o ngrx entende que ele não sofreu uma alteração, logo perdemos o histórico com isso.
    2. fazendo dessa forma quebra no `Angular` lugares implementados com a estratégia de `OnPush`.

`EXEMPLO CERTO:`
```typescript
on(AuthActions.login, (state, action) => {
  const { user } = action;
  return { user }
}),
```

## strictStateImmutability como funciona?

> *DICA* podemos evitar isso configurando nosso StoreModule, para `runtimeChecks: {
      strictStateImmutability: true
    }`

#### segue exemplo:
```typescript
StoreModule.forRoot(
  reducers, 
  { 
    metaReducers,
    runtimeChecks: {
      strictStateImmutability: true
    }
}),
```

com isso nossa aplicação não vai permitir que algum dev sem querer altere o proprio `state` e retorne ele.

exemplo do erro: 
```diff
- TypeError: Cannot assign to read only property 'user' of object '[object Object]'
```


## strictActionImmutability como funciona?

```typescript
const authReducer = createReducer(
  initialState,
  on(AuthActions.login, (state, action) => {
    // Aqui estamos modificando diretamente a ação, o que causará um erro
    action.user.name = 'Novo Nome'; // Isso vai falhar com `strictActionImmutability: true`

    return {
      ...state,
      user: action.user
    };
  })
);
```

## strictActionTypeUniqueness como funciona?

ele impede que criem o mesmo nome de ação no sistema, as ações devem ser únicas, exemplo de como daria erro: 

```typescript
export const loadUsers = createAction('[User API] Load Users');
export const loadUsersAgain = createAction('[User API] Load Users');
```

como duas ações nesse caso estão com o mesmo nome `'[User API] Load Users'` o erro iria aparecer em nossa tela.

## strictActionSerializability como funciona?

mandar algo que não é SERIALIZÁVEL para o NGRX ele vai guardar um objeto vazio no store, com isso não conseguimos rastrear oq aconteceu na aplicação

```typescript
  auth: {
    file: {} // ao mandar um new File() para o store, ele será armazenado como objeto vazio por não ser SERIALIZÁVEL
  }
```


Aqui está um exemplo onde a configuração strictActionSerializability: true causaria um erro:


```typescript
export const uploadFile = createAction(
  '[File] Upload File',
  props<{ file: File }>() // O objeto `File` não é serializável
);
```

Neste exemplo, a ação `uploadFile` contém uma propriedade `file` do tipo `File`. O objeto `File`, que é usado para representar arquivos no navegador, não é serializável, pois ele contém métodos e propriedades que não podem ser convertidos diretamente em uma string JSON.

Em vez de passar o objeto `File`, você pode extrair apenas os dados necessários, como `fileName` e `fileContent`, e passar esses valores na ação. Dessa forma, a ação se torna serializável e a configuração `strictActionSerializability: true` não gerará um erro.

Esse cenário ajuda a manter o gerenciamento de estado limpo e previsível, garantindo que todas as ações possam ser manipuladas de forma consistente, sem surpresas ao serializar ou deserializar o estado.


