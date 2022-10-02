# Tipos de retornos de métodos HTTP

GET
 - 200 OK -> Se o recurso existir
 - 404 Not Found -> Se o recurso não existir
 - 500 Internal Server Error -> para outros erros
  
POST
 - 201 CREATED -> se um novo recurso foi criado
 - 500 Internal Server Error -> para outros erros
  
PUT
 - 200 OK -> se o recurso foi atualizado com sucesso
 - 404 Not Found -> Se o recurso a ser atualizado não existir
 - 500 Internal Server Error -> para outros erros

DELETE
 - 200 OK -> se o recurso foi deletado com sucesso
 - 204 No Content -> caso você não precise passar um response.
 - 404 Not Found -> Se o recurso a ser deletado não existir
 - 500 Internal Server Error -> para outros erros