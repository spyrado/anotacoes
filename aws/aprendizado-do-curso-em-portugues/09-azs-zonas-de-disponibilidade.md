# AZs ou Zonas de Disponibilidades

![alt](./imgs/zonas%20de%20disponibilidade.png)

## O que é uma Zona de Disponibilidade?

- `AZs:` É um ou mais datacenters disponivel(eis) dentro de uma Região.
- São Paulo por exemplo tem 3 Zonas de Disponibilidades
  - a sua região é `sa-east-1`
  - e suas zonas de disponibilidades são:
    - `sa-east-1a`
    - `sa-east-1b`
    - `sa-east-1c`
  - para identificar isso dentro do `CloudShell` digite o seguinte comando:
    - aws ec2 describe-availability-zones --region <sua_regiao_aqui>
- É o `CONTEÚDO` que está `DENTRO` de uma `REGIÃO` (para saber o que é uma região leia o arquivo: `08-regioes.md`)
- as `AZs` possuem `links` entre elas para reduzir a `latência`

## Porque é importante as AZs?

- imagina o seguinte cenário, aconteceu um desastre na `AZ` `sa-east-1a`
- os seus serviços quando configurados em uma REGIÃO, eles fazem `backup` entre as `AZs` daquela região
- ou seja, se uma `AZ` `sa-east-1a` pegar fogo por conta de desastre natural.
- os seus serviços ainda vão continuar de pé por conta que eles também estão nas `AZs`
  - `sa-east-1b`
  - `sa-east-1c`

## Como elas são distribuidas?

- Geralmente elas ficam perto uma da outra para diminuir a latencia
- porem não tão perto para justamente evitar desastre natural.
- elas ficam em torno de 100km de distancia uma da outra não mais que isso.
- exemplo de desastre natural
  - queda de energia no local do az x
  - enundação que impeça que os funcionários vão para o AZ x
  - como eles estão a 50~100km um do outro é muito dificil que o mesmo desastre
    aconteça com o outro que está longe.