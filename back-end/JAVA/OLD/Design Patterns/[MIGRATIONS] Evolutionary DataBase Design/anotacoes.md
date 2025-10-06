# Evolutionary DataBase Design

`LINK REF:` https://www.martinfowler.com/articles/evodb.html

## O que é?

- é um `CONCEITO` de evolução do banco de dados
- TODOS os artefatos do banco são controlados e você consegue versionalos
- Todas as mudanças do banco são `MIGRATIONS`
- Cada um tem sua instancia LOCAL, você não vai se conectar a um banco CENTRAL
- `MIGRATIONS` são aplicadas e integradas da mesma forma que o código é.


## Ferramentas para executar MIGRATIONS

`LINK REF:` https://www.martinfowler.com/articles/evodb.html


- Liquibase, a framework to manage database migrations
- MyBatis migrations, a framework to manage database migrations
- Flyway, a framework to manage database migrations
- DBDeploy, a framework to manage database migrations
- DBmaestro, a commercial tool to enable evolutionary database development
- RedGate, a commercial tool to enable evolutionary database development
- Datical, a commercial tool to enable application release process by automating database release management
- Jailer, a tool to extract subsets of data from a database
- DiffKit, a framework to compare two sets of data and report any differences
- DbUnit, a JUnit extension, used in testing databases
- DbFit, a tool to write readable, easy-to-maintain unit and integration tests for your database code.
- Data Anonymization, a tool to anonymize production data for development use.