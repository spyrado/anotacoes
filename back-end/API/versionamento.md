# Versionamento de API

É importante versionar as API's, para garantir que quando lance uma v2 a v1 continue funcionando.

## Tipos de Versionamentos

- Versionamento por URL
  - subdominio
    - Especificamos a versão no subdominio
    - Exemplo: https://v1-youhost/api/xpto
  - path (mais utilizada)
    - especificamos a versão após a BASE_URL: https://youhost/api/xpto
    - Exemplo: https://youhost/api/xpto/v1
  - query param
    - Exemplo: https://youhost/api/xpto?version=1.0
  - header
    - Exemplo: `Accept:` application/vnd.your_host.v1+json 