# Controller

### Alguns pontos sobre controlers

![](./images/controller.png)

- ```[ApiController]``` -> é um decorator que habilita
a classe abaixo a ser uma controller

- ```[Route("[controller]")]``` -> aqui definimos o nome da rota, quando inserimos controller significa que queremos que o nome da nossa classe seja o nome da controller ou seja se eu fizer algo como: <br/> 
```
  [ApiController]
  [Route("[controller]")]
  public class PessoaController : ControllerBase
```
o nome da nossa rota será /pessoa

- ```[Route("nome_personalizado")]``` -> dessa forma o nome da nossa rota passa a ser ```/nome_personalizado``` independente do nome da Controller