# site-tracking

Online em [https://rastrearpacote.com/](https://rastrearpacote.com/).

Site para rastrear os pacotes do correios. Utiliza [rest-tracking](https://github.com/gabrielboliveira/rest-tracking) para obter os resultados, pois a API SOAP do Correios não permite _cors_. Também utiliza o pacote [tracking-correios](https://github.com/gabrielboliveira/tracking-correios) para validar os códigos de rastreio.

Desenvolvido com [Vue.js](https://vuejs.org/) e [Bulma](http://bulma.io/), iniciado com o template [webpack-simple](https://github.com/vuejs-templates/webpack-simple).

## Passos

```sh
# instalar
$ npm install

# desenvolvimento
$ npm run dev

# compilar para produção
$ npm run build
```

## Licença

[MIT](LICENSE.md)
