# Como Criar uma Action no NgRx

## Criando uma Action Simples

Podemos criar uma action diretamente ao despachá-la para o store usando o método `dispatch`. Aqui está um exemplo básico:

```typescript
this.store.dispatch({
  type: 'Login Action',
  payload: user
});
```

## Criando uma Action Elaborada

Para uma abordagem mais organizada e escalável, é recomendado criar um arquivo específico para cada conjunto de actions relacionadas. Por exemplo, para ações de autenticação, você pode criar um arquivo chamado `auth.actions.ts`.

### Exemplo de Arquivo de Ação: `auth.actions.ts`

Dentro do arquivo, você pode definir ações usando a função `createAction` do NgRx:

```typescript
import { createAction } from '@ngrx/store';

export const login = createAction(
  "[Login Page] User Login",
  props<{ user: User }>
);
```

### Primeiro Parâmetro: `"[Login Page] User Login"`

O primeiro parâmetro da função `createAction` é uma string que representa o **tipo da ação**. Este parâmetro é crucial porque:

1. **Identificação da Ação**: Ele serve como um identificador único para a ação dentro do store do NgRx. Isso é importante porque o reducer utiliza esse tipo para determinar como o estado deve ser alterado em resposta à ação.

2. **Convenção de Nomeação**:
   - **Parte entre colchetes (`[]`)**: Indica de onde a ação foi disparada. Neste exemplo, a ação é disparada da "Login Page".
   - **Segunda parte**: Descreve a ação propriamente dita. No exemplo, a ação é quando ocorre o login do usuário, descrito como "User Login".

Seguir essas convenções ajuda a manter o código mais legível e facilita a compreensão de onde as ações são originadas e o que elas representam. Além disso, usar arquivos separados para ações torna o código mais modular e fácil de gerenciar em projetos maiores.
### Segundo Parâmetro: `props<{ user: User }>()`

O segundo parâmetro, `props`, é uma função que permite definir um **payload** para a ação. Aqui está o que isso significa:

1. **Payload da Ação**: O `props` é utilizado para especificar quaisquer dados adicionais (o payload) que você deseja enviar junto com a ação. No exemplo, `{ user: User }` define que a ação transporta um objeto do tipo `User`.

2. **Tipagem Estrita**: Utilizando `props`, você aproveita o sistema de tipos do TypeScript para garantir que o payload da ação esteja de acordo com a estrutura esperada. Isso promove segurança de tipos, garantindo que os dados passados na ação estejam corretos, e melhora a experiência de desenvolvimento com autocompletação e verificações de tipo no editor.

3. **Facilita o Manuseio dos Dados**: Nos reducers e effects, você poderá acessar o payload da ação de forma direta e segura, sabendo exatamente quais dados estão disponíveis.