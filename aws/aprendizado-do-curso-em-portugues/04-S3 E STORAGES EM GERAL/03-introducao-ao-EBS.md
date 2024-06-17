# Introdução ao EBS ( Elastic Block Store )

> **IMPORTANTE:** O EBS `deve` estar na mesma `AZ` que o seu `EC2`

## O que é?

- É um disco que é vinculado geralmente a uma instancia EC2

1. posso ter mais de UM EC2 na mesma `AZ` compartilhando uma mesma EBS na mesma `AZ`?
   1. sim, antigamente isso não era possível, mas agora é.
   2. vc pode utilizar o multi-attach
   3. porem no momento os EC2 devem ser instancias de `NITRO`.
   4. caso não queira usar multi-attach ou seja não queira compartilhar o EBS, você pode usar...
      1. uma instancia EC2 p2.micro que vai funcionar também.