Use no `pre-commit`:

```sh
#!/usr/bin/env sh
 
CYAN='\033[0;36m'
NC='\033[0m'
echo -e "[${CYAN}Husky${NC}] pre-commit sendo executado..."

echo -e "[${CYAN}Prettier${NC}] padronizando com prettier..."
npx pretty-quick --staged --pattern "*/.*(js|jsx|ts|html)"

# DESATIVANDO Eslint até resolvendo o problema de quebra do .html com angular-template
# echo -e "[${CYAN}ESLint${NC}] ajustando com eslint..."
# npx eslint --max-warnings=0 --fix $(git diff --cached --name-only --diff-filter=ACM | grep -E '\.(js|jsx|ts|tsx|html)$') && git add $(git diff --cached --name-only --diff-filter=ACM | grep -E '\.(js|jsx|ts|tsx|html)$')

echo -e "[${CYAN}Husky${NC}] pre-commit finalizado."
 
```

Use no `pre-push`:

```sh
#!/usr/bin/env sh
 
CYAN='\033[0;36m'
NC='\033[0m'
echo -e "[${CYAN}Husky${NC}] pre-push sendo executado..."

echo -e "[${CYAN}Lint${NC}] validando código..."
npm run lint
echo -e "[${CYAN}Lint${NC}] validação finalizada..."

echo -e "[${CYAN}Husky${NC}] pre-push finalizado."

```

crie uma pasta chamada `.vscode` na raiz do projeto e adicione o arquivo `.settings.json` com esse conteudo:

```json
{
  "editor.tabSize": 2,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll": "explicit"
  },
  "[javascript]": {
    "prettier.singleQuote": true
  }
}
```

instale essas dependencias no `package.json`:

```json
"angular-eslint": "^20.1.1",
"eslint": "^9.29.0",
"typescript-eslint": "8.34.1",
"husky": "^9.1.7",
"lint-staged": "^15.4.3",
"prettier": "^3.5.3",
"pretty-quick": "^4.1.1"
```
 