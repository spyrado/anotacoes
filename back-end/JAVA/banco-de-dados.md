# MYSQL

## Como conectar o banco no spring?

1. adicione essas dependencias no seu `pom.xml`:
2. 
  ```
    <!-- INICIO Dependencias do Banco de dados -->
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>
    <dependency>
        <groupId>com.mysql</groupId>
        <artifactId>mysql-connector-j</artifactId>
    </dependency>
    <!-- FIM Dependencias do Banco de dados -->
  ```
  3. após isso vá até a pasta `src/main/resources/application.yml` e adicone essa
    configuração de conexão:<br>
    ```
      spring:
        datasource:
          dbcp2:
            driver-class-name: com.mysql.cj.jdbc.Driver #Driver necessário para o funcionamento
            url: jdbc:mysql://localhost:3306/NOME_DO_SEU_BANCO_DE_DADOS?useTimezone=true&serverTimezone=UTC
            username: spyrado
            password: admin123 
    ```


## Como conectar o JPA Hibernate que comunica com o banco no spring?

  1. vamos até o caminho `src/main/resources/application.yml`
  2. colocamos essa configuração
      ```
      spring:
        datasource:
          dbcp2:
            driver-class-name: com.mysql.cj.jdbc.Driver
            url: jdbc:mysql://localhost:3306/java_spring_mysql?useTimezone=true&serverTimezone=UTC #evitando problemas de time zone com esses parametros ?useTimezone=true&serverTimezone=UTC
            username: spyrado
            password: admin123 
        # AQUI COMEÇA A CONFIG DO JPA
        jpa:
          hibernate:
            ddl-auto: update
          properties:
            hibernate:
              dialect: org.hibernate.dialect.MySQL8Dialect
            show-sql: false
      ```
  3. `ddl-auto` tem algumas opções e são `importantes` na config do seu projeto, os mais utilizados são: `update` e `none` vai depender do `workflow` do seu projeto e etc.
     1. `validate`: validate the schema, makes no changes to the database.
     2. `create-only`: database creation will be generated.
     3. `drop`: database dropping will be generated.
     4. `update`: update the schema.
        1. Se não existe cria
        2. Se existe e não mudou nada, não faz nada
        3. Se existe e mudou algo, atualiza.
     5. `create`: creates the schema, destroying previous data.
     6. `create-drop`: drop the schema when the SessionFactory is closed explicitly, typically when the application is stopped.
     7. `none`: does nothing with the schema, makes no changes to the database
  4. `dialect`: Informando o dialeto que o hibernate vai utilizar para se comunicar com o banco de dados
  5. `show-sql`: mudar para true quando quiser debugar