## Lista de atalhos para gerar um NGRX:

`Comandos:`
  - ng generate store auth/Auth --module auth.module.ts
    - eu estou dizendo que eu quero gerar um `StoreModule.forFeature` dentro de `auth.module.ts`
    - e juntamente com isso vai criar e configurar um reducer para esse store.
    - o primeiro `auth` representa em qual pasta eu quero colocar essa configuração
    - o segundo `Auth` é o nome da `KEY` que vamos adicionar ao nosso store, resultado final fica assim no `dev tools`:
      ```
        {
          auth: {}
        }
      ```