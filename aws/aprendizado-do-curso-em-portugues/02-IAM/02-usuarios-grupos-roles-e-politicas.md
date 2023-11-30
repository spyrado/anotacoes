# Usuários, Grupos, Roles e Políticas

## Usuários

Conseguimos criar usuários na AWS, só de eu criar um usuário ele já vai ter acesso ao `CONSOLE`, `CLI` e `API`.<br>

`POREM` esse usuário não vai ter `PERMISSOES`, se você acessar com esse usuário na aws você não vai conseguir fazer NADA, não vai conseguir CRIAR/EDITAR/DELETAR e etc.

`Poque isso ocorre?` pq todo usuário que você acaba de criar ele vem com `ZERO` de `privilégio`.

## Grupos

Grupos são criados para organizar os usuários, exemplo:

`[GRUPO DESENVOLVEDORES]` dei permissões pra que todos dentro desse grupo acessem o `S3` e o `RDS`.

`[GRUPO INFRA]` dei permissões pra que todos dentro desse grupo acessem `EC2`.

ou seja criei dois grupos com permissões específicas para cada area e quem estiver dentro de determinado grupo,
vai ter determinada permissão.

## Roles

Elas podem ser aplicadas a `serviços da AWS` exemplo:

Eu quero que uma `VM` ou `EC2` possa acessar uma instancia no `Bucket S3`, fazendo isso eu não preciso LOGAR com o meu usuário, aquele serviço já tem permissão para acessar o `Bucket S3`

## Policy

São nada mais nada menos que `REGRAS` aonde podemos `permitir` ou `bloquear` o `acesso` de `GRUPOS` ou `USUÁRIOS`

EXEMPLO:

Posso criar uma `Policy` que:

- Permite o acesso ao S3
- Só pode fazer UPLOAD
- em um Bucket específico

A quem eu der essa `Policy` ( tanto usuário em específico, como um grupo ) eles atenderam a essa regra.
