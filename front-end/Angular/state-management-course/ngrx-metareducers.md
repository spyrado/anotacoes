> **IMPORTANTE:** Os `metaReducers` são executados na ordem de seu array, ou seja a ordem do array importa dependendo da lógica que você for utilizar


> **IMPORTANTE:** `META REDUCERS` ele são globais, então ao adicionar um logger por exemplo, a cada ação dispachada ele vai executar o seu metaReducer


## Oque é um metaReducer e para que ele é utilizado?

a principal diferença entre um `reducer` normal e um `metaReducer` é que o ngrx executa todos os `metaReducers` ANTES de executar o `reducer` normal.

## E quando eu vou usar isso?

por exemplo, antes de executar o meu reducer que irá armazenar no storage a informação do usuário eu posso executar o `metaReducer` que vai congelar o nosso objeto de usuário para que ele não possa ser modificado posteriormente.

## Explicação detalhada 

Os *metareducers* no NgRx são funções que envolvem um conjunto de *reducers* e podem ser usadas para adicionar funcionalidades adicionais a eles. Eles são ideais para aplicar lógica transversal que precisa ser aplicada a todas ou a múltiplas partes do estado. Aqui estão dois exemplos de uso de *metareducers* ao invés de usar um *reducer* normal:

### 1. **Log de Ações**
Um *metareducer* pode ser usado para interceptar todas as ações disparadas na aplicação e registrar essas ações para fins de auditoria ou depuração. Isso permite que você adicione facilmente a funcionalidade de log sem modificar cada *reducer* individual.

```typescript
export function loggerMetaReducer(reducer: ActionReducer<any>): ActionReducer<any> {
  return function(state, action) {
    console.log('action', action);
    console.log('state', state);
    return reducer(state, action);
  };
}

// Registro do metareducer no módulo
export const metaReducers: MetaReducer<AppState>[] = [loggerMetaReducer];
```

### 2. **Limpeza de Estado ao Logout**
Um cenário comum é limpar o estado da aplicação quando o usuário faz logout. Usando um \*metareducer\*, você pode verificar se a ação de logout foi disparada e, nesse caso, redefinir o estado da aplicação para o estado inicial.

```typescript
export function clearStateMetaReducer(reducer: ActionReducer<any>): ActionReducer<any> {
  return function(state, action) {
    if (action.type === '[Auth] Logout') {
      state = undefined;  // Reseta o estado ao inicial
    }
    return reducer(state, action);
  };
}

// Registro do metareducer no módulo
export const metaReducers: MetaReducer<AppState>[] = [clearStateMetaReducer];
```

### Vantagens dos *Metareducers*:
- **Reutilização**: Permitem aplicar a mesma lógica em múltiplos *reducers* sem duplicação de código.
- **Interceptação global**: Fornecem um ponto central para interceptar e modificar o fluxo de ações, o que pode ser mais difícil de gerenciar usando apenas *reducers* tradicionais.

Esses exemplos mostram como *metareducers* podem adicionar funcionalidades adicionais de maneira eficaz e centralizada em uma aplicação NgRx.
