# What is a server composed of? ( do que um servidor é composto? )

1 - <b>CPU</b> ( Que realiza todos os calculos necessários, processamentos e etc. ) <br>
2 - <b>RAM</b> ( onde conseguimos armazenar dados temporariamente ou para um futuro proximo ) <br>
3 - <b>Storage</b>: Data ( Onde armazenamos arquivos ) <br>
4 - <b>Database</b>: Store data in a structured way ( Banco de dados, onde armazenamos dados de uma maneira mais estruturada e escalável, podendo fazer consultas mais robustas e específicas. ) <br>
5 - <b>Network</b>: Routers, switch, DNS Server ( ???? ) <br>

- NETWORK: É um monte de cabos, roteadores e servidores conectados uns aos outros
- ROUTER: É um dispositivo específico que encaminhara os pacotes de dados entre a rede de computadores ( computer networks ), Eles sabem onde enviar seus pacotes na internet ( tipo os correios, eles pegam a carta (pacote de dados), e sabem para onde enviar essa carta).
- SWITCH: quando o router encaminha o pacote para seu destino, ele chega no switch, o switch pega
  o pacote e envia ele para o servidor ou cliente em sua rede.

Segue um exemplo:

![MarineGEO circle logo](imgs/IT_Terminology.png 'MarineGEO logo')

# Problems with traditional IT approach ( Problemas com abordagens tradicionais de TI )

Contexto:

- Antigamente, os servidores eram criados dentro de sua propria casa, voce ia até uma loja, comprava ele,
  e o colocava dentro de sua casa, o próprio GOOGLE começou na garagem de sua casa, porem conforme o tempo,
  seu negócio vai indo bem, e você precisa de mais servidores, ai você precisa sair da sua casa e comprar uma sala em um predio para poder ter mais servidores.

## Problemas com essas abordagens:

- Você vai precisar pagar um aluguel para alocar os seus servidores na sala.
- Vai precisar gastar com energia, refrigeração e manutenção ( alguem especializado em manutenção de data centers )
- Adicionar e remover hardwares do servidor tomam tempo ( voce precisa encomendar o hardware dps conectar eles ao seu datacenter )
- Dimencionamento limitado ( se amanhã você estiver 10x maior, você vai precisar de 10x mais servidores, mas pode não ter tempo ou espaço para fazer isso)
- Terá de contratar alguem que fique 24/7 monitorando a infraestrutura para caso de algo errado
- O que fazer em casos de desastes? Terremotos, corte de energia repentino, incendio..

## A pergunta é, podemos externalizar tudo isso?

- E a resposta é sim, e essa será a nuvem da AWS ( CLOUD )

# What is Cloud Computing?

- Computação em nuvem é a entrega sob demanda de poder de computação, armazenamento de banco de dados, aplicativo e outros recursos de TI.
- Por meio de uma plataforma de serviço em nuvem, você obterá um preço pré-pago, isso significa que você
  ... só vai pagar pelo que solicitou no momento em que solicitou, e a medida que estiver usando, quando terminar de usar, você não pagará mais.
- Então podemos provisionar exatamente o tipo e o tamanho certo de recursos de computação que você precise.
  ... ( você precisa de um grande servidor? nós temos. precisa de mais memória? nós temos)
- Você pode acessar vários recursos que precisa, e te-los instantaneamente ( quer mais 10 servidores? pronto está aqui, quer ampliar para 100? ok, está aqui. )
- Maneira simples de acessar os servidores, storages, banco de dados e um conjunto de serviços de aplicativo.
- Amazon Web Services, possui e mantem o hardware conectado a rede para esses serviços de aplicativos enquanto você provisiona e usa o que você precisa via web application

# Diferença entre CLOUDS

## Private Cloud

- Serviços de Cloud utilizamos por apenas uma organização, não é exposto ao publico
- Controle completo
- Segurança para aplicações sensiveis
- Atende a necessidades específicas do negócio

Exemplo de empresa que usa: rockspace

## Public Cloud

- Os Recursos de nuvem são propriedade e operados por um provedor de serviços em nuvem tercerizado e são
  ... fornecidos pela internet
- 6 vantagens de usar computação em nuvem

## Hybrid Cloud

- Manteremos alguns servidores no local ( On-premises ) e extenderemos alguns dos recursos de que precisamos para a nuvem
- Teremos controle sobre ativos confidenciais na nossa infraestrutura privada
- Mas teremos a flexibilidade e a economia de usar a nuvem publica

# The Five Characteristics of Cloud Computing

- On-demand self service ( autoatendimento sob demanda ):
  - Usuários podem provisionar recursos e usá-los sem a necessidade de interação com alguém da AWS
- Broad network access (Acesso a uma rede ampla):
  - Os recursos estarão disponiveis na rede, e podemos acessa-los de diversas plataformas.
- Multi-Tenancy and resource pooling (Multilocação e pool de recursos):
  - Isso significa que não apenas nós, mas outros clientes da AWS podem compartilhar a mesma infraestrutura e aplicativos, mantendo a segurança e a privacidade
  - E então esses multiplos clientes estão sendo atendidos com os mesmos recursos físicos
  - Isso significa que eu você e outros, vão compartilhar essa grande nuvem, o que nos da elasticidade
    ... e escalabilidade rapida.
- Rapid elasticy and scalability (Elasticidade rápida e escalabilidade):
  - Isso significa que podemos adquirir e descartar recursos de forma rapida e automática quando precisarmos
  - Isso significa que podemos de forma rápida escalar nossa aplicação on demand
- Measure Service (serviço de medida):
  - O Uso é medido, significa que o usuário paga exatamente pelo oq ele usou. ( essa é uma grande diferença do on-premises ( infraestrutura local privada ))

# Six Advantages of Cloud Computing

- Vamos negociar despesas de capital com despesas operacionais ou seja CAPEX por OPEX
  - Você paga sob demanda do serviço e não precisa possuir o hardware ( espaço fisico economizado )
  - Reduz seu custo total da propriedade dos hardwares(TCO) ( pq vc vai solicitar sob demanda na aws )
    ... Reduz o custo Operacional (OPEX) ( ou seja você não precisa mais que alguem fique dando...
    ... manutenção 24/7 pq vc n tem mais um data center e etc ).
- Beneficiar de enormes economias de escalas
  - O preço será reduzido, pois muitas pessoas estão utilizando a AWS então os preços serão reduzidos ao
    ... longo do tempo, porque a AWS será mais eficiente na execução devido à sua grande escala.
- Stop guessing capacity ( Pare de advinhar a capacidade que precisamos )
  - Antes precisavamos planejar e comprar servidores com antecedencias e esperar que atendecem a capacidade
    ... Hoje podemos solicitar sob demanda tudo isso com AWS, baseado no uso real da nossa aplicação
- Aumento na velocidade e a agilidade
  - uso porque tudo é sob demanda, então se precisarmos de x item, com poucos cliques teremos.
- Pare de gastar dinheiro executando e mantendo data centers.
- Seja global em minutos: com a infraestrutura da AWS digamos que, 5 pessoas podem criar a infra de um
  ... aplicativo em minutos.

# Problems solved by the Cloud

- <b>Flexibility</b>: Altere os tipos de recursos quando necessário.
- <b>Cost-Effectiveness ( Mais economicos )</b>: Pague conforme o uso, pelo que usar
- <b>Scalability</b>: Acomoda cargas maiores, tornando o hardware mais forte, ou adicionando nós adicionais
- <b>Elasticity</b>: Capacidade de expandir e reduzir quando necessário
- <b>Flexibility</b>: mude
