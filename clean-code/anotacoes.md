# CLEAN CODE

## O que significa?

Clean code representa **boas praticas** em seu código, como você escreve o código, ele "prega" que um código limpo deve ser bem legível, manutenível dentre outras coisas.

## Técnicas de refatoração
---
<br>

### [Técnicas de refatoração] MÉTODO DE EXTRAÇÃO
---
<br>

  - **[ERRADO] Exemplo de um método que tem mais de um objetivo:** 
  ```
  function calcularMedia(numeros) {
    let soma = 0;
    let contador = 0;

    for (let i = 0; i < numeros.length; i++) {
      soma += numeros[i];
      contador++;
    }

    const media = soma / contador;

    if (media >= 7) {
      console.log("Aprovado");
    } else {
      console.log("Reprovado");
    }
  }

  // Exemplo de uso da função
  const notas = [8, 7, 6, 9, 5];
  calcularMedia(notas);

  ```
  - **[CORRETO] Exemplo utilizando "Método de extração"**
  ```
  function calcularMedia(numeros) {
    const soma = calcularSoma(numeros);
    const contador = numeros.length;
    const media = calcularMediaAritmetica(soma, contador);
    exibirResultado(media);
  }

  function calcularSoma(numeros) {
    let soma = 0;

    for (let i = 0; i < numeros.length; i++) {
      soma += numeros[i];
    }

    return soma;
  }

  function calcularMediaAritmetica(soma, contador) {
    return soma / contador;
  }

  function exibirResultado(media) {
    if (media >= 7) {
      console.log("Aprovado");
    } else {
      console.log("Reprovado");
    }
  }

  // Exemplo de uso da função
  const notas = [8, 7, 6, 9, 5];
  calcularMedia(notas);

  ```

## Boas práticas:

- **"Mais tarde é igual a nunca"** evite ao máximo deixar códigos ruins para uma "v2" pois o futuro vai ter novas prioridades e nunca vai conseguir
voltar para arrumar o código, ou alinhe com a squad o tempo para se necessário termos 1 task de refatoração 1 vez por sprint ( não é o cenário 
ideal, mas se o contexto for esse é melhor que nada.)
- **Abstrações claras**, sempre quando for fazer algum código abstrato/genérico, deixe ele o mais entendível possível, e não faça códigos genéricos a rodo, para qualquer tipo de situação.
  - Exemplo código genérico ruim
    - ```v(control: string, form: FormGroup) { return form[control].valid }```
  - Exemplo código genérico melhor
    - ```validaFormControl<T>(controlName: T, form: FormGroup) { return form[controlName].valid }```
  - no primeiro exemplo o dev "imaginou" que "v" significa valida, e seguiu o desenvolvimento, no segundo exemplo o dev já foi mais cuidadoso, deixando explicito para o leitor que o método é um "validaFormControl" e que o dev pode passar os nomes dos controls em cada tela que ele usar esse método, pois cada tela tem um nome diferente de control, dentre outros itens.
  
-  **Deve conter apenas o necessário**: geralmente os devs costumam fazer grandes funções que fazem tudo, porem para a leitura de quem vai entender o código fica extremamente ruim, então
   - Exemplo função ruim que faz mais que o necessário.
     - exemplo:
     ``` 
      login() {
        const hasToken = this.servico.
        if(this.form.valid) {
          this.router.navigate(['home'])
        } else {
          console.log('Seu login está inválido');
        }
      }
     ```
- **Sem duplicidade de código**: Código duplicado significa que uma ideia na sua cabeça, não está bem representada no código, nesses caso deve analisar o código duplicado e verificar o que é possível fazer para unificar esse código, unificando o código isso também ajuda nos testes unitários, pois você só irá precisar validar uma vez esse ponto.

- **Minimizar o número de entidades, como classes, métodos, funções e outras coisas do tipo**: a dica aqui é verificar se temos uma solução já feita no projeto, que atenda a sua intenção naquele momento, isso eu englobo tudo, classes metodos funções interfaces e etc.<br>
As vezes temos uma interface que já atende ao cenário proposto, mas como não consultamos o projeto criamos mais uma interface com a mesma intenção gerando duplicidade, as vezes temos funções com nomes diferentes, porem com o mesmo objetivo que seria por exemplo ```clearValue() - limparValor()``` e por ai vai.

- **Observar se a classe e/ou o método possui apenas um objetivo**: métodos que possuem mais de uma tarefa precisam ser divididos.
  - **[ERRADO] Exemplo de um método que tem mais de um objetivo:** 
  ```
  function calcularMedia(numeros) {
    let soma = 0;
    let contador = 0;

    for (let i = 0; i < numeros.length; i++) {
      soma += numeros[i];
      contador++;
    }

    const media = soma / contador;

    if (media >= 7) {
      console.log("Aprovado");
    } else {
      console.log("Reprovado");
    }
  }

  // Exemplo de uso da função
  const notas = [8, 7, 6, 9, 5];
  calcularMedia(notas);

  ```
  - **[CORRETO] Exemplo utilizando "Método de extração"**
  ```
  function calcularMedia(numeros) {
    const soma = calcularSoma(numeros);
    const contador = numeros.length;
    const media = calcularMediaAritmetica(soma, contador);
    exibirResultado(media);
  }

  function calcularSoma(numeros) {
    let soma = 0;

    for (let i = 0; i < numeros.length; i++) {
      soma += numeros[i];
    }

    return soma;
  }

  function calcularMediaAritmetica(soma, contador) {
    return soma / contador;
  }

  function exibirResultado(media) {
    if (media >= 7) {
      console.log("Aprovado");
    } else {
      console.log("Reprovado");
    }
  }

  // Exemplo de uso da função
  const notas = [8, 7, 6, 9, 5];
  calcularMedia(notas);

  ```