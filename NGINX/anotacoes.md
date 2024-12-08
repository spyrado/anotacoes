# NGINX

## Comandos Úteis

- `nginx -t`: verifica se a estrutura do seu arquivo está correta
- `nginx -s reload`: recarrega o seu servidor
- `start nginx`: inicia o seu servidor
- `nginx -s stop`: para o seu servidor
- `nginx -h`: te da todos os comandos e oq cada um faz

## Estrutura de arquivo


### significado:

```
worker_processes  1;

events {
	worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;
    sendfile        on;
    keepalive_timeout  65;
    server {
			listen       8080;
			server_name  localhost;
			location / { // 1. quando a requisição for para barra (/) 
				root   html; // 2. buscar dentro de html
				index  index.html index.htm; // 3. um arquivo chamado index.html
			}
			error_page   500 502 503 504  /50x.html;
			location = /50x.html {
				root   html;
			}
    }
		include C:/Server/servers/*.conf;
}

```

`server`: é onde fica as configurações do seu servidor em si
  - `listen`: você diz em qual porta vai ficar ouvindo ( geralmente 80 )
  - `server_name`: define o nome do servidor ou domínio exemplo: www.google.com
`include C:/Server/servers/*.conf`: esse cara em especifico eu quero incluir outra configuração de servidor,
segue exemplo do que tem dentro do arquivo:
	```
	server {
		listen 80; // ouça na porta 80
		server_name localhost;

		location / {
			root C:/Users/nicol/servidorteste; // aqui eu passo o caminho absoluto
			index index.html; // aqui falo q para o root peque o index.html
		}
	}

	```