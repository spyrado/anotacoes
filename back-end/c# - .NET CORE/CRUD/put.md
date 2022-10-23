# Como fazer um Put em .NET Core
```
[HttpPut("{id:int}")]
public ActionResult<Produto> Put(int id, Produto produto) {

  // Aqui o usuário pode passar um id na url diferente do id do produto e vice versa
  // Exemplo: /Produtos/2 porem no objeto produto ele passa produto.Id 45
  // Se removermos essa validação o c# vai entender que é para criar um novo produto caso o produto anterior venha
  // sem id
  if(id !== produto.Id) return BadRequest();

  // Aqui persistimos o dado em memória mas não enviamos para o banco de dados
  _context.Entry(produto).State = EntityState.Modified;
  
  // Aqui pegamos o dado armazenado em memória e enviamos para o banco de dados.
  _context.Produto?.SaveChanges();

  // aqui retornamos um Ok(Status 200) e retornamos o próprio produto que enviaram na requisição
  // pois esse produto foi salvo no banco com as modificações solicitadas, então
  // ele está igual no banco de dados.
  return Ok(produto);
}
```
## Qual a diferença entre .Update e Entry para atualizar uma entidade no banco de dados?

`_context.Produto?.Update(produto)` -> Para quando a entidade já está sendo Tracked(rastreada) -> e pq uma entidade tem que estar tracked?
`_context.Entry(produto).State = EntityState.Modified;` -> Para quando uma entidade está em um cenário sem rastreio -> Não entendi, estudar sobre dps