`Implementação do endpoint`
```
[HttpPatch("{id}")]
public ActionResult<Produto> Patch(int id, Produto produto)
{
  if (id != produto.Id) return BadRequest();
  _context.Entry(produto).State = EntityState.Modified;
  _context.SaveChanges();
  return Ok(produto);
}
```

## Quando eu faço um patch de
`Envio para o endpoint:` 
```
{
  "id": 10,
  "nome": "Esse nome aqui é diferente",
  "descricao": "DESCRICAOOOOOO AQUI OOO",
  "imagemUrl": "image.jpg",
  "categoriaId": 3
}
```

`Retorno do endpoint`
```
{
    "id": 10,
    "nome": "Esse nome aqui é diferente",
    "descricao": "DESCRICAOOOOOO AQUI OOO",
    "preco": 0,
    "imagemUrl": "image.jpg",
    "estoque": 0,
    "dataCadastro": "0001-01-01T00:00:00",
    "categoriaId": 3,
    "categoria": null
}
```

minha Action retorna a entidade toda do banco, porem eu não dei um find no banco para pegar a entidade toda, como
o Entity Framework entende isso?