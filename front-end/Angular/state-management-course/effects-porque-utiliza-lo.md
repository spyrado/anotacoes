### Por que devo utilizar `Effects` no NgRx?

Os `Effects` no NgRx são uma parte fundamental da arquitetura de gerenciamento de estado em aplicações Angular que utilizam essa biblioteca. Eles são usados para lidar com operações assíncronas e para permitir a separação clara das responsabilidades no seu código. Aqui estão algumas razões pelas quais você deve usar `Effects` no NgRx:

1. **Gerenciamento de Operações Assíncronas**:  
   `Effects` permitem que você gerencie operações assíncronas, como chamadas HTTP, interações com APIs, acesso ao armazenamento local e outras operações que não devem ser executadas diretamente dentro de reducers (que devem ser funções puras).

2. **Manter Reducers Puros**:  
   Os reducers no NgRx são responsáveis por produzir um novo estado baseado nas ações despachadas, mas eles devem ser funções puras, ou seja, sem efeitos colaterais. `Effects` permitem que você mantenha essa pureza ao mover a lógica assíncrona e de efeitos colaterais para fora dos reducers.

3. **Melhor Organização do Código**:  
   Usar `Effects` ajuda a manter seu código organizado. Em vez de espalhar chamadas de API ou outras operações assíncronas por todo o aplicativo, você pode centralizar essa lógica nos `Effects`, o que facilita a manutenção e o entendimento do fluxo de dados na aplicação.

4. **Decoupling de Lógica de Negócio e UI**:  
   `Effects` permitem que a lógica de negócios que não está diretamente relacionada à interface do usuário seja mantida separada. Isso facilita testes e torna o código mais modular e reutilizável.

5. **Respostas a Múltiplas Ações**:  
   Um único `Effect` pode responder a múltiplas ações e despachar múltiplas ações de volta ao sistema, permitindo um fluxo de dados mais complexo, como encadeamento de ações ou tratamento de erros.

6. **Interoperabilidade com Outras Bibliotecas RxJS**:  
   Como os `Effects` são baseados em `Observables` do RxJS, eles podem ser facilmente combinados e manipulados usando operadores RxJS, o que dá grande flexibilidade para criar fluxos de dados complexos.

Em resumo, utilizar `Effects` no NgRx permite que você construa uma aplicação mais modular, fácil de manter e que respeita os princípios de separação de responsabilidades e pureza das funções.