# Conectando nosso MFE ao SHELL

1. Para tornar possível carregar o FlightsModuleno shell, também precisamos expô-lo através da configuração do webpack do remoto.
2. copie o código abaixo e cole ele dentro de `workspace/projects/mfe1/webpack.config.js`,

   ```
   const {
     shareAll,
     withModuleFederationPlugin,
   } = require("@angular-architects/module-federation/webpack");

   module.exports = withModuleFederationPlugin({
     name: "mfe1",

     exposes: {
       "./Module": "./projects/mfe1/src/app/flights/flights.module.ts",
     },

     shared: {
       ...shareAll({
         singleton: true,
         strictVersion: true,
         requiredVersion: "auto",
       }),
     },
   });
   ```

3. A configuração mostrada aqui expõe FlightsModule o nome público Module. A seção shared aponta para as bibliotecas compartilhadas com o shell.
