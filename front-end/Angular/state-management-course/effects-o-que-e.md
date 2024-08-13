# O que é Effects e como utiliza-los?

podemos utiliza-los como `side effects` ou efeito colateral, sempre que uma action for disparada um efeito colateral pode acontecer, por exemplo:

ao fazer um login, e guardarmos o usuário em memória, podemos além disso colocar ele em um local storage porem colocar em local storage é um `side effect` efeito colateral de ter feito o login, ou seja toda hora que a action de login rodar, vamos o nosso effect vai rodar também e armazenar nosso usuário no local storage.

Em resumo: `side effect` é algo extra que queremos fazer em nosso aplicativo após uma ação ter sido dispachada e processada.

> **IMPORTANTE** primeiro roda o seu reducer modificando o estado da aplicação, e depois roda a sua effect em caso de side effect