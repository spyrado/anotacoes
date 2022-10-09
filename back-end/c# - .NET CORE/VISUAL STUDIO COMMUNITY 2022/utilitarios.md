# Utilitários

## Hot Reload

Disponível a partir da versão 2022, ele basicamente reduz o tempo que precisamos gastar esperando por atualizações no aplicativo. 

No Visual Studio 2019 existia mas exigia o uso do Depurador ( Modo Debug )

Também disponivel usando a linha de comando

## Quando o Hot Reload funciona?

Disponível para alterações em:

- Tipos
- Iteradores
- Expressões assíncronas / await
- Expressões LINQ
- Lambdas
- Dynamic objects
  
Não disponível para:

- Renomear elementos
- Remoção de namespaces, tipos e membros
- Modificação de interfaces
- Modificação de assinaturas de método

## Como configurar o Hot Reload?

Vá até o menu:

- Tools -> Options -> Debugging -> .NET / C ++ Hot Reload