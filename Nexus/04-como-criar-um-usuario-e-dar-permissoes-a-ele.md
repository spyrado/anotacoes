# Como criar um usuário no Nexus e dar permissoes para ler e escrever no npm?


## Criando uma role de ler e escrever no npm

1. vá até o menu `Roles`
2. clique em `Create Role`
3. no campo `Type` selecione `Nexus Role`
4. no campo `Role Id` coloque o nome `npm-read-and-write-id`
5. no campo `Role Name` coloque o nome `npm-read-and-write-name`
6. clique no botão `Modify Applied Privileges` e digite na busca `npm`
    - procure pelas roles de nome:
      - `nx-repository-admin-npm-npm-group-browse` // para que o usuário consiga baixar dependencias
      - `nx-repository-admin-npm-npm-group-read` // para que o usuário consiga baixar dependencias
      - `nx-repository-view-npm-npm-internal-edit` // para que o usuário consiga publicar a lib
        
    - inclua elas, salve
7. após salvar as roles clique no botão `Save` no final para salvar a configuração como um todo e ter sua role.
8. pronto você acabou de criar uma role de ler e escrever no npm

## Vinculando a role criada a um usuário npm-deployer

1. vá até o menu `Users`
2. clique em `Create Local User`
3. nos campos: ID, First Name e Last Name coloque o nome `npm-deployer`
4. defina um e-mail para esse usuário
5. uma senha
6. deixa o Status como `Active`
7. no campo `Roles` associe a role criada que chamamos de `npm-read-and-write-name` a esse usuário
8. clique em `Create local user`
9. pronto temos um usuário com permissão para ler e escrever no npm.
