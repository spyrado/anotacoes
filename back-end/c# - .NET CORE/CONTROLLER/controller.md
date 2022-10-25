# Controller

### Alguns pontos sobre controlers

![](./images/controller.png)

- ```[ApiController]``` -> é um decorator que habilita
a classe abaixo a ser uma controller, e habilita alguns recursos, como:
  1. Requisito de roteamento de atributo
  2. Respostas HTTP 400 Automáticas `( Validação do Model State )`
  3. Inferência de parâmetro de origem de associação
  4. Inferência de solicitação de dados de várias partes/formulário
  5. Uso de `Problem Details` para códigos de status de erro

- ```[Route("[controller]")]``` -> aqui definimos o nome da rota, quando inserimos controller significa que queremos que o nome da nossa classe seja o nome da controller ou seja se eu fizer algo como: <br/> 
```
  [ApiController]
  [Route("[controller]")]
  public class PessoaController : ControllerBase
```
o nome da nossa rota será /pessoa

- ```[Route("nome_personalizado")]``` -> dessa forma o nome da nossa rota passa a ser ```/nome_personalizado``` independente do nome da Controller

> Mais detalhes sobre o Route a seguir: 
```
  [ApiController]
  [Route("[controller]")]
  public class TesteController : ControllerBase
```

O `[Route]` especifica um padrão de URL para acessar um `controller` ou `Action`<br>
`[Route("[controller]")]` -> indica a rota com o nome do controlador `(que nesse caso é Teste)`

- ```ControllerBase``` -> É a classe base onde fornece muitas propriedades e métodos que servem para lider com as requisições HTTP.<br>
  Exemplos:

  1. BadRequest() -> Retorna o status 400
  2. NotFound() -> Retorna o status 404
  3. CreatedAtAction() -> Retorna o status 201
  4. PhysicalFile() -> Retorna um arquivo
  5. TryValidationModel -> Invoca a validação do modelo
  6. Ok() -> Retorna o status 200

## Como ativar uma controller?

para que as controllers do `.NET` funcione, você deve configura-las no arquivo `Program.cs`, segue comandos: 

- `builder.Services.AddControllers();` -> adiciona as controller 
- `app.MapControllers();` -> mapeia elas.

## Como chamar mais de um mesmo metodo http em uma única CLASSE?

Primeiro vamos entender o conceito.

Quando não temos duplicidade de metodos HTTP (exemplo, 2 GET em uma mesma controller) a controller geralmente segue esse padrão: <br>

```
  [ApiController]
  [Route("[controller]")]
  public class TesteController : ControllerBase
```

Logo o `[Route("[controller]")]` quando colocamos `[controller]` estamos falando que queremos que o nome da classe,
seja o nome da nossa controller, ou seja, nesse exemplo `Teste`Controller onde `Teste` é o nome da nossa controller.

então os endpoints ficam como

GET -> /teste
POST -> /teste
PUT -> /teste
DELETE -> /teste

# Mas e se eu precisar de mais de um get para a mesma controller?

Ai podemos trabalhar com `actions` elas nos dão essa liberdade:

ainda com o mesmo exemplo:
```
  [ApiController]
  [Route("[controller]/{action}")]
  public class TesteController : ControllerBase
```

Ao adicionarmos action para a `Route` estamos falando que o nome do nosso método com o decorator http é que vai ser o nome do nosso endpoint `[Route("[controller]/{action}")]`.

Exemplo:

```
[HttpGet]
public string Mensagem() {
  return "qualquer_coisa";
}
```

agora meu endpoint vai ser:

GET -> /teste/Mensagem




