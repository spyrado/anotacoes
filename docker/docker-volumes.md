# VOLUMES

> Podemos compartilhar volumes `ENTRE CONTAINERS`

## BIND MOUNTS

  ### adicionando volumes com a flag -v

  - `docker run -it -v /caminho/xpto/volume-docker-pasta-teste:/app ubuntu bash`: aqui eu estou rodando um comando que faz com que dentro do ubuntu tenha uma pasta chamada app e tudo que tenha localmente na minha maquina 
    dentro da pasta /volume-docker-pasta-teste automaticamente vai para dentro do ubunto na pasta /app.
  - `docker run -it` estou pedindo para o docker rodar ALGO ( que eu n falei ainda ) em modo iterativo.
  - `-v /caminho/xpto/volume-docker-pasta-teste:/app` estou indicando que vai ter um volume e esse volume está localizado na minha maquina local no caminho x na pasta /volume-docker-pasta-teste, e que é para passar tudo que tem nessa pasta para a pasta /app
    que fica dentro do ubuntu
  - `ubuntu bash`: no final eu digo para rodar ubuntu em bash
  - `OBSERVAÇÃO`: é uma via de mao dupla, ao startar ele pega oq tem na pasta /volume-docker-pasta-teste porem se durante o "running" do container ele criar algo dentro da pasta /app, ele via passar esse mesmo algo para a pasta /volume-docker-pasta-teste para que
      sempre ambos fiquem atualizados.
  - `VANTAGEM DESSA ABORDAGEM:` toda vez que eu stopo ou deleto o pod e rodar ele com o comando indicando o volume, ele sempre vai iniciar novamente já com o volume que tinha antes, assim não perdemos dados.

  ### adicionando volumes com a flag --amount ( mais recomendada )
    - `docker run -it --mount type=bind,src=/caminho/xpto/volume-docker-pasta-teste,target=/app ubuntu bash`: aqui é a mesma coisa que o exemplo do -v, porem o docker recomenda utilizar o --mount por ficar mais explicito e ter mais compatibilidade

## VOLUME 

> CRIANDO volume e fazendo o docker em vez de pegar local via bind pegar do volume criado

   -  `docker volume ls`: lista os volumes já criados.
   -  `docker volume create meu-volume`: cria um volume chamado "meu-volume"
   -  `docker run -it --mount src=meu-volume,target=/app ubuntu bash` ou `docker run -it -v meu-volume:/app ubuntu bash` ambos vao apontar para a pasta que foi criada no docker chamada de "meu-volume" e sempre que for recuperar será de lá.
   `DUVIDA`, e aonde fica esse volume?
    dentro desse caminho: `/var/lib/docker/volumes`, para acessar precisa acessar com sudo su ( super usuário )
    o conteudo sempre vai ficar aqui `/var/lib/docker/volumes/meu-volume/_data`
   `DICA IMPORTANTE` se voce rodar esse comando: `docker run -it --mount src=meu-volume,target=/app ubuntu bash` porem não existir o volume "meu-volume" criado ainda, ele vai `CRIAR` para voce automaticamente.

## TMPFS

> DIFERENTE dos volumes e os bind mounts você NÃO CONSEGUE compartilha-los entre containers

> Essa funcionalidade está `APENAS DISPONÍVEL` se você estiver rodando dentro de um `linux`

> tmpfs não é armazenado na camada de RW (Read Write), pois ele é armazenado na MEMORIA RAM do HOST

  ### Quais são as vantagens?
    🔹 1. Performance (muito mais rápido)

    RAM é **MUITO** mais rápida que disco.

    👉 Ideal pra:
    - arquivos temporários  
    - cache  
    - processamento intermediário  

    ---

    🔹 2. Segurança 🔐

    Nada é persistido.

    👉 Perfeito pra:
    - senhas temporárias  
    - tokens  
    - dados sensíveis  

    Se o container parar → **sumiu tudo**

    ---

    🔹 3. Evitar escrita em disco

    Às vezes você não quer sujar o disco.

    👉 Exemplo:
    - logs temporários  
    - arquivos que não precisam ser salvos  
