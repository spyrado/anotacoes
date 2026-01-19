# Comandos docker compose

- `docker-compose up`: Lê o arquivo docker-compose.yml e sobe toda a configuração definida nesse arquivo, e prende o terminal que foi executado o comando.
- `docker-compose up -d`: faz a mesma coisa que o comando anterior, porem o -d não fica prendendo o seu terminal, ele executa e já libera o terminal, ou seja:
  - ✅ Sobe os containers normalmente
  - ✅ Libera o terminal imediatamente
  - ✅ Deixa os containers rodando em background