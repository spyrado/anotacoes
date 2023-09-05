# Lista de annotation em java.

1. `@RestController`: indica para o framework que se trata de um controlador Rest, voltado para o desenvolvimento de aplicações web Restful e facilita que nós lidemos com requisições web (POST, GET, PUT, etc) pois une o Controller a um ResponseBody para todos métodos marcados pelo RequestMapping
   ![alt](./imgs/RestController.png)
2. `@RequestMapping`: para se tornar um endpoint, você  precisa adicionar essa annotation passando o caminho do endpoint.
   ![alt](./imgs/request-mapping.png)
3. `@RequestParam`: para que o metodo receba parametros no endpoint vc deve utilizar essa annotation
    ![alt](./imgs/RequestParam.png)