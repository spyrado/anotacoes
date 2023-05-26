MAPA MENTAL SOBRE ESSE ESTUDO LINK: https://whimsical.com/aws-51e7H496tunrdg2SsXu1MB

<br>

> **IMPORTANTE:** NÃO UTILIZE o usuário root, use-o apenas para criar o seu usuário e use o seu usuário
> na aws, ele não deve ser utilizado e nem compartilhado.

<br>

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
  fornecidos pela internet
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
    e escalabilidade rapida.
- Rapid elasticy and scalability (Elasticidade rápida e escalabilidade):
  - Isso significa que podemos adquirir e descartar recursos de forma rapida e automática quando precisarmos
  - Isso significa que podemos de forma rápida escalar nossa aplicação on demand
- Measure Service (serviço de medida):
  - O Uso é medido, significa que o usuário paga exatamente pelo oq ele usou. ( essa é uma grande diferença do on-premises ( infraestrutura local privada ))

# Six Advantages of Cloud Computing

- Vamos negociar despesas de capital com despesas operacionais ou seja CAPEX por OPEX
  - Você paga sob demanda do serviço e não precisa possuir o hardware ( espaço fisico economizado )
  - Reduz seu custo total da propriedade dos hardwares(TCO) ( pq vc vai solicitar sob demanda na aws )
    Reduz o custo Operacional (OPEX) ( ou seja você não precisa mais que alguem fique dando...
    manutenção 24/7 pq vc n tem mais um data center e etc ).
- Beneficiar de enormes economias de escalas
  - O preço será reduzido, pois muitas pessoas estão utilizando a AWS então os preços serão reduzidos ao
    longo do tempo, porque a AWS será mais eficiente na execução devido à sua grande escala.
- Stop guessing capacity ( Pare de advinhar a capacidade que precisamos )
  - Antes precisavamos planejar e comprar servidores com antecedencias e esperar que atendecem a capacidade
    Hoje podemos solicitar sob demanda tudo isso com AWS, baseado no uso real da nossa aplicação
- Aumento na velocidade e a agilidade
  - Isso porque tudo é sob demanda, então se precisarmos de x itens, com poucos cliques teremos.
- Pare de gastar dinheiro executando e mantendo data centers.
- Seja global em minutos: com a infraestrutura da AWS digamos que, 5 pessoas podem criar a infra de um
  aplicativo em minutos.

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

# AWS Cloud Use Cases ( Nuvem AWS Casos de Uso )

- AWS permite que você contrua aplicações sofisticadas e escalaveis.
- Aplicavél a um conjunto diversificado de insdustrias.
- O Caso de Uso inclui:
  - Empresarial TI
  - Backup & Storage
  - Big Data analytics
  - Website Hosting
  - BackEnd for Mobile & Social Apps
  - Entire Game Server on the cloud

# AWS GLOBAL Infrastructure

- AWS Regions
- AWS Availability Zones
- AWS Data Centers
- AWS Edge Locations / Point of Presence

conseguimos ver tudo isso aqui: https://infrastructure.aws/

# AWS Regions

- Aws tem Regions pelo mundo todo
- Os nomes dessas regiões podem ser: us-east-1, eu-west-3
- Uma Região é um Cluster de datacenters ( dois ou mais computadores para que estes trabalhem de maneira conjunta no intuito de processar uma tarefa. Estas máquinas dividem entre si as atividades de processamento e executam este trabalho de maneira simultânea. )
- A maioria dos serviços AWS tem escopo regional

- Conformidade com a governança de dados e requisitos legais: os dados nunca saem de uma região sem
  sua permissão explícita.

## Como escolher uma região na AWS?

Bom isso depende, tem alguns pontos:

- **Compliance ( Conformidade ):** As vezes os governos querem que os dados sejam locais para o pais em que você está
  implantando a sua aplicação. Por exemplo, na França, os dados na França podem ter que permanecer
  na França e, portanto, você deve lançar seu pedido na região francesa.

- **Proximity ( Proximidade ):** Aqui a o conceito de latência, se o seu público ALVO fica na américa do sul e você contrata uma região da Austrália, seu publico alvo terá muito atraso ao acessar a sua aplicação

- **Available Services ( Disponibilidade de Serviços ):** IMPORTANTE: Nem toda region tem todos os serviços, então é muito importante que antes da escolha da sua região, você deve verificar se ela possui
  o serviço que você precisa.

- **Pricing ( Preços ):** Os preços dos serviços variam de região para região, mas isso é transparente na pagina de serviços mostra os preços deles e você consegue compará-los.
  Exemplo: vamos supor que sua aplicação é uma aplicação de upload e download de fotos, nesse caso
  o que importa é o custo sobre o download de fotos, teriamos que fazer uma análise de qual
  região tem o menor custo de "DATA Out" por transação, que isso é o que iria ter mais impácto no nosso
  negócio.

# AWS Availability Zones (AZ)

- Cada região tem muitas zonas de disponibilidade ( Availability Zones ), normalmente cada região possui
  no mínimo 3 e no máximo 6 "zonas de disponibilidade" ( Availability Zones ), mas normalmente é 3, exemplo:
  - ap-southeast-2a
  - ap-southeast-2b
  - ap-southeast-2c
- Cada Zona de Disponibilidade (AZ) pode ter um ou mais data centers com energia, rede, e conectividade, exemplo:
  - ap-southeast-2a pode ter 1 2 3 poderia ser 4 datacenters, nós não sabemos realmente, a AWS não nos informa isso
  - Mas o que sabemos é que essas zonas de disponibilidade (az) estão separadas umas das outras, para que fiquem,
    isoladas de desastres, se um der ruim temos mais 2 funcionando (por exemplo)

# AWS Points of Presence ( Edge Locations )

- A Amazon possui 216 pontos de presença ( 205 pontos de presença 11 cache regional ) em 84 cidades
  de 42 países.
- E isso será muito útil quando entregarmos conteúdo aos usuários finais com a menor latência possível.

# Tour of the AWS Console

- AWS tem serviços globais
  - Identity and Access Management (IAM) ( Gerenciamento de identidade e acesso )
  - Route 53 ( DNS service )
  - CloudFront ( Content Delivery Network ) ( Rede de entrega de conteúdo )
  - WAF ( Web Application Firewall )
- Mas a maioria dos serviços AWS são por escopo de região
  - Amazon EC2 ( Infrastructure as a Service )
  - Elastic Beanstalk ( Platform as a Service )
  - Lambda ( Function as a Service )
  - Rekognition ( Software as a Service )

# Shared Responsibility Model Diagram

- Tudo o que você usa na nuvem, independentemente da forma que você configura é de sua inteira responsabilidade, e isso inclui segurança, seus dados, seu sistema operacional, sua configuração de rede
  firewall e etc.

- E a AWS é responsável pela segurança da NUVEM, então toda a infraestrutura, todo o hardware, todo o software, toda a segurança interna própria eles são responsáveis.

- Segue o DIAGRAMA para exemplificar (https://aws.amazon.com/compliance/shared-responsibility-model/):
  ![aleatorio](imgs/shared_responsibility_model.png 'aleatorio')

# AWS Acceptable Use Policy ( Política de uso aceitável da AWS )

- LINK: https://aws.amazon.com/aup/

- Você não pode usar, ou facilitar ou permitir que outros usem os Produtos ou o Site da AWS:
  - por qualquer atividade ilegal ou fraudulenta;
  - para violar os direitos de outras pessoas;
  - para ameaçar, incitar, promover ou incentivar ativamente violência, terrorismo ou outros danos graves;
  - por qualquer conteúdo ou atividade que promova a exploração ou abuso sexual infantil;
  - para violar a segurança, integridade ou disponibilidade de qualquer usuário, rede, computador ou sistema de comunicações, aplicação de software ou dispositivo de rede ou computação;
  - para distribuir, publicar, enviar ou facilitar o envio de e-mails em massa não solicitados ou outras mensagens, promoções, publicidade ou solicitações (ou “spam”).

# [SERVICES] IAM ( Identity and Access Management )

> **IMPORTANTE:** NÃO UTILIZE o usuário root, use-o apenas para criar o seu usuário e use o seu usuário
> na aws, ele não deve ser utilizado e nem compartilhado.

<br/>

## [SERVICES] IAM Users and Groups

- IAM Significa Identidade e Gerenciamento de acessos
- Root Account criado pro padrão quando se cria uma conta na aws, ele não deve ser utilizado, e nem compartilhado.
- Users (Usuarios) são pessoas dentro da sua organização e podem ser agrupados juntos se fizer sentido.
- Groups (Grupos) apenas contem usuários e não outros grupos.
- User (Usuário) sem um grupo, não é uma boa prática, mas é possível fazer isso.
- Um usuário pode pertencer a mais de um grupo.

## [SERVICES] IAM Permissoes

- Usuários ou Grupos podem receber documentos JSON, chamados de políticas ( Policies ).
- Essas políticas definem as permissões dos usuários.
- Na AWS você sempre deve aplicar o Princípio do Privilégio Mínimo (Least Privilege Principle),
  não de mais permissões do que o usuário precise, de apenas o que ele precisa.
- Segue exemplo:

![aleatorio](imgs/iam_permissions.png 'aleatorio')

<br>

## [SERVICES] IAM Tags

- Podemos utilizar tags ao criar um usuário, elas são uteis para por exemplo, falar que aquele
  usuário é do departamento de engenharia, ai na tag ficaria KEY: Departamento VALUE: Engenharia

<br>

## [SERVICES] IAM Policies

<br>

### [SERVICES] IAM inheritance ( Herança )

- As políticas na aws podem ser herdadas, como herança mesmo em objetos por exemplo
- Se eu tenho um grupo chamado developer com determinadas politicas, e eu colocar
  um usuário dentro desse grupo ele vai herdar as políticas desse grupo
- Se eu tiver um grupo chamado Audit e colocar esse mesmo usuário do grupo developer dentro do audit,
  o usuário agora tem as politicas tanto de developers quanto de audit
- Também podemos ter políticas isoladas para usuários sem grupo, chamamos essas políticas de "inline policy" são políticas que são dedicadas para usuários sem grupo.,
- Segue exemplo:
  ![aleatorio](imgs/politicas_de_heranca.png 'aleatorio')

### [SERVICES] IAM Structure ( estrutura JSON )

```json
{
  "Version": "2012-10-17",
  "Id": "S3-Account-Permissions", // pode dar o nome que quiser apenas para identificar a policie
  "Statement": [
    {
       especificado aqui em mybucket
    }
  ]
}
```

### Significado de cada propriedade do JSON ( policie / política )

- **Version** - Linguagem da versão da política, sempre coloque "2012-10-17" [REQUIRED]
- **Id** - Um identificador para a política ( policie ) [OPTIONAL]
- **Statement** - Uma ou Mais declarações individuais ( Individual Statements )  [REQUIRED]
- **Sid** - Um identificador para o Statement [OPCIONAL]
- **Effect** - Se o Statement Permite ou Nega o acesso (Allow,Deny) [REQUIRED]
- **Principal** - Consiste em qual Conta/Usuário/Função(Role) a política deve ser aplicada  [??]
- **Action** - É a lista de chamadas da API que serão negadas ou permitidas com base no **Effect** [??]
- **Resource** - É uma lista de recursos aos quais as ações serão aplicadas [??]
- **Condition** - De acordo com essa condição ele vai verificar se esse Statement configurado, deve ou 
  não ser aplicado [OPTIONAL] ( não está no objeto acima, mas se possivel dps coloque no exemplo )

<br>

# [SERVICES] IAM Mecanismos de defesa

## [SERVICES] IAM Password Policy

- senhas fortes - mais segurança para a sua conta
- Na AWS voce pode definir uma "política de senha"( Password Policy )
  - definir um tamanho mínimo de senha
  - Requerer caracteres específicos:
    - incluindo letras com Upper Case
    - letras com Lower Case
    - numeros
    - Caracteres Especiais, exemplo: &;%, e etc
  - Voce pode PERMITIR que o usuário mude o seu próprio password
  - Ou pode requerer que os usuários mudem o password de tempo em tempo ( password expiration )
  - Pode também previnir que os usuários reutilizem senhas anteriores na hora da mudança da senha. ( Prevent password re-use )

<br>

## [SERVICES] IAM MFA - Multi Factor Authentication

- Usuários podem ter acesso a sua conta e podem mudar as configurações ou deletar recursos com sua
  conta da AWS
- Você quer proteger seu usuário root e os seus IAM Users.
- Para isso você deve utilizar o MFA, o MFA basicamente faz a combinação da senha que você sabe
  mais um dispositivo físico seu.
- Principal benefício do MFA:
  - mesmo que um usuário perca a sua senha porque foi roubado ou hackeado a conta não será comprometida
    porque o hacker também vai precisar obter o dispositivo fisico do usuário para ter acesso ao token gerado no MFA
- Segue um exemplo:
![aleatorio](imgs/mfa-example.png 'aleatorio')

<br>

## [SERVICES] IAM MFA Devices options in AWS

- [Virtual_MFA_Device] Google Authenticator [ mobile only ]
- [Virtual_MFA_Device] Authy [ multi-device ] ( funciona tanto pc quanto celular )
- Os Virtual MFA Device Suportam multiplos tokens em um unico dispositivo.
- [Universal 2nd Factor] (U2F) Security Key [ YubiKey ] é um dispositivo fisico tipo o que você tem para crypto,
  vc pode cadastrar multiplos usuários e n precisa decorar 50 mil codigos, vc só usa o seu dedo para autenticar e fim.
  fora que por ser um dispositivo fisico ele te trais mais segunrança ainda.
- [Hardware Key Fob MFA Device] esse vc gera a senha apertando um botão.
- [Hardware Key Fob MFA Device for AWS GovCloud (US)] e temos um Key Fob específico, se vc estiver usando a NUVEM do governo nos EUA,
  provavelmente vc vai precisar de um desse para acessar.

![aleatorio](imgs/mfa_devices_options.png 'aleatorio')

## How can users access AWS?

- To access AWS, you have three options:
  - AWS Management Console ( protected by password + MFA )
  - AWS Command Line Interface ( CLI ): protected by access keys
  - AWS Software Developer Kit ( SDK ) - for code: protected by access keys
  - As chaves são geradas pelo o console da AWS ( AWS Console )
  - as chaves (access keys) são gerenciadas pelos proprios usuários.
  - As chaves são secretas, assim como um password, não compartilhe as chaves.
  - Então trate de pensar que a sua "Access Key ID" (username) e sua "Secret Access Key"(password) são como seu
    usuário e senha.

## What's the AWS CLI?

- Uma ferramenta que habilita você a interagir com serviços da AWS usando linhas de comando em um Git Bash por exemplo
- Tem acesso direto as API Publicas da AWS
- Você pode desenvolver scripts para gerenciar os seus recursos e automatizar algumas tarefas
- Ela é open source, segue link: https://github.com/aws/aws-cli
- É uma alternativa ao inves de usar o AWS Management Console
- todas as linhas de comando começam com aws, exemplo:
  aws s3 cp myfile.txt s3://ccp-mybucket/myfile.txt

## What's the AWS SDK?

- AWS Software Development Kit ( AWS SDK )
- SDK é uma lib específica em uma linguagem específica.
- A AWS possui diversos sdk's um para cada tipo de linguagem de programação
- SDK Habilita você a acessar e gerenciar serviços da AWS programaticamente ( via linha de código )
- SDK Sempre ficará dentro do seu código, exemplo para fazer o multipartupload via Node.js:
  VocÊ precisa instalar e importar o SDK de Node, para poder utilizar o serviço de multipart da AWS
- A AWS suporta SDK para:
  - Javascript, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++
  - Mobile SDK's ( Android, IOS ... )
  - IoT Device SDK's ( Embedded C, Arduino... )
- Exemplo: AWS CLI foi construído no SDK da AWS para Python

# How Can I Install AWS CLI?

- Follow these steps
- 1º digite no google "aws cli install on windows"
- 2º Clique em um link que tenha uma url da AWS
- 3º Clique no link que baixa um .msi para a sua maquina
- 4º de next next next até instalar o CLI
- 5º abra o git bash e digite aws --version
- 6º se ele retornou a versão do cli da aws está tudo configurado

# How Can I Use AWS CLI

- Primeiro de tudo para conseguir utilizar o CLI da AWS, precisamos gerar as nossas Chaves de Acesso (Access Key)
- Entre no serviço "IAM"
- Clique em "Usuários(Users)"
- Clique no usuário que deseja gerar a Chave de Acesso procure por "Credenciais de segurança"(
security credentials)
- Procure por "Chaves de acesso"(access keys)
- Clique em criar chaves de acesso
- Selecione a opção "Command Line Interface (CLI)"
- Clique em Proximo
- Clique em Criar chave de acesso
- Voce vai receber duas chaves, "Chave de acesso" e "Chave de acesso secreta", copie as duas e guarde em um lugar seguro
- Vá ate o git bash e configure sua CLI com as chaves
- Digite no git bash: "aws configure"
- Ele vai te pedir o "AWS Access Key ID" (Chave de acesso) ai vc copia e cola a chave de acesso
- Ele vai te pedir o "AWS Secret Access Key" (Chave de acesso secreta) ai vc copia e cola a Chave de acesso secreta
- Ele vai pedir uma região "a mais proxima de você" no meu caso é: "sa-east-1"
- Ele vai pedir um "Default output format" ai vc apenas aperta ENTER
- E pronto sua AWS CLI está configurada