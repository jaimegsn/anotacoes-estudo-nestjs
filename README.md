# Anotações sobre NestJS Framework

Anotações sobre o framework NestJS enquanto estudo sobre ele

## ROADMAP:

- [NestJS](./src/nestjs.md)
  - [NestJS, como instalar, como iniciar um projeto](./src/0_introdutorio/inicio-nestjs.md)
  - [Entendendo estrutura projeto](./src/0_introdutorio/entendendo-estrutura-projeto.md)
  - [Componentes](./src/0_introdutorio/componentes.md)
  - [Módulos](./src/0_introdutorio/modulos.md)
- [Camada de Controllers](./src/1_controllers/criando_controllers.md)
  - [Parametros que podemos receber de uma Request - Req Object, @Body, @Query, @Param, @Header, @Ip](./src/1_controllers/request_params.md)
  - [Mecanismo de reposta, como customiza-la e Status Code HTTP na resposta.](./src/1_controllers/response_statusCode.md)
  - [Personalizando mais ainda a rota dos controllers com 'Route Wildcard'](./src/1_controllers/route_wildcard.md)
  - [Redirection/Redirecionar para uma URL](./src/1_controllers/redirecionar.md)

## Mdbook

Antes certifique-se de instalar corretamente o mdBook seguindo o guia de instalação: [GUIA de Instalação](https://rust-lang.github.io/mdBook/guide/installation.html)

Para realizar o build das minhas anotações no formato de um livro você pode utilizar a ferramenta [mdbook](https://rust-lang.github.io/mdBook/). Assim fica mais fácil a leitura e você pode exportar até mesmo para o kindle.

Para isso, baixe o repositório e use um dos comandos abaixo:

```sh
$ mdbook build
```

Para subir o livro localmente use:

```sh
$ mdbook serve
```
