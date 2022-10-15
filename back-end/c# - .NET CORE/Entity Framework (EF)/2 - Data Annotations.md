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