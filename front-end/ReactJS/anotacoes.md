# ReactJS ESTUDO

## Como instalar?

---

<br/>
Rode os comandos:

- npx create-react-app my-app `-> irá criar um app react com o nome 'my-app'`
- cd my-app `-> entra na pasta do projeto`
- npm start `-> inicia o app`

<br>

---

<br>

## Como criar componentes no React?

---

<br/>

```
function MyButton() {
  return (
    <button>I'm a button</button>
  );
}
```

<br/>

## Como incluir componentes na tela?

---

<br/>

> Todo componente React é identificado com o padrão de TAG PascalCase [1], nesse exemplo o componente MyButton entra no html como `<MyButton/>`

<br>

```
function MyButton() {
  return (
    <button>I'm a button</button>
  );
}

export default function MyApp() {
  return (
    <div>
      <h1>Welcome to my app</h1>
      <MyButton /> // [1]
    </div>
  );
}

```

<br>

## O que é JSX?

---

<br/>

JSX é uma extensão da linguagem JavaScript, que nos permite inserir `Elementos HTML` dentro de código `Javascript`, nos dando um poder de desenvolvimento muito maior e mais flexivel.

JSX não é uma linguagem lida pelo browser, para isso precisamos de algum `transpiler` ( geralmente Babel ) para converter essa linguagem para uma linguagem lida pelo browser `( assim como TypeScript )`.

JSX por sua vez é mais `rigido` quanto a fechamento de tags, como por exemplo `<br/>` se você não fechar,
ele vai gerar um erro.

Seu componente `NÃO PODE` Executar multiplos JSX, temos que dar um wrap nele, para que funcione, segue exemplo:

> Você pode utilizar `<></>` ou `<div><div/>` para fazer um wrap do seu componente

<span style="color:red; font-weight: bold;">BAD</span>:

```
function AboutPage() {
  return (
    <h1>About</h1>
    <p>Hello there.<br />How do you do?</p>
  );
}
```

<span style="color:#0f9d58; font-weight: bold;">GOOD</span>:

```
function AboutPage() {
  return (
    <>
      <h1>About</h1>
      <p>Hello there.<br />How do you do?</p>
    </>
  );
}
```

<br>

## Adicionando Styles

---

<br/>

Para adicionar estilos css, basta criarmos uma classe em um arquivo separado e na tag que queremos estilizar chamar essa classe juntamente com o atributo className, você só precisa garantir que o código css, vai estar como link no seu arquivo principal, o resto o react cuida para você.

xpto.css

```
.avatar {
  color: red;
}
```

xpto.js

```
<img className="avatar" />
```

<br>

## Adicionando Styles Com Variáveis JavaScript

---

<br>

Para adicionar estilos via variavel JS, você deve usar duplo `{{}}` para que o html entenda que dentro de style irá entrar variáveis JS.

```
const user = {
  name: 'Hedy Lamarr',
  imageUrl: 'https://i.imgur.com/yXOvdOSs.jpg',
  imageSize: 90,
};

export default function Profile() {
  return (
    <>
      <h1>{user.name}</h1>
      <img
        style={{
          width: user.imageSize,
          height: user.imageSize
        }}
      />
    </>
  );
}
```

<br>

## Exibir variaveis no html (Displaying data)

---

<br/>

Para que você consiga exibir variáveis no html, vc deve envolver essa variável com `{}`, segue exemplo
abaixo:

```
return (
  <h1>
    {user.name}
  </h1>
);
```

<br>

## Renderização Condicional

---

<br/>

No exemplo abaixo se o usuário está logado eu exibo o painel de admin, caso contrário eu chamo o formulário
de login

```
let content;
if (isLoggedIn) {
  content = <AdminPanel />;
} else {
  content = <LoginForm />;
}
return (
  <div>
    {content}
  </div>
);
```

Simplificando o código acima ( `short hand` ):

```
<div>
  {
    isLoggedIn ?
    ( <AdminPanel /> ) :
    ( <LoginForm /> )
  }
</div>
```

Quando você não precisar da condição `else`, podemos simplificar ainda mais:

```
<div>
  { isLoggedIn && <AdminPanel /> }
</div>
```

<br>

## Utilizando o for loop para exibir listas

---

<br/>

Para exibir listas você deve utilizar o operador `map` para transformar o array em uma lista html, que seja aceita pelo JSX, e depois retornar essa variável, segue o exemplo:

```
const products = [
  { title: 'Cabbage', id: 1 },
  { title: 'Garlic', id: 2 },
  { title: 'Apple', id: 3 },
];
```

```
const listItems = products.map(product =>
  <li key={product.id}>
    {product.title}
  </li>
);

return (
  <ul>{listItems}</ul>
);
```

> O atributo `key` identifica os elementos dentro da lista ( `deve se passar um identificador unico para ele` assim como no exemplo `product.id` ), e fala para o react quando acontece alguma mudança na lista ( inserção, deleção, atualização e etc ).

<br>

## Como chamar evento no html?

---

<br/>

Declaramos a função dentro do nosso component ou fora e chamamos essa função como no exemplo abaixo `<button onClick={handleClick}></button>`:

```
function MyButton() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}
```

<br>

## Informando o React para atualizar a tela ( Updating the screen ) [UTILIZANDO HOOKS]

---

<br/>

Utilizamos o `useState` para atualizarmos a informação no html, a declaração fica assim:

- `const [count, setCount] = useState(0);`
- sendo `count` o nome da variavel que eu quero atualizar.
- `setCount` a funcionalidade que vai atualizar a variavel `count` e informar para o react atualizar o html
- useState(`VALOR_INICIAL_DA_VARIAVEL_COUNT`)

> Por convenção seguimos esse padrão de nomenclatura, `[something, setSomething]`.

```
function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Clicked {count} times
    </button>
  );
}
```

<br>

# Hooks

<br/>

Funções iniciadas com `use` nós chamamos de `Hooks` um dos hooks que acabamos de utilizar foi o `useState`
para saber mais sobre outros hooks acesse: https://beta.reactjs.org/reference/react

<br/>

---

## **useState**

<br>

> **_NOTE:_**  O React quando se trata de Comunicar o RENDER para atualizar a visualização para o usuário
> nós temos que utilizar o useState, se eu simplesmente declarar um let index = 0 colocar ele no html
> e atravez de um click dar um index = index + 1, ele nuncá vai atualizar o render( a tela )

<br>

## Compartilhando dados entre componentes ( Sharing data between components )

---

<br/>

No exemplo anterior que utilizamos `setState` se duplicarmos o código no html, cada botão vai emitir o seu prório controle de valor, então se eu clicar para incrementar um numero no primeiro botão apenas o primeiro
botão será alterado para o valor 1, o segundo continuará com o valor 0.

```
return (
  <>
    <MyButton/>
    <MyButton/>
  </>
)
```

Porem existem casos que nós queremos compartilhar informações entre componentes, nesse caso como devemos fazer?<br>
Nós devemos subir o useState para o componente PAI, que vai passar para os filhos o valor atualizado,
segue exemplo:

```
function ButtonCount({ count, onClick }) {
  return (
    <>
      <button onClick={onClick}>click me</button>
      <span>{count}</span>
    </>
  );
}

function App() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div className="App">
      <ButtonCount count={count} onClick={handleClick} />
      <ButtonCount count={count} onClick={handleClick} />
    </div>
  );
}
```

`<ButtonCount count={count} onClick={handleClick} />` -> `count` e `onClick` declarado na TAG de um componente são chamados de props, todos os `"atributos(props)"` que você inserir ali, podem ou não ser
utilizados pelo componente.

Aqui nós pegamos as mesmas props passadas para a tag, e repassamos para a função de click do botão para,
executar a função pai e atualizar o count.

```
function ButtonCount({ count, onClick }) {
  return (
    <>
      <button onClick={onClick}>click me</button>
      <span>{count}</span>
    </>
  );
}
```

<br>

> Nota: nesses casos o `onClick` na `tag do COMPONENTE`, serve apenas como `prop` e não como `evento`
> por isso precisamos passar como prop para o component filho receber o valor dessa prop, e passar
> para o real `evento`

<br>

---

Até aqui essa doc foi baseada nesse link de ref: https://beta.reactjs.org/learn#writing-markup-with-jsx

---
