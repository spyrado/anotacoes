# Mockito

Um framework de testes que nos ajuda a mockar as coisas, tornando mais simples o dia dia.

## Como instalar?

1. adicione a dependencia ao maven
   ```
   <dependency>
     <groupId>org.mockito</groupId>
     <artifactId>mockito-core</artifactId>
     <scope>test</scope>
   </dependency>
   ```

<br>

---

<br>

### Anotações e seus significados

- `@InjectMocks`: Quando utilizamos InjectMocks, podemos injetar o nosso serviço dentro da nossa classe de testes.
  - ![a](../../imgs/injetando-service.png)
