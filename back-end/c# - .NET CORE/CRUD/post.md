# Como fazer um post em .NET Core
```
[HttpPost]
public ActionResult<Produto> Post(Produto produto) {
  // Aqui persistimos o dado em memória mas não enviamos para o banco de dados
  _context.Produto?.Add(produto);
  // Aqui pegamos o dado armazenado em memória e enviamos para o banco de dados.
  _context.Produto?.SaveChanges();

  // e aqui retornamos o produto inserido no banco de dados dessa forma:
  return CreatedAtAction('GetById', new { id = produto.Id }, produto);
  // aqui vou traduzir o código acima
  return CreatedAtAction('NomeDaAction', "PARAMETROS DA ACTION", "RETORNO DO ENDPOINT");
}
```