# Como funciona o mecanismo de reposta, como customiza-la e Status Code HTTP na resposta.

### Mercanismo de Resposta:

As respostas do que controller dá para o cliente é baseado no retorno do método do controller, se o retorno for um objeto ou um array ele é automaticamente serializado em JSON e enviado ao cliente, caso seja um dado simples como string, number, boolean... ele é enviado como um texto simples.

### Customizar resposta:

Nós podemos utilizar os seguintes decorators: **`@Res()`** ou **`@Response()`**, para definir um determinado parâmetro como um response object, ou seja um objeto que representará a nossa resposta no lado do servidor.

Esse response object ainda irá receber uma tipagem do TypeScript, essa tipagem será do tipo **`Response`** para que com ele possamos enviar respostas customizadas, exemplo: **`response.status(200).send(txt)`** ou **`response.status(200).json(obj)`**.

**########### Atenção existem dois tipos de Response ############**
**########### Atenção existem dois tipos de Response ############**
**########### Atenção existem dois tipos de Response ############**

O tipo de Response na qual estou falando para conseguirmos usar os métodos estáticos `status`, `send`, `json`... é o objeto do **EXPRESS** e para utiliza-lo precisamos **INSTALAR ELE**, **`npm install --save @types/express`**

**Isso não é sobre os decorators `@Res()` ou @Response() eles são sempre do próprio NestJS estou falando sobre o tipo do parâmetro, quanto aos decorators é recomendado usar o `@Res()` para não confudir o Response do express com o do NestJS**

Exemplo:

```typescript
import { Controller, Res } from "@nestjs/common";
import { Response } from "express";

@Controller("cats")
export class CatsController {
  @Get()
  findAll(@Res() response: Response) {
    return response
      .status(200)
      .header("Custom-Header1", "Value1")
      .heder("Custom-Header2", "Value2")
      .json({ action: "This action returns all cats" });
  }
}
```

Perceba que a maioria dos atributos de Response que usamos com o do Express, no NestJS são readonly: https://developer.mozilla.org/en-US/docs/Web/API/Response

Podemos personalizar o **HEADER** da resposta também com decorator da seguinte forma:

```typescript
import { Post, Header } from "@nestjs/common";

@Post()
@Header("Custom-Header1", "Value1")
@Header("Custom-Header2", "Value2")
create() {
  return 'This action adds a new cat';
}
```

### Status Code HTTP na resposta:

**'Também é possivel personalizar com o Response do Express com vimos na seção anterior'**

Os métodos do controller por padrão retornarão o Status Code HTTP 200 e isso é para todos os verbos HTTP, exceto para o Post que o seu padrão é 201, caso queira alterar isso temos que usar o decorator **`@HttpCode(numero)`**. Por exemplo:

```typescript
import { Controller, Get } from "@nestjs/common";
import { HttpCode } from "@nestjs/common/decorators/http";

@Controller("cats")
export class CatsController {
  @Get()
  @HttpCode(201)
  findAll(): string {
    return "This action returns all cats";
  }
}
```
