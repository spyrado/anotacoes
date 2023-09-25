# Padrão de projeto 

# VO ( Value Object )

- Ele prove mais segurança a nossa aplicação.
- A `VO` Define um contrato entre `front` e `back`
- Permite que possamos versionar nossa api `domain/v1/cliente` `domain/v2/cliente`, enquanto uma `VO` antiga tem 3 props, se precisarmos adicionar mais uma prop, podemos criar uma `VOV2` recebendo essa nova prop, e endpoints com path `v2` que batem nessa nova `VOV2`
- Ele cria uma camada entre `controller` e `Entidade`, ou seja a controler bate primeiro no `VO` pra depois o VO bater na entidade.
- Torna os endpoints mais flexiveis a mudanças, se mudarmos direto na entidade alguma alteração do banco,
  podemos quebrar a aplicação, por outro lado se criarmos um novo `VO` e só passarmos ele quando bater na
  nova versão da api, tudo fica certo.<br>
    EXEMPLO:<br>
    - `PessoaVO` -> dentro do pacote `v1`
    - `PessoaVO` -> dentro do pacote `v2`
    - quando o endpoint for chamado 
        - https://dominio/v1 -> ele vai pegar a lógica que tem da `PessoaVO` dentro do pacote `v1`, para mantem a mesma estrutura anterior
        - https://dominio/v2 -> porem novas chamadas que baterem aqui na `v2`, vão pegar da `PessoaVO` do pacote v2 com as novas alterações