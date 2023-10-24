# O que significa "Content Negociation"

É a capacidade do nosso servidor `REST` disponibilizar diferentes versões de um mesmo objeto.
ou seja, posso devolver `JSON` `XML` `YML` `CSV` `PDF` `PNG` enfim..

Além disso, pode estar relacionado a um tipo de linguagem(idioma)
Exemplo:

A nossa API suporta `internacionalização` e eu posso devolver a resposta em português ou espanhol ou ingles

## Resumo

é a capacidade da nossa api de fornecer diferentes tipos de dados `JSON` `XML` `YML` `CSV` `PDF` `PNG` e/ou idiomas.

claro que a API(`SERVER-DRIVEN`) tem que estar preparada para que o cliente(`Agent-driven`) solicite oq ele deseja.