# Lista de como podemos tratar os erros no C# / .NET Core

## Importancia de tratar um erro

É importante realizar o tratamento de erros pois podemos deixar nossa aplicação vulnerável<br>ao mandar todo o `stack trace` como resposta do erro para o front end.
<br/>
<br/>

## 1º Utilizando o famoso try catch

Podemos lançar exceções personalizadas com ele segue um exemplo:

```

  try
  {
    throw new Exception(); // aqui estou forçando uma exception só para mostrar como funciona o catch
  }
  catch (Exception)
  {

    return StatusCode(StatusCodes.Status500InternalServerError, "Ocorreu um problema ao tratar a sua solicitação");
  }

```

nessa linha: `return StatusCode(StatusCodes.Status500InternalServerError, "Ocorreu um problema ao tratar a sua solicitação");`<br>
nós estamos falando para retornar um status code do tipo 500 ( pois é um erro interno do servidor ) e eu mando uma mensagem<br>
customizada para que o usuário não tenha acesso a informação de erro no detalhe de implementação.