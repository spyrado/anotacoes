# REDE BRIDGE

Link de referência: https://docs.docker.com/engine/network/drivers/bridge/#differences-between-user-defined-bridges-and-the-default-bridge

> O Docker já configura uma rede por padrão chamada bridge

## Como identificar uma bridge dentro de um container?

Exemplo utilizando ubuntu:
  - docker run -it ubuntu
  - docker ps // para visualizar o id do container
  - docker inspect ID_DO_CONTAINER
    - o json retornado vai ter uma propriedade chamada "Networks" é nela que contem o "bridge" que contem o ip e todas as configs de rede.

## Como verificar quais networks o docker possui?

  -  `docker network ls`: lista as networks que o docker possui
  

## Como identificar se os 2 dockers que vc rodou estão na mesma rede E estão se comunicando?
  - primeiro rode o comando em um dos containers: 
    - apt-get update e depois 
    - apt-get install iputils-ping
    - após instalar os 2 de um ping no ip que voce deseja comunicar ex: container 1 vai dar um ping no container 2 e o ip do container 2 é "IPAddress": "172.17.0.3",
      - comando: ping 172.17.0.3
        - se ele ficar logando varias vezes, significa que está comunicando, se logar uma vez só n tem conexao.

## Comunicacao VIA IPs

  - Não é interessante agt se comunicar via IP com docker, pois ele pode ser reiniciado e pode gerar outro ip quando startado novamente
  - A boa prática é criar um DNS ou um hostname para ficar se comunincando com a mesma rede.

## Como criar um HostName para não depender de comunicação via IP?

  - para criar um hostname é bem facil no docker, siga o passo a passo:
    - primeiro vamos criar nossa rede customizada
      - docker network create --driver bridge minha-rede-customizada
    - após criar a rede, vamos subir dois containers ubuntu só para demonstração:
      - docker run -it --name ubuntu1 --network minha-rede-customizada ubuntu 
      - docker run -it --name ubuntu2 --network minha-rede-customizada ubuntu
        - o que esses 2 comandos fazem? criam cada um 1 container cada um com nome diferente ( ubuntu1 e ubuntu2 ) porém eles associam a MESMA rede, ou seja, via hostname agora eu vou conseguir dar um ping do ubuntu1 para o 2 e vice versa.
        - agora eu posso ir no ubuntu1 por exemplo e dar os comandos:
          - apt-get update
          - apt-get install iputils-ping
          - e por fim
          - ping ubuntu2
            - ele vai pingar normalmente e não dependemos mais de pingar no IP, só pingamos via hostname

