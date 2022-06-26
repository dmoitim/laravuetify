<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 2000 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the Laravel [Patreon page](https://patreon.com/taylorotwell).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Cubet Techno Labs](https://cubettech.com)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[Many](https://www.many.co.uk)**
- **[Webdock, Fast VPS Hosting](https://www.webdock.io/en)**
- **[DevSquad](https://devsquad.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[OP.GG](https://op.gg)**
- **[WebReinvent](https://webreinvent.com/?utm_source=laravel&utm_medium=github&utm_campaign=patreon-sponsors)**
- **[Lendio](https://lendio.com)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

## Passo a passo para criação do projeto

1- Com o composer instalado, executar o comando abaixo para criar o projeto, em nosso exemplo ele será chamado de "laravuetify"
```
composer create-project laravel/laravel laravuetify
```

2- Após a finalização do processo, instalar o vuejs e o vuetify e suas dependências, como requisitos de desenvolvimento:
```
npm i vue@^2.6.14 vue-template-compiler@^2.6.14 vue-loader@^15.9.8 vuetify@^2.6.6 --save-dev
```

3- Abrir o arquivo laravuetify\webpack.mix.js e adicione a linhe ".vue()", deixando o arquivo conforme abaixo:
```
mix.js('resources/js/app.js', 'public/js')
    .vue()
    .postCss('resources/css/app.css', 'public/css', [
        //
    ]);
```

4- Executar o comando NPM abaixo e aguardar a instalação das dependências e compilação dos arquivos:
```
npm run watch
```

5- Abrir o arquivo laravuetify\resources\js\app.js e 
adicionar no final do arquivo as linhas para realizar as importações necessárias e a inicialização do vue, deixando o arquivo conforme abaixo:
```
import './bootstrap';
import Vue from 'vue';
import Vuetify from 'vuetify';
import 'vuetify/dist/vuetify.min.css';

Vue.use(Vuetify)

Vue.component('welcome-component', require('./components/WelcomeComponent.vue').default)

const app = new Vue({
    vuetify: new Vuetify(),
    el: '#app',
});
```

7- Criar o arquivo WelcomeComponent.vue dentro do diretório laravuetify\resources\js\components, conforme abaixo:
```
<template>
    <div>
        <h1>Welcome Component</h1>
        <v-btn color="primary" class="my-2">Button</v-btn>
        <v-alert dismissible type="success">Vuetify installed successfully!</v-alert>
    </div>
</template>

<script>
    export default {
        
    }
</script>
```

8- Alterar o arquivo welcome.blade.php de laravuetify\resources\views, conforme abaixo:
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Laravel 9 With Vue JS 2 and Vuetify</title>
    <link href="https://fonts.googleapis.com/css?family=Roboto:100,300,400,500,700,900" rel="stylesheet">
    <link href="https://cdn.jsdelivr.net/npm/@mdi/font@6.x/css/materialdesignicons.min.css" rel="stylesheet">
    <link rel="stylesheet" href="{{asset('css/app.css')}}">
</head>
<body>
    <div id="app">
        <v-app>
            <v-main>
                <v-container>
                    <welcome-component></welcome-component>
                </v-container>
            </v-main>
        </v-app>
    </div>

    <script src="{{asset('js/app.js')}}"></script>
</body>
</html>
```

9- Feito isso, executar o comando abaixo e carregar o endereço http://127.0.0.1:8000 no navegador:
```
php artisan serve
```

Créditos: https://www.youtube.com/watch?v=JColnqkcvWI