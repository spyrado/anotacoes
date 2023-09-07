# Lista de annotation em java.

1. `@RestController`: indica para o framework que se trata de um controlador Rest, voltado para o desenvolvimento de aplicações web Restful e facilita que nós lidemos com requisições web (POST, GET, PUT, etc) pois une o Controller a um ResponseBody para todos métodos marcados pelo RequestMapping.<br>
   ![alt](./imgs/RestController.png)

2. `@RequestMapping`: para se tornar um endpoint, você  precisa adicionar essa annotation passando o caminho do endpoint.
   1. endpoint sem parametros na url (path param)
   ![alt](./imgs/request-mapping.png)

   2. Endpoint com parametros na url (path param)
   ![alt](./imgs/request-mapping-path-parameter.png)

3. `@RequestParam`: para que o metodo receba parametros no endpoint vc deve utilizar essa annotation
    ![alt](./imgs/RequestParam.png)

4. `@PathVariable`: recupera as variaveis declaradas dentro de `@RequestMapping` do exemplo `2.2`. 
   1. Segue exemplo:<br>
   ![alt](./imgs/path-variable.png)
   
5. `@ResponseStatus`: diz o status que a classe irá retornar (400, 500, 200 e etc.)
   
6. `@ControllerAdvice`: ele funciona como um interceptor, no exemplo de tratamento de exceções, 
se colocado em um handler de exceções ele vai ser ativado toda vez que o código identificar que não existe um tratamento específico para aquela exceção vai cair na nossa exceção generica.


# Diferenças entre PathVariable e RequestParam

- `@RequestParam` você pode passar vários parâmetros no client que o endpoint não dará erro
- `@PathVariable` já com path, se você passar path não esperado pelo endpoint dará erro.
