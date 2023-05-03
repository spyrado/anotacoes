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

![aleatorio](imgs/IT_Terminology.png 'aleatorio')

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
  <br>... só vai pagar pelo que solicitou no momento em que solicitou, e a medida que estiver usando, quando terminar de usar, você não pagará mais.
- Então podemos provisionar exatamente o tipo e o tamanho certo de recursos de computação que você precise.
  <br>... ( você precisa de um grande servidor? nós temos. precisa de mais memória? nós temos)
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
  <br>... fornecidos pela internet
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
    <br>... e escalabilidade rapida.
- Rapid elasticy and scalability (Elasticidade rápida e escalabilidade):
  - Isso significa que podemos adquirir e descartar recursos de forma rapida e automática quando precisarmos
  - Isso significa que podemos de forma rápida escalar nossa aplicação on demand
- Measure Service (serviço de medida):
  - O Uso é medido, significa que o usuário paga exatamente pelo oq ele usou. ( essa é uma grande diferença do on-premises ( infraestrutura local privada ))

# Six Advantages of Cloud Computing

- Vamos negociar despesas de capital com despesas operacionais ou seja CAPEX por OPEX
  - Você paga sob demanda do serviço e não precisa possuir o hardware ( espaço fisico economizado )
  - Reduz seu custo total da propriedade dos hardwares(TCO) ( pq vc vai solicitar sob demanda na aws )
    <br>... Reduz o custo Operacional (OPEX) ( ou seja você não precisa mais que alguem fique dando...
    <br>... manutenção 24/7 pq vc n tem mais um data center e etc ).
- Beneficiar de enormes economias de escalas
  - O preço será reduzido, pois muitas pessoas estão utilizando a AWS então os preços serão reduzidos ao
    <br>... longo do tempo, porque a AWS será mais eficiente na execução devido à sua grande escala.
- Stop guessing capacity ( Pare de advinhar a capacidade que precisamos )
  - Antes precisavamos planejar e comprar servidores com antecedencias e esperar que atendecem a capacidade
    <br>... Hoje podemos solicitar sob demanda tudo isso com AWS, baseado no uso real da nossa aplicação
- Aumento na velocidade e a agilidade
  - uso porque tudo é sob demanda, então se precisarmos de x item, com poucos cliques teremos.
- Pare de gastar dinheiro executando e mantendo data centers.
- Seja global em minutos: com a infraestrutura da AWS digamos que, 5 pessoas podem criar a infra de um
  <br>... aplicativo em minutos.

# Problems solved by the Cloud

- <b>Flexibility</b>: Altere os tipos de recursos quando necessário.
- <b>Cost-Effectiveness ( Mais economicos )</b>: Pague conforme o uso, pelo que usar
- <b>Scalability</b>: Acomoda cargas maiores, tornando o hardware mais forte, ou adicionando nós adicionais
- <b>Elasticity</b>: Capacidade de expandir e reduzir quando necessário
- <b>High-availability and fault-tolerance (Alta disponibilidade e tolerância a falhas)</b>: Porque não utilizamos um único data center a aws tem uma FROTA de datacenters espalhados pelo mundo todo
- <b>Agility</b>: Podemos desenvolver, testar e lançar aplicativos rapidamente

# Types of Cloud Computing

- **[IaaS]** Infrastructure as a Service ( IaaS ) ( Infraestrutura como Serviço )
  - O que é?
    - É como se você contratasse servidores dentro da computação em nuvem mas você contrata tudo isso como serviço, segue um exemplo:
      - Rede
      - Roteamento
      - Armazenamento
      - Memória
      - Processamento (CPU) e etc..
  - fornece blocos de construção para a TI em nuvem.
  - Com esse IaaS vamos fornecer rede, computadores, data storage space em sua forma bruta,
  - Nivel muito alto de flexibilidade: usando esses negócios básicos que criam Legos, teremos esse
    ... nivel muito alto de flexibilidade
  - Podemos entender facilmente como podemos migrar da IT local e tradicional ( on premises ), para a nuvem.
- **[PaaS]** Platform as a Service ( PaaS ) ( Plataforma como Serviço )
  - Elimina a necessidade da sua organização gerenciar a infraestrutura
  - Concentre-se na implantação e no gerenciamento de seus aplicativos.
  - Um bom exemplo de um PaaS de antigamente, era quando você subia seu site em alguma hospedagem
    de site, tipo uma hostinger da vida, você só precisava subir seu codigo escolher o banco,
    e fim n precisava se preucupar se tava rodando em windows, linux, quanto de memória estava puxando e etc.
  - Você tem um pouco menos de liberdade ( o IaaS é o que mais da liberdade ), porem você não precisa,
    fazer tudo na mão ( como é o caso do IaaS ), então no PaaS, vc pode escolher seu banco configurar via tela e fim, no IaaS vc precisaria INSTALAR o banco, configurar tudo na mão etc.
- **[SaaS]** Software as a Service ( SaaS ) ( Software como Serviço )

  - O que é?
    - Ele define soluções entregues por meio da nuvem, como por exemplo:
      - Dropbox
      - GoogleDrive
      - SalesForce
      - Netflix
      - Google Analytics
      - Paypal
  - Vantagens
    - Redução de custo para empresas e usuários ( como é em nuvem, n precisamos de local fisico e etc )
    - Facilidade de acesso as informações ( por estar na internet e não em um local fisico )
    - Benefícios de atualizações disponíveis, por estar online, todos os usuários sempre receberam,
      ... as mais recentes atualizações.

- E Aqui vai um exemplo em imagem:

![aleatorio](imgs/exemplo_de_tipos_de_cloud_computing.png 'aleatorio')

# Example of Cloud Computing Types

- Infrastructure as a Service ( IaaS ):
  - Amazon EC2 ( on AWS )
  - GCP, Azure, Rackspace, Digital Ocean, Linode
- Platform as a Service ( PaaS )
  - Elastic Beanstalk ( on AWS )
  - Heroku, Google App Engine ( GCP ), Windows Azure ( Microsoft )
- Software as a Service ( SaaS )
  - Many AWS Services ( ex: Rekognition for Machine Learning )
  - Google Apps ( Gmail ), Dropbox, Zoom

# Pricing of the Cloud - Quick Overview

- AWS tem 3 fundamentos de precificação, seguindo o modelo de precificação de pagamento conforme o uso ( pay as you go )
  - Computador: pagar pelo tempo de computação
  - Armazenamento: Paga pelo tamanho de dados armazenados na nuvem.
  - Data Transfer OUT of the Cloud: Vamos pagar quando os dados sairem da CLOUD
  - Data Transfer IN is free: Todo dado recebido na CLOUD não é cobrado.
  - Isso resolve o caro problema do TI Tradicional
  - Segue exemplo em imagem:
    ![aleatorio](imgs/pricing_of_the_cloud.png 'aleatorio')