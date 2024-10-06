para descriptografar o certificado basta rodar o comando:

> openssl x509 -in server.crt -text


para descriptografar a chave(key) basta rodar o comando:

> openssl rsa -in server.key -text -noout