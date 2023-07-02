# Como criar uma aplicação React?

Com a ultima versão:

> npx react-native@latest init AwesomeProject

Ou com uma versão específica 

> npx react-native@X.XX.X init AwesomeProject --version X.XX.X 

# Como iniciar sua aplicação Android?

1. > npx react-native start
2. > npx react-native run-android

# Como limpar o cache do seu aplicativo?

> npm start -- --reset-cache

<br>

# StyleSheet

## Como tipar um StyleSheet.create?

???

<br>

# Fonts

- Como adicionar fonts?
  - primeiro vá vá até o google fonts, escolha uma e baixe ela, vai vir em zip e dentro vai ter todos os
    arquivos que vamos precisar os famosos .ttf e etc.
  - crie um diretorio para as fontes: PROJECT-DIRECTORY/assets/fonts
  - jogue as fontes lá dentro
  - crie um arquivo de configuração para o projeto ( caso não tenha ainda ) chamado **react-native.config.js** e adicione o seguinte código dentro dele:
  ```
  module.exports = {
    project: {
        ios:{},
        android:{}
    },
    assets:['./assets/fonts/'],
  }
  ```
  - feito isso rode o comando 
    - `npx react-native link` ( para React Native V0.68 ou menor )
    - `npx react-native-asset` ( para versões >= V0.69 )
  - e pronto esse plugin vai refletir as fontes onde deve.
  - agora é só estilizar, como por exemplo: 
  `fontFamily: 'Roboto'`
- Como remover fontes adicionadas com esse plugin?

# Como usar icones no React Native?

- instale essa lib `npm i react-native-vector-icons` e leia a doc: https://www.npmjs.com/package/react-native-vector-icons

- SIGA ESSE TUTORIAL DO CHAT GPT 

Com um plus, além de vc instalar oq ele pede vc vai precisar rodar esse comando para
typar os icones `@types/react-native-vector-icons`

A e também ele não fala, mas vc deve entrar em node_modules/react-native-vector-icons/Fonts
escolher a fonte que deseja exemplo: `MaterialCommunityIcons.ttf` copiar ela e colar dentro de `assets/fonts` e link depois utilizando `npx react-native-asset` que ele vai distribuir certinho para android / ios
e o resto o  tutorial explica

One of the most popular libraries for adding custom fonts to a React Native project is react-native-vector-icons. While it is primarily known for providing a wide range of icon sets, it also allows you to use custom fonts in your React Native applications.

To add custom fonts using react-native-vector-icons, you can follow these steps:

1. Install the library using npm or Yarn:

```shell
npm install react-native-vector-icons --save
```
or
```shell
yarn add react-native-vector-icons
```

2. Link the library to your project:

```shell
react-native link react-native-vector-icons
```

Note: For React Native versions 0.60 and above, the library should be automatically linked, so you can skip this step.

3. Add the font files to your project's assets. Place the font files (typically with .ttf or .otf extensions) in the `assets/fonts` directory of your React Native project. Create the directory if it doesn't exist.

4. Register the fonts in your `react-native.config.js` file. If you don't have this file in your project's root directory, create it and add the following code:

```javascript
module.exports = {
  project: {
    ios: {},
    android: {},
  },
  assets: ['./assets/fonts/'],
};
```

5. Import and use the custom font in your React Native components. You can import the font using the name of the font file (without the extension). For example:

```javascript
import Icon from 'react-native-vector-icons/FontAwesome';

// Example usage
const MyCustomIcon = () => (
  <Icon name="rocket" size={30} color="#900" />
);
```

Make sure to replace `FontAwesome` with the appropriate icon set you want to use.

By following these steps, you can easily add and use custom fonts in your React Native application using the `react-native-vector-icons` library.

# Como usar Navegação

- **Vamos utilizar o React Navigation**
- link da lib: https://reactnavigation.org/docs/getting-started
- rode os seguintes comandos
-  `npm install @react-navigation/native`
-  `npm install react-native-screens react-native-safe-area-context`
-  Vá até o seu App.tsx e envolta todas as tags existentes dentro de `NavigationContainer`
como nesse exemplo:
```
function App(): JSX.Element {
  return (
    <>
      <NavigationContainer>
        <Login></Login>
      </NavigationContainer>
    </>
  );
}
```
-  depois instale `npm install @react-navigation/native-stack`
-  após isso podemos incluir as stacks de rotas para nossa aplicação monitorar
-  vamos chamar o metodo `createNativeStackNavigator` que nos retorna um objeto
contendo duas propriedades `Screen` e `Navigator` os dois são componentes do **React**,
usados para configurar a navegação
- `Navigador` -> deve conter elementos `Screen` como filho para definir as configurações de rota.
- `Screen` -> contem 2 parametros `name` que presetenda o nome da rota e `component` que representa
qual componente ele vai carregar quando chamar essa rota.