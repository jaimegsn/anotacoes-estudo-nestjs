# Todos os parametros que podemos receber de uma Request - Req Object, @Body, @Query, @Param, @Header, @Ip

Em NestJS nós temos o Request Object que é um objeto que representa a requisição que foi enviada pelo cliente, e com esse objeto é possível acessar os atributos de uma requisição como cabeçalho, corpo, url...

Podemos utilizar esse objeto como parâmetro no método de algum controller para pegar os dados de alguma requisição que foi enviada para aquele determinado operador(método do controller), para isso basta utilizarmos o decorator **`@Req()`** ou **`@Request()`** no parâmetro de algum método do controller. Por exemplo:

```typescript
import { Controller, Get, Request } from "@nestjs/common";

@Controller("/teste")
export class ControllerUsuario {
  constructor() {}

  @Get()
  getHello(@Request() request: Request): object {
    const headers = request.headers;
    const body = request.body;
    const url = request.url;
    return headers;
  }
}
```

Porém se quisermos temos alguns decorators que nos auxiliam em capturar alguns atributos da requisição sem precisar fazer algo muito manual com o Request Body, são os seguintes decorators:

- **`@Param(key?: string)`**: Permite acessar os parâmetros de rota (URL) passados na solicitação. Opcionalmente, você pode especificar uma chave para acessar um parâmetro específico.

  ```typescript
  import { Controller, Get, Param } from "@nestjs/common";

  @Controller("/users")
  export class UsersController {
    @Get("/:id")
    getUserById(@Param("id") userId: string) {
      return `User ID: ${userId}`;
    }
  }
  ```

  Com isso nós acessamos essa operação com a seguinte URL: **"/users/5"**

- **`@Body(key?: string)`**: Permite acessar o corpo da solicitação. Pode ser usado para extrair dados do corpo da solicitação, um exemplo de utilização comum é mandar um objeto no corpo da requisição para cadastro, então podemos capturar esses dados com **`@Body()`** e manipular na nossa aplicação.

  ```typescript
  import { Controller, Post, Body } from "@nestjs/common";

  @Controller("/users")
  export class UsersController {
    @Post()
    createUser(@Body() user: CreateUserDto) {
      // 'user' é um objeto preenchido com os dados do corpo da requisição
      // ...
    }
  }
  ```

- **`@Query(key?: string)`**: Permite acessar os parâmetros de consulta (query params) passados na URL. Pode ser usado para obter os valores dos parâmetros de consulta, opcionalmente fornecendo uma chave para acessar um parâmetro específico.

  ```typescript
  import { Controller, Get, Query } from "@nestjs/common";

  @Controller("/users")
  export class UsersController {
    @Get()
    getUsersByRole(@Query("role") role: string) {
      return `Users with role: ${role}`;
    }
  }
  ```

  **Query params podem ser usados para evitar duplicação de URL e a criação exceciva URL's**, Query params são opcionais, enquanto que Path Params ou Url Params são obrigatórios ser passados, se usassemos sempre parâmetros na URL, teriamos que criar várias URL's se tornando algo caótico. Passamos Query params na url dessa forma: **"/users?role=admin"**, nesse exemplo estamos passando o valor admin para o parâmetro role

- **`@Headers(name?: string)`**: Permite acessar os cabeçalhos da solicitação HTTP. Pode ser usado para obter o valor de um cabeçalho específico, opcionalmente fornecendo um nome de cabeçalho.

  ```typescript
  import { Controller, Get, Headers } from "@nestjs/common";

  @Controller("/users")
  export class UsersController {
    @Get()
    getUserAgent(@Headers("user-agent") userAgent: string) {
      return `User Agent: ${userAgent}`;
    }
  }
  ```

- **`@Ip()`**: Fornece o endereço IP do cliente que fez a solicitação.

  ```typescript
  import { Controller, Get, Ip } from "@nestjs/common";

  @Controller("/users")
  export class UsersController {
    @Get()
    getClientIp(@Ip() clientIp: string) {
      return `Client IP: ${clientIp}`;
    }
  }
  ```
