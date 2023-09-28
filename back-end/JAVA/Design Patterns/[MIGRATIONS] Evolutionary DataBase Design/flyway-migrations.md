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

- Com a estrutura de pastas criada, vá até o seu banco de dados e de um `export database as SQL`