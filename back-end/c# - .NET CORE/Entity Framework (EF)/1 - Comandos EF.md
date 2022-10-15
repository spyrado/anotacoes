# Lista de Comandos do Entity Framework

> Comandos via Command Line

- ```donet ef``` &rarr; Comando base.
- ```donet ef migrations add QUALQUER_NOME ``` &rarr; Ao rodar o comando, ele pega tudo que você mapeou no código e cria um script a partir do código gerado.
- ```donet ef migrations remove QUALQUER_NOME ``` &rarr; Remove o script de migração criado.
- ```donet ef database update``` &rarr; Gera o banco de dados e as tabelas com base no script.


> Comandos via Package Manager Console

> Porem esses comandos só vão rodar caso você instale o Nuget Microsoft.EntityFrameworkCore.Tools

- ```add-migration QUALQUER_NOME```
- ```remove-migration QUALQUER_NOME```
- ```update-database```