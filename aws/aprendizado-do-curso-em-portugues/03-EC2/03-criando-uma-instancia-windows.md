# Criando uma Instância Windows

## Como criar?

- Vá até o painel da aws procure por EC2
- Procure por "Launch instance"
- configurações principais:
  - de um nome a sua instancia
  - selecione qual instancia você quer criar ( NESSE CASO É WINDOWS )
  - clique em "create new key pair" ( vai gerar o login para acessar a maquina )
    - selecione para gerar em `.pem` que ai vc pode converter para outro tipo se quiser
  - para fins de estudos mude a porta de onde é autorizado o acesso a maquina
    - mude de qualquer porta (0.0.0.0/0) para My Ip
- e pronto feita as configurações principais, voce pode mandar criar/executar a instancia.
