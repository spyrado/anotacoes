# Como configurar os seus repositories?


1. primeiro você deve estar logado como admin
2. você deve criar 3 repositories:
    - **SIGNIFICADO DE CADA UM:**
      - `npm-proxy:`
        - esse npm vai servir como um proxy para quando você tentar baixar dependencias do `npm-hosted` e caso não tenha essas dependencias no `npm-hosted` ele vai buscar no link do proxy que você configurou.
      - `npm-hosted:`
        - esse aqui representa o seu repositório PRIVADO INTERNO, que vai subir as coisas da sua empresa.
      - `npm-group:`
        - esse cara junta tanto o `npm-hosted` quanto o `npm-proxy` e disponibiliza tudo que foi upado até então para quem vai consumir.
    - **COMO CRIAR CADA UM:**
      1. `npm-proxy:`
          - vá até "Repositories" e depois em "+ Create repository"
          - escolha o npm (proxy)
          - no campo `Name` de o nome de npm-proxy
          - no campo `Remote Storage` você deve colocar o link que ele deve buscar quando o projeto tentar baixar alguma dependencia do `npm-hosted` e não achar nada, geralmente colocamos o `https://registry.npmjs.org`, pq caso ele tente baixar o angular por exemplo e não ache no npm-hosted ele vai buscar no npm publico.
          - mantenha o resto como está e clique em `create repository`
      2. `npm-hosted:`
          - vá até "Repositories" e depois em "+ Create repository"
          - escolha o npm (hosted)
          - no campo `Name` de o nome de npm-internal
          - mantenha o resto como está e clique em `create repository`
      3. `npm-group:`
          - vá até "Repositories" e depois em "+ Create repository"
          - escolha o npm (group)
          - no campo `Name` de o nome de npm-group
          - no campo `Member repositories` você deve vincular os 2 repositórios que você acabou de criar(`npm-proxy e npm-internal`) ao npm-group
          - mantenha o resto como está e clique em `create repository`
      4. pronto com isso você configurou tudo que tinha para configurar de repositorio