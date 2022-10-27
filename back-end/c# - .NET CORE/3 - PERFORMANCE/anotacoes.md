# Performance

## IEnumerable vs List, qual usar?
<p style="color: #40a240;">R: Se você for somente ler e ou filtrar algum dado, utilize IEnumerable ele é mais performático é apenas uma interface.
<br> 
Se você precisa adicionar ou remover algo da lista utilize a Classe List.</p>

## Otimizando o código nas consultas com `HTTP GET`
> **Nota:** Quando consultamos entidades usando o Entity Framework ele armazena as entidades no contexto ( `em cache` )<br>
> realizando o tracking ou rastreamento das entidades para acompanhar o estado das entidades

> **Warning**: Porem este recurso `adiciona uma SOBRECARGA` que afeta o desempenho das consultas rastreadas

<p style="color: #40a240;">R: Para solucionar isso pedimos que ele não use Tracking (Rastreio), segue exemplo:<br></p>

```
var produtos = _context.Produtos.AsNoTracking().ToList();
```
> **Recomendação**: Utilizar o método AsNoTracking quando tivermos metodos de apenas `LEITURA` que não<br>
> tenha a necessidade de `ALTERAÇÃO`, pois o AsNoTracking tira o rastreio da entidade e se for o caso de uma edição<br>
> você irá perder essa rastreabilidade
