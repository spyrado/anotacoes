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
  "[Login Page] User Login"
);
```

### Convenções de Nomeação

- **Parte entre colchetes (\`[]\`)**: Indica de onde a ação foi disparada. Neste exemplo, a ação é disparada da "Login Page".
- **Segunda parte**: Descreve a ação propriamente dita. No exemplo, a ação é quando ocorre o login do usuário, descrito como "User Login".

Seguir essas convenções ajuda a manter o código mais legível e facilita a compreensão de onde as ações são originadas e o que elas representam. Além disso, usar arquivos separados para ações torna o código mais modular e fácil de gerenciar em projetos maiores.
