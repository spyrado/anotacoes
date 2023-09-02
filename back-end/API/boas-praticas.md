# BOAS PRATICAS

## Paginacao

A paginação é importante, para que tanto o client quanto o banco não fiquem onerosos, processem muitos dados, deixando a aplicação com mais performance.

## Filtros

Parametros que o usuário enviar para receber determinado resultado

## Definir recursos lógicos

Separar os recursos, exmeplo não criar um endpoint que faz tudo, cria um recurso(endpoint) de cliente, um de peças, um de ordem de serviço e etc.

## Tolerância a falhas

Colocar tratativas para todas as falhas que você identificar na aplicação para que sempre tenha uma resposta para o client

## Cache

Criar cache de requisições muito requisitadas, para evitar onerar o seu servidor.

## Conectividade

Sempre facilite os meios de conectividade com a sua API

## Timeouts

É fundamental que seu CLIENT não fique pendurado no seu servidor consumindo recursos.

Imagine que o server tentou processar a requisição do seu CLIENT e atingiu um tempo limite, você deve interromper e mandar uma mensagem de erro.
Isso impede que o CLIENT fique consumindo rescursos do seu servidor e impede que a aplicação inteira venha a cair.

## Documentação

Muito importante utilizar

## Utilizar SSL

É algo fundamental em aplicações profissionais

## Versionamento

faz com que a API fique mais facil de manter, e não quebra o uso de API's antigas.

## Teste e validação

Deve fazer testes que validem se a sua API está funcionando corretamente.

## API Self-service

com swagger e HATEAOS o CLIENT já consegue navegar e pelos links pode continuar navegando.

## Exportações

Interessante a sua API suportar o envio de EXCEL E ETC

## i18n / Globalization

Também deve ser considerado.

## Notificações

Notifique o client quando uma requisição vai ficar pendurada pois vai fazer um processamento longo.

## Limite de campos

??

## Monitore sua API

Observables talvez? assim conseguimos monitorar possiveis gargalos na API algum endpoint que está consumindo muito e tudo mais.

## Selecione a Tecnologia Adequada

Trabalhar com REST SOA SOAP 