# Iniciando uma aplicação angular com module federation

> **Link Referência:** https://www.angulararchitects.io/blog/the-microfrontend-revolution-part-2-module-federation-with-angular/

## Passo a passo

- Certifique-se de estar com uma aplicação angular de versão 14 ou maior.
- Crie o projeto Angular sem a aplicação
  - **Comando CLI:** `ng new workspace --create-application=false`
- Agora crie as aplicações separadamente:
  1. `cd workspace`
  2. agora vamos criar as aplicações
  3. digite: `ng g application shell`
  4. digite: `ng g application mfe1`
  5. e pronto temos a estrutura de pastas.
- Agora vamos adicionar o module federation
  - **IMPORTANTE** sempre use o `@angular-architects/module-federation` juntamente com um @ na frente indicando a versão que é compatível com a versão do angular que você está utilizando.
  - _Exemplo:_
    - meu angular é versão 16
    - a versão compativel de module federation com o meu angular é a 16 também
    - então no meu comando eu preciso adicionar o @ dessa versão
      - segue exemplo:
        - `@angular-architects/module-federation@16.0.4`
  - acesse o seu workspace, no exemplo acima eu teria que acessar o `nome-do-meu-projeto`, e após acessar rode os comandos abaixo
    - **Comando CLI:** `ng add @angular-architects/module-federation@16.0.4 --project shell --port 4200 --type host`
    - **Comando CLI:** `ng add @angular-architects/module-federation@16.0.4 --project mfe1 --port 4201 --type remote`
- Exemplicando os comandos acima:
  - Estou adicionando a dependencia do module-federation ao projeto(--project) shell e mfe1
  - Para cada projeto eu adiciono uma porta diferente para conseguir executar ambos simultaneamente.
  - E por fim, eu defino o tipo de cada um.
    - Como o `shell` (chassi) vai ser o projeto base ele vai ser do tipo (type) `host`
    - E como o `mfe1` não é o projeto base (chassi), ele fica como `remote`.
