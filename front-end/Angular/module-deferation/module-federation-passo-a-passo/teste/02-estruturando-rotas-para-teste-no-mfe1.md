# Estruturando rotas para teste no MFE1

Passo a passo:

1. por enquanto não temos componentes, apenas um aplicação que vai servir de `chassi`, e outra que vai servir de `mfe1`
2. vamos organizar nosso `mfe1` para conseguir rodar ele localmente
3. rode o comando `cd workspace/`
4. agora inicie o servidor `ng serve mfe1 -o` ou `run:all mfe1`
5. vamos remover o template inicial de `app.component.html`
6. no lugar dele vamos adicionar o `<router-outlet></router-outlet>`
7. e para fazer com que o router-outlet funcione vamos importar em `app.module` o `RouterModule`
   - `POREM` se no seu projeto já está importando o `AppRoutingModule` dentro de `app.module`
   - não será necessário importar novamente o `RouterModule` pois o `AppRoutingModule` já importa ele.
8. vamos agora criar um componente `home` para servir apenas para o nosso `mfe1` navegar entre oq foi desenvolvido.
   - `IMPORTANTE` não vamos utilizar esse componente `home` no nosso chassi, ele é apenas para facilitar no desenv do `mfe1`.
9. entre em `cd workspace`
10. digite o comando `ng g m home --route=home --module=app  --project=mfe1` ( o `--project` indica para qual projeto você quer realizar a ação )
    - o comando acima diz, gere um modulo chamado `home` sua rota ficara dentro de `home` e quem vai carregar essa rota vai ser o `app`
    - esse comando já vai importar todas as dependencias de rotas e já vai colocar o `HomeRoutingModule` dentro de `home.module`
11. altere em app.routing.module de `mfe1` o `path` de `path: 'home'` para `path: ''`
12. abra o seu mfe1 no navegador e em sua tela deve aparecer `home works`
13. para finalizar vamos adicionar esse `html` dentro de `home.component.html`:

    ```
    <div style="display: flex; align-items: center">
    <div>
       <img
          style="margin-right: 16px"
          width="40"
          alt="Angular Logo"
          src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNTAgMjUwIj4KICAgIDxwYXRoIGZpbGw9IiNERDAwMzEiIGQ9Ik0xMjUgMzBMMzEuOSA2My4ybDE0LjIgMTIzLjFMMTI1IDIzMGw3OC45LTQzLjcgMTQuMi0xMjMuMXoiIC8+CiAgICA8cGF0aCBmaWxsPSIjQzMwMDJGIiBkPSJNMTI1IDMwdjIyLjItLjFWMjMwbDc4LjktNDMuNyAxNC4yLTEyMy4xTDEyNSAzMHoiIC8+CiAgICA8cGF0aCAgZmlsbD0iI0ZGRkZGRiIgZD0iTTEyNSA1Mi4xTDY2LjggMTgyLjZoMjEuN2wxMS43LTI5LjJoNDkuNGwxMS43IDI5LjJIMTgzTDEyNSA1Mi4xem0xNyA4My4zaC0zNGwxNy00MC45IDE3IDQwLjl6IiAvPgogIDwvc3ZnPg=="
       />
    </div>
    <h1>MFE1 teste de componentes</h1>
    </div>

    <h3>Rotas disponíveis:</h3>
    <ul style="display: flex; list-style: none; gap: 16px">
    <li><a routerLink="/rota1">rota1</a></li>
    <li><a routerLink="/rota2">rota2</a></li>
    <li><a routerLink="/rota3">rota3</a></li>
    </ul>

    ```

14. e pronto no arquivo `03` vamos aprender como criar um componente, e linkar ele, tanto no mfe1 para teste quando no chassi(shell) como mfe de fato.
