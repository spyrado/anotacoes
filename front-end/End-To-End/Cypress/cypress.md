# Cypress

<details>
  <summary>Inicio</summary>
  npm install cypress -> instala o cypess
  cypress open -> roda o cypress

  `/// <reference types="Cypress" />` -> adicione essa linha no começo de um arquivo `nome_arquivo.spec.js` para o vs code<br> entender que estamos trabalhando com cypress
</details>


<details>
  <summary>Asserts</summary>
  Podemos fazer de algumas formas umas menos intuitivas como:<br>
  
  Todas abaixo tem o mesmo resultado, o que muda é a leitura, e na minha opiniao `to be equal` seria o ideal nesse caso
  
  ```
    expect(1).equal(1); -> vai dar o mesmo resultado
    expect(1).to.equal(1); -> vai dar o mesmo resultado
    expect(1).to.be.equal(1); -> vai dar o mesmo resultado
  ```
</details>

<details>
  <summary>Asserts para objetos</summary>

  ```

    it('Equality for Objects', () => {
  
    const obj = {
      a: 1,
      b: 2
    };
    // essa é uma forma errada, pq o js entende que é outro objeto outra referencia, para isso devemos utilizar deep
    // expect(obj).to.be.equal({ a: 1, b: 2 }); -> ERRADA
      expect(obj).to.be.deep.equal({ a: 1, b: 2 }); -> CERTA
    });

  ```
</details>