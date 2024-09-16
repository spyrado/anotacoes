## Problema resolvido por `forRoot` e `forChild` no Angular

Em uma aplicação Angular, os métodos `forRoot` e `forChild` foram introduzidos para resolver o problema de **duplicação de instâncias de serviços** e a necessidade de diferenciar entre **configurações globais** e **locais** de módulos. Isso é especialmente importante quando se trabalha com **lazy loading** e **feature modules**.

Se eu tiver uma lib, e essa lib provê uma service dentro do modulo, se ela fizer dessa maneira:<br>
<img src="imgs/Captura%20de%20tela%202024-09-14%20215458.png" width="350"/><br>
O que vai acontecer é que em cada lugar que eu importar esse módulo, eu vou ter uma nova instancia da service `PollingService`,
porem digamos que a implementação da `PollingService` tem que ser singleton(uma vez instanciada se usa a mesma instancia no restante da aplicação).

#### exemplo:
  imagina que eu atualizo o contador dessa service para 7 na pagina 1,<br>
  quando eu for para a página 2 esse contator vai ser zerado, pq da forma como foi implementado ele vai gerar uma nova instancia, e como resolver isso? É ai que entra o nosso pattern `forRoot`

## Problema:
- Ao usar módulos carregados antecipadamente (eager-loaded) ou compartilhados, pode haver apenas uma instância de certos serviços na aplicação. No entanto, se você usar **módulos lazy-loaded**, o Angular cria um novo injetor para cada módulo carregado dessa forma, potencialmente gerando múltiplas instâncias de serviços.
- Além disso, algumas configurações precisam ser **globais** (disponíveis para toda a aplicação), enquanto outras precisam ser **locais** a um módulo específico.

## Solução com `forRoot` e `forChild`:
- O método `forRoot` permite definir **serviços globais** e configurações que são compartilhadas por toda a aplicação, garantindo que apenas **uma instância** do serviço seja criada.
  - Exemplo: O `RouterModule.forRoot()` configura o roteamento principal da aplicação e fornece uma única instância do `Router` globalmente.
  
- O método `forChild` é usado para módulos que devem ser carregados **parcialmente** ou **sob demanda** (lazy-loaded), permitindo que eles usem as mesmas rotas ou serviços sem recriar instâncias globais. Ele garante que os módulos de funcionalidade tenham suas rotas configuradas sem interferir na configuração global da aplicação.
  - Exemplo: `RouterModule.forChild()` é usado em módulos de funcionalidades para adicionar rotas específicas sem registrar um novo `Router`.

### Benefícios:
1. **Prevenção de múltiplas instâncias**: O `forRoot` evita a criação de múltiplas instâncias de serviços em toda a aplicação.
2. **Organização modular**: Facilita a configuração de módulos de recursos (feature modules) e o carregamento sob demanda.
3. **Configuração flexível**: Permite que você passe configurações diferentes dependendo do contexto (módulo global ou local).

### Exemplo:

```typescript
@NgModule({
  imports: [RouterModule.forRoot(appRoutes)], // Configuração global
})
export class AppModule {}

@NgModule({
  imports: [RouterModule.forChild(childRoutes)], // Configuração específica do módulo
})
export class FeatureModule {}
