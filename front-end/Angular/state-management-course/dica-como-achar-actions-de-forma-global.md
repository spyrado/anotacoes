## Como achar Actions de forma global?

Para encontrar actions de forma global, siga os passos abaixo:

**Abra o arquivo `app.component.ts`**.

**Injete o `store` no construtor**:
```typescript
constructor(private store: Store<AppState>) {}
```

**Execute o comando no método `ngOnInit`**:
```typescript
ngOnInit() {
this.store.subscribe(console.log);
}
```

### Resultado

Ao fazer isso, o `console.log` no navegador indicará de onde a action foi disparada, não apenas de dentro do `app.component`.

#### Exemplo:

Quando você clica em "login" na tela, mesmo com o `console.log` no `app.component`, o console do navegador irá mostrar de onde o evento foi disparado. No caso, ele indicará que foi do `login.component.ts`. Isso facilita a identificação de onde as actions estão sendo disparadas.