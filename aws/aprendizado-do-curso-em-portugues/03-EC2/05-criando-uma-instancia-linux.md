# Criando uma Instância Linux

## Como criar?

- Vá até o painel da aws procure por EC2
- Procure por "Launch instance"
- configurações principais:
  - de um nome a sua instancia
  - selecione qual instancia você quer criar ( NESSE CASO É Amazon Linux )
  - clique em `"create new key pair"` OU selecione um key pair já existente caso você já tenha um.
    - `[create new key pair]` selecione para gerar em `.pem` que ai vc pode converter para outro tipo se quiser
  - `[SECURITY GROUP]` para fins de estudos mude a porta de onde é autorizado o acesso a maquina
    - mude de qualquer porta (0.0.0.0/0) para My Ip
- e pronto feita as configurações principais, voce pode mandar criar/executar a instancia.
