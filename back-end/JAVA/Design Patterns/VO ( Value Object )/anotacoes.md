# Padrão de projeto 

# VO ( Value Object )

- Ele prove mais segurança a nossa aplicação.
- Torna os endpoints mais flexiveis a mudanças, se mudarmos direto na entidade alguma alteração do banco,
  podemos quebrar a aplicação, por outro lado se criarmos um novo `VO` e só passarmos ele quando bater na
  nova versão da api, tudo fica certo. 