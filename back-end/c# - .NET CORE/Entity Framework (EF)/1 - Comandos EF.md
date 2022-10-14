# Lista de Comandos do Entity Framework

> Comandos via Command Line

- ```donet ef``` &rarr; Comando base.
- ```donet ef migrations add 'nome' ``` &rarr; Adiciona o script de migração.
- ```donet ef migrations remove 'nome' ``` &rarr; Remove o script de migração criado.
- ```donet ef database update``` &rarr; Gera o banco de dados e as tabelas com base no script.


> Comandos via Package Manager Console

- ```add-migration 'nome'```
- ```remove-migration 'nome'```
- ```update-database```