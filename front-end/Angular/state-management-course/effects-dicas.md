> **DICA:** Sempre que estiver criando um novo effect desligue sua aplicação para evitar loop infinito

#### Ao invez de utilizarmos essa estrutura para criar um side effect

```typescript
const login$ = this.actions$
  .pipe(
    ofType(AuthActions.login),
    tap(action => 
      localStorage.setItem('user', JSON.stringify(action.user)))
  );

login$.subscribe(); // Melhor forma é criar um "createEffect" ele já da um auto subscribe para nós.
```

#### melhorando a forma a cima:

```typescript
login$ = createEffect(() => this.actions$
  .pipe(
    ofType(AuthActions.login),
    tap(action => 
      localStorage.setItem('user', JSON.stringify(action.user)))
  ),
  { dispatch: false }
);
```

#### ganhos ao implementar da forma acima:

1. removemos o `login$.subscribe();` pois o createEffect já da um auto subscribe

## Explicação do código

Passo a Passo:

- createEffect:
  - A função createEffect é usada para criar um efeito no NgRx. Ela recebe como argumento uma função que retorna um Observable que representa o efeito.

- this.actions$.pipe(...):
  -  this.actions$ é um observable que emite todas as ações despachadas no sistema. O pipe é utilizado para transformar ou reagir a essas ações.

- ofType(AuthActions.login):
  - O operador ofType filtra as ações, permitindo que o efeito reaja apenas a ações específicas, neste caso, AuthActions.login. Ou seja, este efeito só será acionado quando uma ação de login for despachada.

- tap(action => ...):
  - O operador tap é utilizado para realizar efeitos colaterais, como interações com APIs ou armazenamento, sem modificar os dados que estão sendo passados adiante na cadeia. Aqui, ele está sendo usado para armazenar o objeto user no localStorage quando a ação de login é despachada.

- localStorage.setItem('user', JSON.stringify(action.user)):
  - Esta linha de código grava o usuário que foi incluído na ação login no localStorage do navegador, serializando o objeto user como uma string JSON.

- { dispatch: false }:
  - A chave { dispatch: false } passada como segundo argumento para createEffect indica que, após a execução do efeito, nenhuma nova ação deve ser despachada.

### Por que usar dispatch: false?

- Efeito de Lado (Side Effect) sem Novo Despacho:
  - Normalmente, os efeitos no NgRx são usados para lidar com operações assíncronas ou complexas que resultam em uma nova ação sendo despachada, como, por exemplo, uma ação de sucesso ou falha após uma chamada de API. No entanto, há casos como o deste exemplo, onde o efeito não precisa despachar uma nova ação — ele só precisa executar algum código (neste caso, salvar o usuário no localStorage). Usar { dispatch: false } diz ao NgRx para não esperar que o efeito resulte em uma nova ação.

- Prevenção de Ciclos Infinito:
  - Se um efeito fosse, inadvertidamente, programado para despachar uma ação que ele mesmo está ouvindo, poderia causar um ciclo infinito de despachos. Declarar dispatch: false ajuda a evitar esse tipo de problema em cenários como este, onde o objetivo do efeito não é despachar novas ações.

- Melhor Performance:
  - Evitar o despacho desnecessário de ações pode melhorar a performance do aplicativo, especialmente em casos onde o efeito é simples e não requer interações adicionais com a store do NgRx.
