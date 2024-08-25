# Merge Map

`VIDEO REFERÊNCIA: ` https://www.youtube.com/watch?v=RSf7DlJXoGQs

O `mergeMap` funciona como uma corrida de 800 metros:

![alt text](image-3.png)

Todos vão sair ao mesmo tempo, uns podem sair em primeiro, outros em segundo, mas não significa que sempre oq sair primeiro vai finalizar a corrida em primeiro.

### Como no exemplo abaixo:
![alt text](image-2.png)
![alt text](image-4.png)

O usuário selecionou a `SEGUNDA OPÇÃO` foi feito o request logo em seguida da `SEGUNDA OPÇÃO`,
porem ela foi a última a dar a resposta, pois a carga do request 2 é maior que os demais.

Logo em seguida o usuário selecionou a `TERCEIRA OPÇÃO` e a terceira opção veio a resposta mais rapido.

## Quando NÃO Utilizar mergeMap? &cross;

  - não devemos utilizar `mergeMap` nesse caso, pois se o usuário selecionar a `opção 1` depois a `opção 2` e depois a `opção 3` como o merge map ele simplesmente dispara a primeira requisição que chega e não aguarda ela finalizar, vamos ter um problema ai, pois se a ultima opção que o usuário selecionar for a 3, mas a opção 1 for a mais demorada, o ultimo retorno vai ser da opção 1 sobrescrevendo o resultado selecionado pelo usuário que foi 3.

## Quando utilizar mergeMap? &check;

  - Quando as emissões/eventos puderem ser processadas de simultanea ( muitas vezes mais performático )
  - quando a ordem não importar.