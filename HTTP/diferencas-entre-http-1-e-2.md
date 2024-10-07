## HTTP 1 VS HTTP2 


- **HTTP 1**
  - requisições sincronas, ela aguarda a sua requisição finalizar para que vc possa fazer outra requisição
  - geralmente nos geramos varias requisições ao inves de uma, para poder carregar o conteudo
- **HTTP 2**
  - requisições multiplexas, ela faz varias requisições de uma só vez, otimizando o tempo de carregando da sua pagina
  - economiza recursos
  - vc pode utilizar o recurso server push, 
    - que vai enviar antecipadamente os dados necessários para o cliente ( dados comuns de serem carregados ) 
    - ele nao trafega nossa informação como texto, sendo mais performatico