# Objeto de Referencia e Cópia

Link de Referência: [Object Reference](https://javascript.info/object-copy)

## Variáveis primitivas
-----
<br>
Variáveis com valores primitivos sempre tem o seu valor copiado de forma a não ter referencia.
exemplo:

<br>

![](./images/primitive-no-reference.png)

Na imagem acima vemos que temos duas variáveis ( ```NOME``` e ```NOME2``` ), sendo que ```NOME``` é passado como referencia para ```NOME2```, porem quando alteramos ```NOME2``` para qualquer outra string, a variavel ```NOME``` continua intácta, isso já não acontece 
com Objetos, acontece apenas com variaveis do tipo primitiva ( string, number, boolean e etc.. )

<br>

## Variáveis do tipo Objeto
-----

Já com variáveis do tipo objeto ao você atribuir ela a outra variável, ela pega o endereço de memória ( referência ) dessa variável e não o seu conteúdo,
ou seja toda vez que você alterar uma variável que pegou uma referencia de outro objeto, esse objeto pai sempre será modificado também, ***você deve ficar atento a isso***.

Segue um exemplo de como isso afeta o código:

<br>

![](./images/object-reference.png)

Aqui conseguimos observar que a variavel ```obj``` foi declarada com a propriedade ```nome = 'Nicolas'```, porem ao passar a variavel ```obj``` para a outra variavel ```obj2``` e na variável ```obj2``` alterarmos a propriedade ```nome``` para ```xpto```, o ```obj``` também é afetado com essa alteração, ficando tanto ```obj``` quanto ```obj2``` com a propriedade ```nome``` igual a ```xpto```.

## Como resolver esse problema?

Quando nos deparamos com esse tipo de situação devemos utilizar alguns recursos nativos do JavaScript para resolver isso, segue a solução;

<br>

![](./images/solucao-object-reference.png)

Na imagem acima utilizamos a estratégia de transformar o Objeto em um JSON isso faz com que o javascript desvincule a referencia, e transformamos o JSON em objeto para o javascript trabalhar normalmente como objeto.

```JSON.parse(JSON.stringify(obj));```
