## Como gerar um certificado https para node?

> é importante sua aplicação ter certificado https, pois impede que suas requisições sejam rastreadas com facilidade, sem https se o usuário mandar um post de login, eu consigo ver tranquilamente, pq ele não criptografa a informação que está trafegando na rede

Vá até a raiz do seu projeto e insira esse comando: 
 - `openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout server.key -out server.crt`


como configurar no node?


deixe de usar o listen dessa forma:
```typescript
server.listen(8000, () => {
  console.log("API disponível em http://localhost:8000")
})

```

e agora passe a utilizar com o modulo https juntamente com as configs do certificado
```typescript
const fs = require('fs')
const jsonServer = require('json-server')
const server = jsonServer.create()
const https = require('https')

https.createServer(
  {
    key: fs.readFileSync('server.key'),
    cert: fs.readFileSync('server.crt')
  },
  server
).listen(8000, () => {
  console.log("API disponível em https://localhost:8000")
})
```