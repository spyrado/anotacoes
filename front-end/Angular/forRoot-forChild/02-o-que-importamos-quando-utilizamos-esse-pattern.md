# O que importamos quando utilizamos o .forRoot ou o .forChild?

Ao importar algum modulo com o `.forRoot` ou `.forChild`, estamos apenas injetando o serviço dele no nosso import

<img src="imgs/Captura de tela 2024-09-15 093115.png" width="350"/><br>

Não estamos trazendo,
as `declarations` dele junto:

<img src="imgs/Captura de tela 2024-09-15 093208.png" width="350"/><br>

feito isso, nossa service passa a ser singleton ( apenas uma instancia para a aplicação toda )<br>
e agora qualquer outro lugar que eu importar o `PollingModule` SEM o uso de `.forRoot` ou `.forChild` ele pegará apenas as `declarations`.

<img src="imgs/Captura de tela 2024-09-15 093743.png" width="350"/><br>