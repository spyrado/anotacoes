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
Dockerfile
```dockerfile
FROM node:18.19.1
WORKDIR /app
COPY . .
RUN npm install
RUN npm install @angular/cli@18.2.10 -g
EXPOSE 4500
CMD ["ng", "serve", "--port=4500","--host", "0.0.0.0"]
```


## ANGULAR SERVIDOR EM NGINX
Dockerfile
```dockerfile
FROM node:18.19.1 as builder
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/dist/angular-estudo-26-10-2024/browser /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
COPY mime.types /etc/nginx/mime.types
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

nginx.conf
```nginx
events {
  worker_connections 1024;
}

http {
  server {
    include /etc/nginx/mime.types;
    default_type application/octet-stream;
    listen  80;
    server_name localhost;


    location / {
      root /usr/share/nginx/html;
      index index.html;
      try_files $uri $uri/ /index.html;
    }

    error_page 500 502 503 504 /50x.html;
    location = /50x.html {
      root /usr/share/nginx/html;
    }
    
  }
}
``` 

mime.types
```
types {
    text/html                  html htm shtml;
    text/css                   css;
    application/javascript     js;
    application/json           json;
    image/gif                  gif;
    image/jpeg                 jpeg jpg;
    application/xml            xml;
    text/xml                   xml;
    image/png                  png;
}
```