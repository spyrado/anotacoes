# [AWS] Cloud Front

## O que é um Cloud Front e para que serve?

*Video de referência:* https://www.youtube.com/watch?v=A7PCmh6-YKs


#### Significados
  1. CDN ( Rede de entregadores de serviços )
  2. Edge Location ( Ponto de presença )

### Como funciona fluxo do Cloud Front?

*Link de referência ( site oficial da AWS ):* https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowCloudFrontWorks.html

**Contexto:** Um usuário de São Paulo clica para assistir um video na aplicação porem esse video está armazenado no japão (em Tokyo por exemplo)

1. O usuário clica para ver o video, e a aplicação vai fazer o request desse vídeo para o edge location ( Ponto de presença ) mais proximo dele e se caso não encontrar nada ele vai buscar lá no servidor aonde foi "Hospedado" que no nosso cenário de **Contexto** é o Japão(Tokyo).



<!-- - Content Delivery Networks -> CDN
  - É uma "Rede de entregadores de serviços", a AWS coloca alguns Edge Locations em pontos especiais, que não são Data Centers, porem eles estão espalhados pelo mundo pra guardar conteúdo, com essa estratégia nós conseguimos diminuir a latencia e aumentar a velocidade.
- Baixa Latência e "Alta velocidade"
- Armazenamento temporário em Edge Locations
- Integra com outras soluções ( Shield,  WAF, S3... )
- http / https
- EX:
  - Slack
  - Netflix
  - S3 static website -->