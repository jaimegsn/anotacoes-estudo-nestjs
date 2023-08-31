# Controllers

Controllers são responsáveis por receber requisições do cliente e encaminhar ela para um determinado processamento e depois retornar uma resposta adequada para o cliente.

Para criarmos um controller precisamos criar uma classe controller no módulo, por exemplo: **`usuario.controller.ts`**, cada controller terá sua URL de acesso personalizada e ela pode ter vários métodos dentro dela para realizar operações diferentes, esses métodos podem também personalizar mais ainda a URL.

Iremos utilizar um decorator **`@Controller()`** na classe, para indicar que aquela classe é um controller, depois nos métodos iremos utilizar decorators para indicar o verbo HTTP daquela operação (**`@Get()`**, **`@Put()`**, **`@Post()`**, **`@Delete()`**). Por exemplo:

```typescript
import { Controller, Get } from "@nestjs/common";

@Controller()
export class ControllerUsuario {
  constructor() {}

  @Get()
  getHello(): string {
    return "Testando meu Controller personalizado";
  }
}
```

Esse controller está devolvendo uma String para o cliente.

A personalização da URL acontece da seguinte maneira:

```typescript
@Controller("/usuario")
export class ControllerUsuario {
  constructor() {}

  @Get()
  getHello(): string {
    return "Testando meu Controller personalizado";
  }
}
```

Com isso para acessarmos as operação **`getHello`** desse controller temos que acessar a seguinte URL: **"/usuario"**

Podemos ainda personalizar por operação, assim:

```typescript
@Controller("/usuario")
export class ControllerUsuario {
  constructor() {}

  @Get()
  getHello("/hello"): string {
    return "Testando meu Controller personalizado";
  }
}
```

Com isso para acessarmos as operação **`getHello`** desse controller temos que acessar a seguinte URL: **"/usuario/hello"**

**Operações/URL Duplicadas** temos que ter cuidado para não criarmos operações duplicadas se não ocasionará em algum erro, as operações se diferem umas das outras de acordo com as seguintes características: url e método(verbo) http, se esses dois fatores forem iguais teremos erro.

### Registrando o Controller na classe do Módulo

Após termos seguido todos os passos anteriormente e ter tido cuidado para não criar operações duplicadas, podemos acessar o nosso controller ? **Ainda Não**.

Precisamos registra-lo na classe do módulo da classe no array controllers. Por exemplo:

```typescript
import { Module } from "@nestjs/common";
import { ControllerUsuario } from "./usuario.controller";

@Module({
  controllers: [ControllerUsuario], // Registrando o controller no módulo
})
export class AppModule {}
```

Agora sim podemos acessar
