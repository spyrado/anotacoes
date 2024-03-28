# Quais são as vantagens de se utilizar NGRX?

## Arquitetura

![](./imagens/arquitetura-gerenciamento-de-estado.png)

- `STORE` se transforma em nossa fonte única de verdade, o que isso quer dizer?
  - quer dizer que não vamos mais precisar ficar passando informação de um componente para outro via @Input e @Output criando um monte de dependencia e dificultando a manutenção.
  - podemos consultar tudo de uma única fonte, o `STORE`.
- `SELECTOR` você seleciona coisas que você armazenou no seu `reduzcer`/(store), vc preconfigura o reducer com uma variavel lá no root, e ai você da um select nessa variavel que você configurou no seu reducer.
- `ACTION` é uma ação que eu envio para o estado da minha aplicação
- `REDUCER` O reducer captura a ação disparada para fazer uma mutação(alteração) no store.
