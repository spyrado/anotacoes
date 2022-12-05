# Cypress

## Início

npm install cypress -> instala o cypess
cypress open -> roda o cypress

`/// <reference types="Cypress" />` -> adicione essa linha no começo de um arquivo `nome_arquivo.spec.js` para o vs code<br> entender que estamos trabalhando com cypress

<br/>

---

<br/>

## DEBUG

Utilize o debug, para entender mais sobre o que ocorre.

> **Nota:** Após abrir o inspecionar e cair no ponto de debug só de o play( deixe passar o debug ), e vai aparecer<br>
> um log do que ocorreu, segue exemplo:

`cy.get('#buttonSimple').should('have.value', 'Clique Aqui').debug();` -> com o debug no `should` ele vai abrir infos sobre oq ocorreu no `should`<br>

![](./images/debug-console.png)

`cy.get('#buttonSimple').click().debug().should('have.value', 'Clique Aqui');` -> com o debug no `click` ele vai abrir infos sobre oq ocorreu no `click`<br>

![](./images/debug-click.png)

<br/>

---

<br/>

## PAUSE

O comando `.pause()` ele serve como um debugger, porem nós conseguimos ver o passo a passo do que está ocorrendo,<br>
podemos dar um `next step` na ferramenta ai iremos acompanhar passo a passo do comportamento da ferramenta.

> **Nota:** Se os comandos estiverem aninhados eles serão executados de uma vez e você não vai conseguir dar um <br>
> `next step` entre eles para isso vc pode durante a analise, separar esse `aninhamento`.

#### Exemplo de aninhamento:

```
  cy.pause();
  cy.title()
    .should('be.equal', 'Campo de Treinamento')
    .and('contains', 'Campo');
```

#### Exemplo do funcionamento do pause:

O comando abaixo vai dar um pause antes de executar os 2 outros comandos, ai `na ferramenta` eu posso dar um `next`<br>
ai ele vai cair nessa primeira validação: `cy.title().should('be.equal', 'Campo de Treinamento');`<br>
e depois eu posso dar outro `next` ai ele cai na proxima validação (`cy.title().should('contains', 'Campo');`) e por ai vai

```
  cy.pause();
  cy.title().should('be.equal', 'Campo de Treinamento');
  cy.title().should('contains', 'Campo');
```

<br/>

---

<br/>

## Asserts

Podemos fazer de algumas formas umas menos intuitivas como:<br>

Todas abaixo tem o mesmo resultado, o que muda é a leitura, e na minha opiniao `to be equal` seria o ideal nesse caso

`expect(1).equal(1);` -> vai dar o mesmo resultado<br>
`expect(1).to.equal(1);` -> vai dar o mesmo resultado<br>
`expect(1).to.be.equal(1);` -> vai dar o mesmo resultado

<br/>

---

<br/>

## Asserts para objetos

`expect(obj).to.be.deep.equal({ a: 1, b: 2 });` -> `.deep` Verifica TODAS as propriedades dentro do objeto<br>
`expect(obj).eql({ a: 1, b: 2 });` -> é um shortcut do comando a cima <br>
`expect(obj).include({ a: 1);` -> Verifica se EXISTE AQUELA PROPRIEDADE/VALOR dentro daquele objeto

```

  it('Equality for Objects', () => {

  const obj = {
    a: 1,
    b: 2
  };
  // essa é uma forma errada, pq o js entende que é outro objeto outra referencia, para isso devemos utilizar deep
  // expect(obj).to.be.equal({ a: 1, b: 2 }); // ERRADA
    expect(obj).to.be.deep.equal({ a: 1, b: 2 }); // CERTA
    expect(obj).eql({ a: 1, b: 2 }); // SHORTCUT DE DEEP
    expect(obj).include({ a: 1 }); // VERIFICA SE EXISTE AQUELA PROP/VALUE DENTRO DO OBJ
  });

```

<br/>

---

<br/>

## Asserts para Arrays

`expect(array).to.be.members([1,2,3]);` -> Deve possuir exatamente os mesmos numeros<br>
`expect(array).to.include.members([1,3]);` -> Deve ter esses numeros dentro do array.<br>
`expect(array).not.to.be.empty;` -> Nao deve estar vazio<br>
`expect([]).to.be.empty;` -> Deve estar vazio<br>
`expect([]).length(0);` -> variação de implementacao do deve estar vazio<br>
`expect([1,2]).length.greaterThan(0);` -> deve ser maior que 0<br>

<br/>

---

<br/>

## Asserts para ELEMENTOS HTML

`cy.get('#buttonSimple').should('have.value', 'Clique Aqui');` -> pelo `have.value` eu verifico o texto do botão

<br/>

---

<br/>

## ASYNC

Trabalhando com coisas asyncronas no cypress, uma delas é pegar o título de uma página, exemplo:

Se eu digitar:<br>
`cy.visit('url_da_pagina');` e logo após isso digitar:<br>
`cy.title()` vai dar erro, pois ele retorna uma função "encadeada"(`chained`) e para testar funções encadeadas utilizamos o `should`, segue um exemplo:<br>
`cy.title().should('be.equal', 'Campo De Treinamento');` ele é igual a um `expect` só que um pouco diferente.

Mas o cypress nos preparou um metodo chamado should,

```
it('should visit a page and assert a title', () => {
  cy.visit('https://wcaquino.me/cypress/componentes.html');
  cy.title().should('be.equal', 'Campo');
});
```
Também podemos precisar trabalhar com promises do cypress e promises do js, aqui vai um exemplo<br>
[clique nesse link para ser redirecionado para o exemplo](#3-exemplo-de-uso-de-promises-com-async-do-js-vs-async-do-cypress)

<br/>

---

<br/>

## SHOULD

> **Nota:** o `should` pode ser utilizado encadeado, ou seja eu posso fazer algo como:

```
cy.title()
  .should('be.equal', 'Campo de Treinamento')
  .should('contains', 'Campo');
```

> **Nota:** mas para deixarmos um pouco mais legível utilizamos `and` no lugar do segundo should para mais, segue exemplo:

```
cy.title()
  .should('be.equal', 'Campo de Treinamento')
  .and('contains', 'Campo');
```

> O should ele cria uma assertiva, e assertivas são automaticamente retentadas durante um periodo de tempo e a condição
> para elas pararem de ser retentadas é caso de sucesso na acertiva ou o tempo delas acabem ( geralmente o padrão é 4 segundos de retentativa ).

`CENÁRIO 1:` No exemplo abaixo se o titulo for diferente de Campo De Treinamento, ela vai executar por 4 segundos e somente depois vai disparar um erro.<br>
`CENÁRIO 2:` Agora se no exemplo abaixo o título for igual ela vai executar até que obtenha a informação do título.

`RESULTADO CENÁRIO 1:` O tempo de execução demorou 4 segundos, pois não existia aquele título e o should ficou reexecutando até dar o tempo de timeout( que são 4 segundos ) <br>
`RESULTADO CENÁRIO 2:` O tempo de execução demorou 0.35 segundos, pois o título inserido era exatamento o esperado.

`cy.title().should('be.equal', 'Campo De Treinamento');`

<br/>

---

<br/>

## Hooks

`before` -> Ele é executado UMA vez ANTES de TODOS os Testes, exemplo:

Aqui eu digo que antes de qualquer teste, entre na pagina XPTO.

```
  before(() => {
    cy.visit('https://wcaquino.me/cypress/componentes.html');
  });
```

`beforeEach` -> Para cada `it` ele executa uma vez, exemplo:

No exemplo abaixo eu quero que a cada nova execução de teste ele deixe de um reload na pagina,<br>
assim eu garanto que a nova execução vai ser em um cenário limpo.

```
  beforeEach(() => {
    cy.reload();
  });
```

> **Nota:** O before e beforeEach eles seguem a lógica deles, POREM se eles estiverem dentro de um describe<br>
> eles só vao executar tudo dentro do describe, e nada fora, EXEMPLO:

No exemplo abaixo o `teste 3` não contem as execuções de `before` e `beforeEach`

```
  describe('Teste XPTO', () => {

    before(() => {
      // executa isso 1
    });

    beforeEach(() => {
      // executa isso 2
    });

    it('teste 1', () => {

    });

    it('teste 2', () => {

    });

  });

  it('teste 3', () => {

  });
```

<br/>

---

<br/>

## Seletores

O cypress dependendo de como você selecionar um elemento ele pode não identificar aquele elemento, segue um exemplo:<br>
`cy.get('#elementosForm:sugestoes')` -> Essa forma de selecionar um elemento é errada no cypress, ele considera `:` como caracter especial, Para fazer com que ele considere o `:` devemos usar `\\:`

Forma correta:<br>
`cy.get('#elementosForm\\:sugestoes')` -> Obviamente que aqui é só um cenário, o ideal não é utilizar um id dessa forma,
de preferencia utilize data-attributes para lidar com cypress

<br/>

---

<br/>

## Type

<br>

> **Nota:** Doc de referencia: https://docs.cypress.io/api/commands/type#Usage

<br>

Podemos ao longo do digito(type) manipular ele e dar um backspace por exemplo para remover algum caracter,<br>
simulando um comportamento do usuário.

Nesse exemplo eu estou digitando `Teste12345` e removendo via {backspace} os ultimos 2 digitos Teste123`45`,<br>
resultando em `Teste123`, e depois eu verifico se o resultado esperado confere.

```
cy.get('[data-cy=dataSobrenome]')
  .type('Teste12345{backspace}{backspace}')
  .should('have.value', 'Teste123');
```

### Argumentos

<br>

> **Nota:** Só lembrando que todos os argumentos existem na doc: https://docs.cypress.io/api/commands/type#Arguments

<br>

Sequence Notes<br>
{{} Types the literal { key<br>
{backspace} Deletes character to the left of the cursor<br>
{del} Deletes character to the right of the cursor<br>
{downArrow} Moves cursor down<br>
{end} Moves cursor to the end of the line<br>
{enter} Types the Enter key<br>
{esc} Types the Escape key<br>
{home} Moves cursor to the start of the line<br>
{insert} Inserts character to the right of the cursor<br>
{leftArrow} Moves cursor left<br>
{moveToEnd} Moves cursor to end of typeable element<br>
{moveToStart} Moves cursor to the start of typeable element<br>
{pageDown} Scrolls down<br>
{pageUp} Scrolls up<br>
{rightArrow} Moves cursor right<br>
{selectAll} Selects all text by creating a selection range<br>
{upArrow} Moves cursor up<br>

Text passed to .type() may also include any of these modifier character sequences:

Sequence Notes<br>
{alt} Activates the altKey modifier. Aliases: {option}<br>
{ctrl} Activates the ctrlKey modifier. Aliases: {control}<br>
{meta} Activates the metaKey modifier. Aliases: {command}, {cmd}<br>
{shift} Activates the shiftKey modifier.<br>

<br/>

---

<br/>

## Inputs

<br>

`cy.get('seletorDoMeuInput').type('texto xpto')` -> insere um texto dentro do input
`cy.get('seletorDoMeuInput').clear()` -> limpa o campo do input
`cy.get('seletorDoMeuInput').type('texto xpto', { delay: 2000 )` -> insere um texto dentro do input, porem com delay de 2 segundos<br>
Dois pontos importante sobre o `delay`

1.  Interessante quando você deseja VISUALIZAR o que a funcionalidade está fazendo
2.  As vezes é um campo de busca que tem um debounce de 3 segundos ou 500 ms para disparar para o backend,<br>
    ai voce pode trabalhar com o `delay` nesses casos para testar esses cenários

<br/>

---

<br/>

## Radio Buttons

<br>

Exemplo de teste:

```
cy.get('#formSexoMasc')
  .click()
  .should('be.checked');
cy.get('#formSexoFem')
  .should('be.not.checked');
```

> **Nota:** Geralmente um radio button é composto por 2 ou mais items, e eles são agrupados pela propriedade name

```
cy.get('[name="formSexo"]')
      .should('have.length', 2);
```

<br/>

---

<br/>

## CheckBox

<br>

Diferentemente de um `radiobutton` um `checkbox` pode ter varios checks diferentes checkados, no cypress
podemos pegar todos os checks `pelo seu name que geralmente um grupo de checkbox tem um unico name`

Segue exemplo: <br>
Aqui eu estou pegando todos os checkboxes com name formComidaFavorita e pedindo para o cypress clicar em todos ( checked === true )<br>
`cy.get('[name=formComidaFavorita]').click({ multiple: true })`

<br/>

---

<br/>

## Click

<br>

`.click()` -> clica no elemento<br>
`.click({ multiple: true })` -> clica em mais de um elemento <br>
( apenas passar o parametro quando o `seletor for um array` )

<br/>

---

<br/>

## Combos / Selects

<br>

Como validar um select?

Por padrão o `.select('')` ele pode validar tanto o valor visual para o usuário, quanto o valor enviado para<br>
o endpoint.

POREM, para verificar no `.should('have.value', 'xpto')` o should aceita apenas o valor enviado para o endpoint.

Segue exemplo:

```
cy.get('[data-test=dataEscolaridade]')
  .select('2o grau completo') // valor visual para o usuário
  .should('have.value', '2graucomp') // valor da propriedade value do html <option value="2graucomp">2o grau completo</option>
```

<br/>

---

<br/>

## Combo Multiplo / Multi Selects

<br>

Como validar um combo de select?

Para selecionar mais de um item, devemos utilizar um array e passar apenas as props values das options, ou seja<br>
`<option value="nada">Texto de Exemplo</option>`

```
cy.get('[data-testid=dataEsportes]')
  .select(['nada', 'natacao', 'Corrida'])
```

<br/>

---

<br/>

## Retentativas / Retrys

<br>

Em um cenário aonde você clica em um botão e um campo demora um tempo para aparecer, temos o seguinte problema
caso nós tentarmos encadear o should para verificar o estado do elemento.

O Cypress tem uma peculiaridade, exemplo, pq esse comando funciona?

```
cy.get('#novoCampo').should('not.exist');
cy.get('#novoCampo').should('exist');
```

E esse não funciona?

```
cy.get('#novoCampo')
  .should('not.exist')
  .should('exist');
```

A Explicação é simples, quando você utiliza um get(`cy.get('#novoCampo')`) para cada teste, ele vai testar <br>
individualmente, quando você encadeia os `shoulds` ele só irá ser válido se todas as condições forem verdadeiras.

Ou seja, no primeiro quando eu clico no elemento ele demora 3 segundos para aparecer então o teste<br>
`cy.get('#novoCampo').should('not.exist');` passa de primeira.<br>
e o segundo teste fica aguardando (tempo padrão do cypress +/- 4 segundos para lançar uma excessão) <br>
como o tempo para exibir é menor que 4 segundos esse teste também passa
`cy.get('#novoCampo').should('exist');`

Agora no segundo cenário, seria a mesma coisa porem o primeiro should ele entende como verdade, mas o segundo não
pq se o primeiro deu como não existe ele guarda essa ref e passa para o segundo should e o segundo should da uma <br>
Excepton null, pois se o primeiro ele diz que não existe o segundo realmente nao vai existir.

> **Nota:** Aqui explica sobre o pq acontece isso pois ele pega a referencia anterior: https://docs.cypress.io/api/commands/should#Yields

<br/>

---

<br/>

## Find Solo E Find Com Async (Com async não é interessante vou explicar o pq)

<br>

### Diferença entre usar find e usar um seletor

Exemplo, temos a seguinte estrutura:

```
<ul id="lista">
  <li><span>item 1</span></li>
  <li><span>item 2</span></li>
</ul>
```

E podemos selecionar ela de duas formas, porem cada forma tem sua particularidade.

`cy.get('#lista li span', { timeout: 6000 })`<br>
`.should('contain', 'Item 2');` -> aqui eu to falando o seguinte
pega minha lista e todos os spans que tiver dentro de cada `<li>` e aguarde até que apareça o Item 2, nesse exemplo, o `should` vai ficar perguntando ao `get` e fazendo com que o get fique dando get no seletor até achar a assertiva que foi imposta que no caso é `'contain', 'Item 2'`
como no exemplo a lista é asyncrona porem com um tempo `definido` de exibição, se esse tempo definido passar de 4 segundos podemos indicar para o nosso seletor aguardar mais tempo pela prop `timeout` que nesse caso eu passei
6 segundos.

`cy.get('#lista li').find('span')`
`.should('contain', 'Item 2')`-> Já o nosso find, ele não vai esperar pelo segundo elemento aparecer
assim que dermos o find ele vai pegar a primeira referencia que veio em `cy.get('#lista li')` e dar um find em `span`
porem como a lista é `asyncrona` o primeiro `cy.get('#lista li')` que ele pega é apenas essa estrutura:

```
<ul id="lista">
 <li><span>item 1</span></li>
</ul>
```

e fica guardado na memoria que existe apenas essa estrutura com o `.find()` ou seja, não importa quantas retentativas
o crypres der, `nunca vai achar o item 2`.

já utilizando sem o `find` o `should` vai ficar perguntando pro get, iai tem esse valor? iai tem esse valor? até dar
o tempo de timeout.

com o `find`, o get vai achar a estrutura o find vai localizar o elemento e a partir dai, o get vira um "cache" da primeira estrutura que ele achou, e o `should` vai ficar perguntando pro find, iai achou o `item 2`? iai achou?
porem como ficou em cache a estrutura sem o item 2, nunca vai achar.

Por isso utilizar o `find` para estruturas asyncronas não é uma boa.

<br/>

---

<br/>

## Elementos removidos do DOM dinamicamente durante o teste

<br>

Ao remover elementos do dom DURANTE o teste, o cypress vai gerar um erro falando olha o elemento `<li id="item-1">` `(cy.get('#item-1'))`
foi removido do dom.

as vezes o front por algum motivo remove esse item 1 mais adiciona novamente, ai o certo para fazer o teste novamente
seria fazer a seleção pelo elemento pai, exemplo:
`cy.get('#lista #item-1').should('have.text', 'XPTO');

<br/>

---

<br/>

## Timeout / Wait

<br>

### Timeout

---

<br>

O tempo de retentativas até a falha do cypress por padrão é de 4 segundos, porem conseguimos alterar esse valor,
para mais ou para menos, segue um exemplo

`cy.get('#exemplo1')` -> aqui ele vai demorar `4 segundos` para achar o `exemplo1`
`cy.get('#exemplo1', { timeout: 2000 })` -> aqui ele vai demorar `2 segundos` para achar o `exemplo1`
`cy.get('#exemplo1', { timeout: 10000 })` -> aqui ele vai demorar `10 segundos` para achar o `exemplo1`

### Podemos também alterar o timeout padrão do cypress para um determinado tempo

Para fazer isso você deve ir no arquivo `cypress.json` e adicionar a configuração abaixo:

```
{
  "defaultCommandTimeout": 1000 // aqui vc configura em milisegundos quanto tempo voce deseja que se torne o padrão
}
```

### Wait

---

<br>

> **Nota:** Cuidado com o uso do wait ele trava os testes até atingir o tempo definido, já o timeout não, assim que a condição for atendida ele executa ela, caso contrario ficará tentando até o tempo definido.

A **Nota** já diz tudo, tenha cuidado com o uso do wait, pq ao colocar um wait de 5 segundos TODA VEZ que a aplicação rodar e parar nesse wait ela vai esperar por 5 segundos, POREM, se você colocar para o elemento um timeout maior, vai ser mais performatico e vc deve se perguntar o pq?

Bom.. vou mostrar:

`cy.get('.procura-elemento', { timeout:  5000 })` -> nesse caso, eu estou falando para o `cy.get` ficando retentando
buscar esse elemento até no maximo 5segundos, porem se ele achar em `100 milisegundos` o teste vai executar apenas `100 milisegundos` e é ai que está a diferença entre o `timeout` e o `wait`

`cy.wait(5000)`<br>
`cy.get('.procura-elemento')` -> ja nesse conjunto de código estou falando, para tudo e vamos ESPERAR POR 5 SEGUNDOS independente se o elemento aparece antes OU NÃO na tela e só depois de 5 segundos que vamos buscar esse elemento,
ou seja aqui nós criamos um gap de performance, o sistema toda vez vai parar por 5 segundos porem nem sempre demora 5, as vezes demora menos..

<br/>

---

<br/>

## Nem todo comando tem Retry

<br/>

O click não tem retry, no exemplo abaixo o click nao fica clicando até que satisfaça a condição de should,<br>
ele apenas clica uma vez só e fim.

```
it('Click não tem retry', () => {
  cy.get('#buttonCount')
    .click()
    .should('have.value', '11'); // se eu colocar 111 aqui o click não vai ficar clicando até que atenda a condição

});
```

<br/>

---

<br/>

## Then vs Should

<br/>

Primeiramente que ao usar `then` ou `should` como Promises, temos alguns pontos aqui.

`Then`:

1 - Ao utilizar then como Promise, ele vai retornar apenas uma vez quando satisfazer a condição e vai retornar
um objeto em JQuery, ai é só logar esse JQuery e usar como deseja.

2 - O then se não atender ao meu expect eu posso retornar um valor x dentro da arrow function

3 - Com Then eu posso chamar um elemento dar um then e chamar outro dentro do then

`Should`:

1 - Já o should faz a mesma coisa porem a diferença é que ele fica dando retry até que a condição se satisfaça,
ou seja performaticamente não é bom utilizar o should como promise.

2 - Já o should eu posso retornar um valor porem o should por padrão não le esse retorno ele simplemente ignora

3 - Já com o should eu não consigo pegar um elemento dar um should e dentro desse should eu pegar outro elemento<br>
Se eu fizer isso ele fica em loop infinito, pq ele fica retentando pegar o elemento de dentro e de fora.

THEN

```
  cy.get('#lista li span').then($el => {
    console.log($el);
  });
```

SHOULD

```
  cy.get('#lista li span').should($el => {
    console.log($el);
  });
```

<br/>

---

<br/>

## Wrap

<br/>

### #1 Exemplo de uso

Com o uso do wrap podemos transformar elementos que não são rastreados pelo cypress para elementos rastreaveis,
é como se fosse um `of` do `rxjs`, segue um exemplo:

`var objetoNormal = { nome: 'Nicolas' };`

`cy.wrap(objetoNormal).should('have.property', 'nome', 'Nicolas')`

No código acima eu estou permitindo que um objeto normal do js ganhe funcionalidades de validações do cypress,
o mesmo eu posso fazer para elementos do dom, segue um exemplo:

### #2 Exemplo de uso

```
cy.get('#formNome').then($el => {
  $el.type('Testando o type com wrap'); // ASSIM NÃO FUNCIONA
  cy.wrap($el).type('Testando o type com wrap'); // ASSIM FUNCIONA
});
```

No código acima eu estou pegando um input e dando um `then` para obter o elemento e trabalhar em cima dele,
nesse caso apenas como exemplo de como posso utilizar o `wrap`, eu estou dando um `wrap` nesse `elemento`
para que ele ganhe as `funcionalidades do cypress` e eu possa digitar nele.

### #3 Exemplo de uso de promises com async do js vs async do cypress

Suponhamos que estamos mexendo com `Promises` e 2 são do proprio cypress e uma é customizada do js, vamos ter um erro de ordem de execução pois o cypress gerencia suas promisses top down ( primeira segunda e etc..) já no js, a primeira
promisse que executar ele loga na tela, com `cy.wrap` podemos resolver o problema de uma promise customizada, segue
um exemplo:

```
const promiseCustom = new Promise((resolve, reject) => {
  setTimeout(() => resolve(10), 500);
});

cy.get('#buttonSimple').then(() => console.log('Executei primeiro'));
promiseCustom.then((result) => console.log(result));
cy.get('#buttonList').then(() => console.log('Executei terceiro'));
```

![](./images/promise-customizada2.png).

Voce percebe na imagem que o valor 10 da promisse foi logado por ultimo e não em segundo, para resolvendo isso
podemos utilizar o `wrap` para entrar no ciclo do cypress, segue a correção:

Altere a linha do `promiseCustom.then` para:<br>
`cy.wrap(promiseCustom).then((result) => console.log(result));` e pronto, agora vai executar na ordem certa.

<br/>

---

<br/>

## Its

<br/>

Basicamente ele acessa uma propriedade que você informar, segue o exemplo:

## Exemplo 1

```
var objetoNormal = { nome: 'Nicolas' };

cy.wrap(objetoNormal).its('nome').should('be.equal', 'Nicolas');
```

No exemplo acima eu acesso a prop `nome` com `its` e verifico o valor dela se é igual a `Nicolas`.

## Exemplo 2

também podemos acessar mais de uma prop como no exemplo abaixo:

```
// Mais de um its
const objetoDentroDeObjeto = {
  nome: 'Nicolas',
  endereco: { rua: 'do fulano' },
};

cy.wrap(objetoDentroDeObjeto)
  .its('endereco')
  .its('rua')
  .should('eq', 'do fulano');
```


## Exemplo 3
Também podemos acessar diretamente, minimizando o comando:

```
cy.wrap(objetoDentroDeObjeto)
  .its('endereco.rua')
  .should('eq', 'do fulano');
```

<br/>

---

<br/>

## Invoke

<br/>

Podemos utilizar o evoke de algumas maneiras, ele é utilizado para executar funções e testa-las, seja ela pura do javascript ou do JQuery ou do cypress, não importa, sendo função podemos testar o seu resultado.

```
const getValue = () => 1;
const soma = (a,b) => a+b;

// função simples
cy.wrap({ getValue }).invoke('getValue').should('be.equal', 1);

// função com argumentos
cy.wrap({ soma }).invoke('soma', 1,2).should('be.equal', 3);

// utilizando a pagina com invoke e escrevendo um valor em um input
cy.visit('https://wcaquino.me/cypress/componentes.html');
cy.get('#formNome').invoke('val', 'Inputando texto com invoke');

// Esse alert funciona o teste, porem o cypress mata imediatamente ele para não atrapalhar o fluxo de teste
cy.window().invoke('alert', 'invokando alerta pelo invoke');

// podemos pegar um elemento da tela e acessar qualquer propriedade JQuery e manipular esse elemento com o invoke
cy.get('#resultado').invoke('html', '<input type="button" value="injetando html com invoke">');
```