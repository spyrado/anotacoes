# Como plugar sua aplicação .NET Core no Banco de dados?

1. Instale esses pacotes: 
  - Pomelo.EntityFrameworkCore.MySql
  - Microsoft.EntityFrameworkCore.Design
  - Microsoft.EntityFrameworkCore.Tools OU dotnet tool install --global dotnet-ef via command line

2. Crie sua Entidade ( Classe que vai representar a tabela com as propriedades no banco de dados )
  - Exemplo:
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

3. Cria sua classe de contexto ( Classe que vai linkar a Entidade que voce criou com o Banco )
  - Exemplo: 
    ```
    namespace APICatalogo.Context
    {
      public class APICatalogoContext : DbContext
      {

        public APICatalogoContext(DbContextOptions<APICatalogoContext> options) : base(options)
        {
        }

        public DbSet<Produto>? Produtos { get; set; }
      }
    }
    ```

4. Em ```appsettings.json``` configure o seu banco de dados, voce pode definir qual connection string vc precisa, cada tipo<br> de banco de dados tem uma a do exemplo é uma do MySql, segue site para consulta: <br>
https://www.connectionstrings.com/<br>
https://www.connectionstrings.com/mysql
  - Exemplo:
    ```
    "ConnectionStrings": {
      "DefaultConnection": "Server=localhost;Database=CatalogoDB;Uid=spyrado;Pwd=123456;"
    },
    ```

5. Plugue toda a configuração feita em ```appsettings.json``` + A sua classe de contexto ```APICatalogoContext``` com o banco de dados, via servico dentro de ```Program.cs```
  - Exemplo:
    ```
      var builder = WebApplication.CreateBuilder(args);

      string mysqlConnection = builder.Configuration.GetConnectionString("DefaultConnection");

      builder.Services.AddDbContext<APICatalogoContext>(options =>
        options.UseMySql(mysqlConnection, ServerVersion.AutoDetect(mysqlConnection))
      );
    ```
    Resumo do que todo esse código faz:<br>
    ``` builder.Services.AddDbContext<NomeContexto>``` Adiciona minha Classe de contexto para ser configurada que no caso é ```APICatalogoContext```.<br>
    ```options.UseMySql``` Aqui eu informo qual é o meu provedor, que no caso é o MySql
    ```options.UseMySql(mysqlConnection``` E como parametro eu passo minha string de conexao que defini aqui: <br>
    ```string mysqlConnection = builder.Configuration.GetConnectionString("DefaultConnection");```<br>

    Feito isso, eu incluo no serviço de contexto do EF o container DI nativo e assim eu posso injetar uma instancia de APICatalogoContext aonde eu precisar dela.

6. Migrations do EF Core -> Ele oferece uma maneira de atualizar de forma incremental o esquema no banco de dados<br>
para mante-lo em sincronia com o modelo de dados do aplicativo, preservando os dados existentes no banco.
> **Importante**
> Sempre que você adicionar/remover alguma entidade e/ou prop da entidade, você deve executar o Migrations para que
> reflita no banco de dados
  