# Conexao com o banco

- Para configurar a conexao com o banco vá até appsettings.json

```
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;DataBase=NOME_DATA_BASE;Uid=NOME_DO_SEU_USUARIO_NO_BANCO;Pwd=SUA_SENHA"
  }
}
```

# Provedor

Precisamos utilizar um provedor para fazer a conversa entre o .NET e o Banco De Dados, atualmente o mais famoso é o Pomelo.EntityFrameworkCore.MySql

para instalar basta digitar 

dotnet add package Pomelo.EntityFrameworkCore.MySql