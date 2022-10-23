```
    [HttpDelete("{id:int}")]
    public ActionResult<Produto> Delete(int id)
    {
      var produto = _context.Produtos?.FirstOrDefault(produto => produto.Id == id);
      if(produto is null) return NotFound("Produto não encontrado...");

      _context.Produtos?.Remove(produto);
      _context.SaveChanges();

      return Ok(produto);
    }
```

## Dúvidas, ao inves de dar um FirstOrDefault no delete, eu poderia simplesmente reutilizar o meu método
## GetById, ou seja é uma boa prática reutilizar uma action para dar suporte em outra Action?

```
[HttpGet("{id}", Name = "ObterProduto")]
public ActionResult<Produto> GetById(int id)
{
  var produto = _context.Produtos?.FirstOrDefault(produto => produto.Id == id);
  if(produto is null) return BadRequest();
  return produto;
}
```