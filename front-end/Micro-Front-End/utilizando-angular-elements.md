# Micro Front End Utilizando [Angular Elements]

Link ref: [implementando micro front utilizando angular elements](https://dzone.com/articles/scaling-micro-frontends-using-angular-elements)

## Como implementar?
---
<br>

...

<br>

## Desvantagens de usar em específico Angular Elements
---
<br>

- Todo projeto feito com angular elements, gera um build todo de .js e .css, ou seja<br>
  se tivermos uma aplicação com uma lib bootstrap v4 e outra aplicação com bootstrap v5 ambas em micro front e caso o bootstrap mude a classe .container { } na versao v4 de .container {padding: 14px} para .container { padding: 20px; background: red; } na versao v5, nosso sistema será impactado com isso, então todos os micros devem estar alinhados para utilizarem as mesmas versões de libs de estilo.

- Outro ponto, cada micro gera um build, e suponhamos que ambos os micros tenham o bootstrap v5 como framework css, então todo build desses micros vao gerar as MESMAS CLASSES toda hora, ou seja é como se estivessemos colocando 2 arquivos bootstrap.min.css
no servidor.