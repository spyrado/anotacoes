# ECS - Elastic Container Service

## O que é?

### ECS Cluster

- `Cluster:` é um agrupamento lógico de tarefas ou serviços.
- `Task:` dentro da aws é a mesma coisa que `container`
- `Resgistry:` dentro da aws é a mesma coisa que `image`
  - esses registros são `GERENCIADOS` por um `serviço da amazon` chamado `Elastic Conainer Registry` ou `ECR`

### ECS Service

- Ele que gerencia os containers, vc pode reduzir ou aumentar a quantidade de containers, quais as caracteristicas de cada container e etc.

### ECS Container Instance

- é onde ficam as configurações do container
- a aws chama de `TASK DEFINITION`

### ECS EC2 CLUSTER vs ECS FARGATE

- ECS EC2 CLUSTER

  - Você é o responsável por gerenciar, colocar auto escale, configurar cluster e etc.

- ECS FARGATE
  - ele é serverless isso significa que a aws que gerencia pra voce.
