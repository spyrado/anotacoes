# Como logar localmente no seu repositório privado ( Nexus )?


## Cadastrando o Nexus na raiz do seu .npmrc
  1. vá até o nexus clique em `Repositories`
  2. clique no repositorio chamado npm-group
  3. procure pelo campo chamado `URL` e copie a url dele, no meu caso a minha é: http://localhost:8081/repository/npm-group/
  4. vá até o seu terminal
  5. de um `cat ~/.npmrc` ele vai mostrar o registry atual, provavelmente vai ser o `https://registry.npmjs.org` se quiser duplique o seu .npmrc para não perder as infos dele.
  6. vamos substituir esse registry pelo do nexus, rode o comando `npm config set registry="http://localhost:8081/repository/npm-group/"`
  7. pronto agora todo `npm install xpto` que você der vai bater sempre no Nexus

## Logando localmente no npm-group Nexus
  1. agora que já apontamos para o nexus no passo anterior
  2. rode o comando `npm login --registry=http://localhost:8081/repository/npm-group/`
  3. vai pedir o usuário e a senha lá do nexus que você criou no passo `04-como-criar-um-usuario-e-dar-permissoes-a-ele.md`
  4. coloque o usuário e a senha e pronto você vai conseguir se logar ao repo do nexus
  5. após isso qualquer `npm install xpto` que você der vai vir do nexus, caso não tenha no nexus vai dar erro.

## Logando localmente no npm-internal Nexus
  2. rode o comando `npm login --registry=http://localhost:8081/repository/npm-internal/`
  3. vai pedir o usuário e a senha lá do nexus que você criou no passo `04-como-criar-um-usuario-e-dar-permissoes-a-ele.md`
  4. coloque o usuário e a senha e pronto você vai conseguir se logar ao repo do nexus
  5. após isso você vai conseguir subir a sua lib para o repositório privado, é só dar o comando: `npm publish --registry=http://localhost:8081/repository/npm-internal/`