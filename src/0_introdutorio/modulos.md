# Módulos NestJS

Módulos no NestJS são contêineres organizacionais que agrupam e encapsulam um conjunto relacionado de componentes, em outras palavras é uma unidade que contém componentes relacionados como controladores, serviços, repositórios...

### Analógia com Spring:

Móddulos em NestJS são similares a pacotes no Spring Framework com Java. Ambos são unidades organizacionais que agrupam componentes relacionados e fornecem uma maneira de organizar, modularizar e reutilizar funcionalidades em um aplicativo.

**Com a ressalva de que cada módulo em NestJS é representado por uma classe e um diretório ao invés de apenas um diretório como acontece no Java**, essa classe define e configura os componentes associados a esse módulo, como controladores, serviços, provedores e outros. Essa classe é geralmente nomeada de acordo com o nome do módulo seguido por "Module" (por exemplo, `usuario.module.ts`)

### Classe do modulo raiz():

```typescript
import { Module } from "@nestjs/common";
import { AppController } from "./app.controller";
import { AppService } from "./app.service";
import { UsuarioModule } from "./usuario/usuario.module";

@Module({
  imports: [UsuarioModule],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```

- `@Module`: O decorador **`@Module`** é usado para definir e configurar um módulo em NestJS. Ele aceita várias opções, como imports, controllers e providers, que você pode configurar para organizar e definir os componentes do módulo.

- imports: é usado para importar outros módulos no módulo atual, esses módulos importados podem ser módulos personalizados definidos por você ou módulos de bibliotecas externas. Importar um módulo significa que você pode usar os componentes (controladores, serviços e outros provedores) definidos nesse módulo no contexto do módulo atual.
  **Após importamos um módulo externo, nós precisamos importar apenas o componente externo em algum componente do módulo atual para utilizar**

- controllers: é usado para listar os controladores que fazem parte do módulo atual.

- providers: é usado para listar os provedores (geralmente serviços) que fazem parte do módulo atual. Provedores são componentes que têm lógica de negócios, interagem com bancos de dados, chamam APIs externas, entre outras tarefas.

- **`export class AppModule{}`**: raramente escreveremos código aqui, pois é uma convenção para permitir que esse módulo seja importado e utilizado por outros módulos.

- **Fazer todas essas listagem de imports,controllers,providers é importante para a injeção de dependência que o NestJS faz por debaixo dos panos, além de melhorar a clareza do código**

**Todo modulo terá uma classe nesses moldes, e é encorajado pelo NestJS que tenhamos um módulo para cada Funcionalidade da aplicação**

### Criando um novo módulo:

- Abra o terminal na raiz do seu projeto NestJS.

- Use o comando da CLI do NestJS para gerar um novo módulo. O comando segue o formato **`nest generate module nome-do-modulo`**.

Isso criará um diretório dentro do diretório **src** com o nome do módulo.

**Ou podemos fazer o processo manualmente, criando um novo diretorio para o módulo, a classe dele e importa-lo ao módulo principal**
