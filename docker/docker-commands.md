Link REF: https://www.youtube.com/watch?v=F2au3FXq9Y4

lista de comandos docker

- `docker --helper` -> para verificar se o seu docker está instalado na maquina
- `docker run hello-world` -> para verificar se o seu docker desktop está de pé
- `docker build -t angular-docker .`
  - `docker build`: Comando usado para construir uma imagem Docker.
  - `-t angular-docker`: A opção `-t` permite atribuir uma tag (ou nome) à imagem que está sendo construída. Neste caso, a imagem será nomeada como angular-docker
  - `.` o ponto no final é para falar para o docker que o arquivo Dockerfile está na raiz aonde o comando está sendo executado
- `docker run -p 4500:4500 angular-docker`
  - `docker run`: Comando para iniciar um novo contêiner a partir de uma imagem Docker.
  - `-p 4500:4500`: Opção para mapear portas entre o host e o contêiner.
    - `4500:4500`: O formato é porta_host:porta_contêiner. Isso significa que a porta 4500 do host será redirecionada para a porta 4500 dentro do contêiner.
  - `angular-docker`: Nome ou tag da imagem Docker que será usada para criar o contêiner. Essa imagem deve ter sido previamente construída ou baixada.
- `docker ps`: lista todos os containers ativos
- `docker pull [NOME_DA_SUA_IMAGEM]`: ele baixa a imagem apenas.
- `docker run [NOME_DA_SUA_IMAGEM]`: ele baixa a imagem e sobe um docker
- `docker exec -it [ID_DO_SEU_CONTAINER] bash`: ele entra nesse docker em modo interativo ( você fica dentro desse container podendo executar comandos dentro dele )
-  `docker stop ID_DO_SEU_CONTAINER`: faz com que o container pare de rodar, ele RESETA toda a arvore de processos que estavam em execução.
-  `docker pause ID_DO_SEU_CONTAINER`: faz com que o container pare de rodar, porem ele NÃO RESETA a arvore de processos, os processos continuam rodando.
-  `docker unpause ID_DO_SEU_CONTAINER`: faz o seu container voltar a rodar.
-  `docker run [IMAGEM]`: ela roda sua image, porem se vc ficar rodando ele vai criar 1 instancia para cada docker run.
-  `docker start [ID_DO_SEU_CONTAINER]`: se voce deu um stop, voce pode dar um start pelo id do container que o container volta a subir e reexecutar tudo que estava programado.
-  `top`: não é comando docker, é linux, mas é util pois ele verifica todos os processos que estão sendo executados