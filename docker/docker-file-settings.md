Link REF: https://www.youtube.com/watch?v=F2au3FXq9Y4
# Configurações

- `FROM` node:21 -> significa que quero instalar a dependência do Node na versão 21 
  - `FROM` node:18.19.1 `as` builder
    - o `as` eu estou dando um apelido para o meu node
- `FROM nginx:alpine` -> `:alpine` é uma tag que especifica a versão da imagem Docker que você deseja usar. Neste caso, a imagem é baseada no Alpine Linux, uma distribuição Linux extremamente leve e minimalista.
- `WORKDIR` /app -> diz em qual diretório eu quero trabalhar, que nesse caso é `/app`  
- `COPY` . . -> diz que quero copiar tudo que está na raiz local, e colar na raiz do meu `WORKDIR` que no caso é `app`
- `RUN` npm install -> o `RUN` serve para rodar algum comando, nesse caso o comando foi `npm install`
- `EXPOSE` 4200 -> indico para qual porta eu quero que meu servidor aponte.
- `CMD` ["ng", "serve", "--host", "0.0.0.0"] -> digo qual comando deve rodar 


## ANGULAR SERVIDOR EM NODE COM DOCKER 
```dockerfile
FROM node:18.19.1
WORKDIR /app
COPY . .
RUN npm install
RUN npm install @angular/cli@18.2.10 -g
EXPOSE 4500
CMD ["ng", "serve", "--port=4500","--host", "0.0.0.0"]
```