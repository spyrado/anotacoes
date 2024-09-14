### O que são Entities no NgRx?

No NgRx, **Entities** são uma maneira de gerenciar coleções de dados no estado da aplicação de forma eficiente. Elas permitem armazenar e acessar grandes quantidades de dados de maneira organizada e otimizada, utilizando um formato normalizado.

### Benefícios de Utilizar Entities no NgRx

1. **Normalização dos Dados**: Armazena dados em um formato de dicionário (chave-valor), facilitando o acesso e a manipulação dos dados.
2. **Simplificação do Código**: O NgRx Entity oferece funções utilitárias para operações comuns (adicionar, atualizar, remover), reduzindo o código boilerplate.
3. **Desempenho**: Operações em grandes conjuntos de dados são mais rápidas e eficientes devido ao uso de dicionários.
4. **Selectors Automáticos**: Facilita a criação de selectors para acessar os dados no estado.

### Exemplo de Uso

```typescript
import { EntityAdapter, createEntityAdapter } from '@ngrx/entity';

// Definindo a entidade
export interface Livro {
  id: string;
  titulo: string;
  autor: string;
}

// Criando o adapter da entidade
export const livroAdapter: EntityAdapter<Livro> = createEntityAdapter<Livro>();

// Definindo o estado inicial
export interface LivroState extends EntityState<Livro> {
  carregando: boolean;
}

export const estadoInicial: LivroState = livroAdapter.getInitialState({
  carregando: false,
});

// Usando o adapter no reducer
import { createReducer, on } from '@ngrx/store';
import * as LivroActions from './livro.actions';

export const livroReducer = createReducer(
  estadoInicial,
  on(LivroActions.carregarLivrosSucesso, (state, { livros }) =>
    livroAdapter.setAll(livros, state)
  )
);

// Selectors automáticos
export const {
  selectIds,
  selectEntities,
  selectAll,
  selectTotal
} = livroAdapter.getSelectors();
