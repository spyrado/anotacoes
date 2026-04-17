# O que é um assistente de código?

- assitente de código utiliza Language Models para completar diferentes tasks
- Language Models precisam utilizar diferentes tipos de Tools para trabalhar em uma vasta variedades de tasks.
  - as Language Models utilizam Tools como:
    - ler arquivo
    - escrever arquivo
    - executar comandos
    - e tudo que não envolve apenas gerar algum texto.

## Exemplo de fluxo
```
  👨‍💻 Você
    ↓
  💬 Prompt ("analisa meu main.go")
    ↓
  🧠 LLM (decide o que fazer)
    ↓
  🧰 Precisa de dados externos?
    ↓
  🔌 MCP Client chama uma tool
    ↓
  📦 MCP Server (read_main_go)
    ↓
  📄 Retorna conteúdo do arquivo
    ↓
  🧠 LLM processa o código
    ↓
  💬 Resposta final pra você
```

  > Você → LLM → (preciso de dados?) → Tool → LLM → Resposta

## 🧠 O “pensamento” do LLM (simplificado)

Quando você manda:

“Analisa meu main.go”

O LLM raciocina mais ou menos assim:

1. O usuário quer analisar código  
2. Eu não tenho o código  
3. Existe uma tool chamada "read_main_go"  
4. Vou usar ela  

👉 Ele chama a tool  

Depois:

5. Recebi o código  
6. Agora consigo analisar  
7. Vou responder explicando + sugerindo melhorias  

## 🧩 Agora com “papéis” bem claros
  | Componente | Papel                                 |
| ---------- | ------------------------------------- |
| Você       | Faz a pergunta                        |
| LLM        | “Cérebro” (decide tudo)               |
| MCP Client | Ponte                                 |
| MCP Server | Expõe ferramentas                     |
| Tool       | Executa ação (ler arquivo, API, etc.) |
