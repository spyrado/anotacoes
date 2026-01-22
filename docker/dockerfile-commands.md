# Comandos do Dockerfile

- `FROM node:14` -> estou baixando uma imagem de node na versão 14
- `WORKDIR /app` -> estou falando que meu diretório de trabalho é a pasta app
- `COPY . .` -> estou copiando tudo que está na raiz desse projeto e jogando para dentro do meu workdir ( app ou qualquer outro nome que você definir no WORKDIR )
- `RUN npm install` -> estou instalando as dependencias do sistema
- `ENTRYPOINT npm start` -> estou falando que sempre que o container for iniciado deve rodar esse comando