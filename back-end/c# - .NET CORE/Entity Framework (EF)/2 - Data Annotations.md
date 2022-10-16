# Data Annotations

LINK REF DOC FULL: https://www.entityframeworktutorial.net/code-first/dataannotation-in-code-first.aspx


## O que é Data Annotations?

São `atributos` que podem ser aplicados a `classes e seus membros` para realizar as seguintes tarefas: 

1. Definir regras de `validação` para o modelo
2. Definir como os dados devem ser `exibidos` na interface
3. Especificar o `relacionamento` entre as entidades do modelo
4. Sobrescrever as `convenções` padrão do Entity Framework Core


### Um dos exempos é:

 - Serve para indicar ao banco de dados o que aquela propriedade deve seguir.

Exemplo:

```
public class Student
{
    public int StudentID { get; set; }
    [Required]
    public string StudentName { get; set; }
}
```

Estou dizendo que StudentName lá no banco de dados deve ser Obrigatório, ou seja NOT NULL, assim garantimos que caso no front insira um valor nullo vai gerar um erro de retorno para ele.

## Atributos para sobrescrever as convenções do EF Core

1. `Key` -> Identifica como `Primary Key`
2. `ForeignKey` -> Especifica que a prorpiedade é usada como uma `chave estrangeira`
3. `Table("NOME_TABELA")` -> Define o nome da tabela para qual a classe será mapeada
4. `Column` -> Define o nome da coluna para a qual a propriedade será mapeada
5. `DataType` -> Associa um tipo de dados adicional a uma propriedade
6. `NotMapped` -> Exclui a propriedade do mapeamento
7. `StringLength` -> Define o tamanho mínimo e máximo permitido para o tipo
8. `Required` -> Especifica que o valor do campo é obrigatório

## Mensagem de erro de acordo com a validação

 - Podemos exibir uma mensagem de erro para cada validação.
 
        Exemplo:

    ```
    public class Student
    {
        [Required(ErrorMessage = "Campo StudentName é obrigatório")]
        public string StudentName { get; set; }
    }
    ```