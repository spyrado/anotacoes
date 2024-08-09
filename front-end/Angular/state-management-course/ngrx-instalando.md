## Instalando NGRX

Para instalar o NGRX, rode o seguinte comando:

`Comandos:`<br>
  - ```ng add @ngrx/store``` 
    - Este comando integrará o NGRX ao seu projeto, adicionando automaticamente o módulo StoreModule ao seu AppModule. O StoreModule é responsável por gerenciar o estado global da aplicação, proporcionando uma "base de dados" centralizada para gerenciar o estado de forma eficiente.
  - ```ng add @ngrx/devtools```
    -  > dependencias: após instalar o comando devemos também ir no chrome e baixar o [Redux DevTools](https://chromewebstore.google.com/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=en)
    - ele vai adicionar nosso `StoreDevtoolsModule.instrument({ maxAge: 25, logOnly: environment.production })` ao `app.module`
      - maxAge: 25:
        - Define o número máximo de estados que o DevTools vai armazenar na sua história de ações. Neste caso, ele irá manter os últimos 25 estados da aplicação. Isso é útil para economizar memória e evitar sobrecarga.
      - logOnly: environment.production:
        -  Quando definido como true, o DevTools apenas registra as ações sem permitir alterações manuais no estado através da interface das ferramentas DevTools. Isso é especialmente importante para produção, pois evita que usuários possam modificar o estado da aplicação através do DevTools.
    - O comando ng add @ngrx/devtools adiciona o NGRX Store DevTools ao seu projeto Angular. 
    - O NGRX DevTools é uma ferramenta de depuração que ajuda a monitorar e inspecionar o estado da aplicação. 
    - Ele fornece funcionalidades como:
      - Time-travel Debugging: Permite reverter e avançar nas ações para ver mudanças no estado.
      - Logging de Ações: Registra todas as ações despachadas e suas consequências.
      - Inspeção de Estado: Oferece uma visualização detalhada do estado atual.
    - Essas funcionalidades são integradas diretamente ao seu projeto e podem ser visualizadas por meio de extensões de navegador, como o Redux DevTools


