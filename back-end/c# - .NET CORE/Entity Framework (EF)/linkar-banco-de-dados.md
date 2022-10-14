# O que fazer para linkar com o banco

Para mais infos: https://www.entityframeworktutorial.net/efcore/entity-framework-core-console-application.aspx

1. Crie a Entidade

```
namespace APICatalogo.Domain;

public class Produto
{
  public int Id { get; set; }
  public string? Nome { get; set; }
  public string? Descricao { get; set; }
  public decimal Preco { get; set; }
  public string? ImagemUrl { get; set; }
  public float Estoque { get; set; }
  public DateTime DataCadastro { get; set; }
}

```


2. Crie sua classe de contexto que vai definir qual Entidade vc vai utilizar e o nome da tabela

```
namespace APICatalogo.Context
{
  public class APICatalogoContext : DbContext
  {

    public DbSet<Produto>? Produtos { get; set; }
  }
}
```