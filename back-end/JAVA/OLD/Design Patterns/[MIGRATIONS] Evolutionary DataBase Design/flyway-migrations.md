# Flyway

## O que é?

- É uma ferramenta que te possibilita exucutar migrações no banco.
- Desfazer migrações
- Pode fazer migrações baseadas em `SQL`
- Migrações repetidas que a cada execução ela é recriada.
- Existem `MIGRATIONS` baseadas em código JAVA/KOTLIM 
- Versionamento de `.sql`
  - ![alt](./imgs/versionamento.png)

## Como usar?

- Instale as dependencias no seu `pom.xml`
```
<dependency>
	<groupId>org.flywaydb</groupId>
	<artifactId>flyway-core</artifactId>
</dependency>

<dependency>
	<groupId>org.flywaydb</groupId>
	<artifactId>flyway-mysql</artifactId>
</dependency>

```

- Crie a seguinte estrutura de pastas dentro de `src/main/resources`
  - crie a pasta `db`
  - e dentro da pasta `db` crie a `migration`
  - dentro da pasta `migration` você irá colocar os seus versionamentos definidos no `FlyWay`

```
src/main/resources/
│
├── db/
│ ├── migration/
│ ├── V1__XPTO.sql
```

- Com a estrutura de pastas criada, vá até o seu banco de dados e de um `export database as SQL`,
  ou se ele não possuir faça manualmente pegando todas as tabelas e todos os inserts dela se possivel.
- no exemplo de estudo eu tive que pegar a criação da tabela pesoa e os inserts, e o nome dos 
  scripts ficaram assim:
  - `V1__Cria_Tabela_Pessoa.sql`
  - `V2__Popula_Tabela_Pesspa.sql`
  - coloquei eles dentro de 
  - 
  ```
    src/main/resources/
    │
    ├── db/
    │ ├── migration/
    │ ├── V1__Cria_Tabela_Pessoa.sql
    │ ├── V2__Popula_Tabela_Pesspa.sql
  ```
  - >`IMPORTANTE`: após fazer tudo isso, verifique se a configuração do seu hibernate no `application.yml`
    está configurado como `ddl-auto: update`, se estiver `MUDE` para `ddl-auto: none`.
    pois o `update` ele pega as `entidades` gera o sql e cria o banco pra mim, mudando para `none` o hibernate vai apenas `ler e gravar informações` ele não vai mais mudar a estrutura do banco pra mim, agora quem vai fazer isso vai ser o `flyway`
  - mapeando todo o seu banco de dados, você já pode ir no seu banco local, e dar um drop nas tabelas     dele, pois o flyway vai gera-las ao iniciar o código.

## Após integrar com o fly way

- ele vai criar as tabelas de acordo com o que você colocou em `src/main/resources/db/migration`
- la no banco ele vai adicionar uma tabela de controle chamada `flyway_schema_history`,
  nela contem todo o `histórico` de migrações/criaçoes/mudanças e etc.
- `flyway_schema_history` colunas:
  - `description`: é o nome do seu script `.sql` dentro de `src/main/resources/db/migration`
  - `checksum`: é um `hash` gerado para controlar o script, se um dia alguém mudar um `espaço` que seja,
    o valor do `checksum` vai mudar, resultando em erro na hora de startar a aplicação.
    - exemplo de erro quando eu altero o arquivo `V2__Popula_Tabela_Pesspa.sql`: 
    ``` 
      Caused by: org.flywaydb.core.api.exception.FlywayValidateException: Validate failed: Migrations have failed validation
      Migration checksum mismatch for migration version 2
      -> Applied to database : 1470983646
      -> Resolved locally    : 1939374397
    ```