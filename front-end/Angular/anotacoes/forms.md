## ControlContainer

Utilizamos o ControlContainer geralmente via DI ( Injeção de Dependencia ) para pegar o formulário do componente PAI

> POREM É muito importante sabermos que o ControlContainer ele apenas pega uma instancia do formulário pai, ou seja ele vai subindo na arvore do dom até achar o primeiro formGroup.

> Mas... se a demanda for ter um form independente o ControlContainer não vai servir para fazer um form
> reutilizavel e independente, pois ele DEPENDE da declaração de um formGroup no componente pai.
> Nesse caso podemos utilizar outra estratégia, que pode ser tanto ControlValueAcessor (demorado)
> como uma solução bem melhor que seria utilizando @ViewChild

exemplo:

app-pai.component.ts

```
  <app-pai [formGroup]="form">
    <app-filho></app-filho>
  </app-pai>
```

app-filho.component.ts

```
  contructor(private controlContainer: ControlContainer){}

  ngOnInit() {
    console.log(this.controlContainer); // Aqui vai conter todo o conteudo da variavel form do app-pai
  }
```

## NgControl

Classe injetável do Angular responsável por recuperar a instância de um `FormControl`, `FormControlName` ou `NgModel`

`Diferença entre NgControl` e `ControlContainer`, as vezes vc só precisa fazer uma manipulação em um control específico e não no formulário interiro
