# O que é storage?

<br>

- basicamente são HDs ou qualquer outro tipo de tecnologia de armazenamento, que vai guardar seus dados/arquivos/videos/documentos e etc.

<br>

## Quais storages existem na AWS?

<br>

> Cada tipo de armazenamento tem o seu objetivo.

1. `S3` - É o mais famoso e mais utilizado
2. `Glacier`
3. `EFS`
4. `Snowball`
5. `Cloud Front`
6. `Storage Gateway`
7. `EBS`
8. `Instance Store EC2`

> **Exemplo IMPORTANTE**: as vezes você precisa de armazenar arquivos que devem ser acessados por 2 servidores ao mesmo tempo
>
> - você deve estar pensando, é só utilizar o `S3`
> - porem se você utilizar o `EFS` ele já é projetado para esse tipo de trabalho e você pode até economizar com essa escolha.

<br>
