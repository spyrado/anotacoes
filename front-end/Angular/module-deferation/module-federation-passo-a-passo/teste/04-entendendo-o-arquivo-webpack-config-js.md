# Entendendo o arquivo webpack.config.js

![](./imagens/webpack-config-js.png)

- `remotes`: mapeia o `mfe1` para o microfrontend compilado separadamente.

  > **NOTA** Embora especificar a URL da entrada remota dessa forma seja conveniente para o desenvolvimento, precisamos de uma abordagem mais dinâmica para produção.
  > O próximo artigo desta série fornece uma solução para isso: [Federação Dinâmica](https://www.angulararchitects.io/en/blog/dynamic-module-federation-with-angular/).

- `shared`: Define os pacotes npm a serem compartilhados entre o `shell` e os `microfrontends`
  > **NOTA** Para esta propriedade, a configuração gerada usa o método auxiliar `shareAll` que basicamente compartilha todas as dependências encontradas em seu arquivo package.json. Embora isso ajude a obter rapidamente uma configuração funcional, pode levar a muitas dependências compartilhadas. Uma seção posterior aqui aborda isso.
  - A combinação de: `singleton: true` e `strictVersion: true`
    faz com que o webpack emita um erro de tempo de execução quando o shell e o(s) microfrontend(s) precisam de versões incompetíveis diferentes (por exemplo, duas versões principais diferentes). Se pularmos strictVersion ou definirmos como false, o webpack emitirá apenas um aviso em tempo de execução. Mais informações sobre como lidar com incompatibilidades de versões podem ser encontradas em [outro artigo desta série](https://www.angulararchitects.io/blog/getting-out-of-version-mismatch-hell-with-module-federation/).
  - `requiredVersion: 'auto'` A configuração requiredVersion: 'auto'é um pouco extra fornecida pelo @angular-architects/module-federationplugin. Ele procura a versão usada no seu arquivo package.json. Isso evita vários problemas.
    - > **NOTA** A função auxiliar share usada nesta configuração gerada substitui o valor 'auto' pela versão encontrada em seu arquivo package.json.
