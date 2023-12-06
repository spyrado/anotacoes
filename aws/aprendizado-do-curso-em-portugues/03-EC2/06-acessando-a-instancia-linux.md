# Acessando a instancia (LINUX) EC2 que criamos

## Informações importantes

Linux é MUUUITO mais rapido que o windows, ele é mais `enxuto` e não requer muito recurso para funcionar,
então `se você não precisa de um windows como servidor`, recomendo rodar `linux`.

## Como acessar?

1. Selecione a instancia Linux em EC2 -> Instances -> escolha uma instancia linux que você criou.
2. Após selecionar clique em `Connect`
3. Clique em `EC2 Instance Connect`
4. Clique em `Connect`
5. Vai abrir uma nova aba com o console web da propria AWS acessando o servidor Linux
6. E pronto você vai ter acesso ao CLI do linux
7. digite sudo su para entrar como administrador no linux

## Erro ao conectar

> IMPORTANTE: Caso de ERRO ao tentar conectar siga esse passo a passo

Você deve mudar o ip de entrada lá no seu Security Group

1. Vá até EC2 -> Instances
2. Selecione a instancia que está dando erro
3. Clique na aba `Security`
4. Procure por `Security groups`
5. e clique no link logo abaixo do `Security groups`
6. Clique em `Edit Inbound rules`
7. clique em `Source`
8. escolha `Anywhere-IPv4` (SOMENTE PARA QUESTÕES DE ESTUDOS)
