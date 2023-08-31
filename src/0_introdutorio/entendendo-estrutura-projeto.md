# Entendendo a estrutura de um projeto NestJS:

- **node_modules/ (diretório)**:
  Este é o diretório onde conterá as nossas dependências que foram baixadas pelo gerenciador de pacotes(npm, npx, yarn), ele se baseia no arquivo package.json para saber quais dependências são necessárias

- **src/ (diretório)**:
  Este é o diretório principal onde você desenvolve o código-fonte da sua aplicação. Ele contém os módulos, controladores, serviços e outros componentes que compõem o aplicativo.

  - **`app.controller.ts`** é o controlador principal do módulo raiz (AppModule), responsável por lidar com as rotas HTTP do aplicativo.

  - **`app.module.ts`** é o próprio módulo raiz do aplicativo, que define os componentes principais e suas interações.

  - **`app.service.ts`** pode ser o serviço principal do módulo raiz, que contém a lógica de negócios compartilhada em todo o aplicativo.

  - **`main.ts`** é o ponto de entrada do aplicativo e geralmente chama o método **`bootstrap`** do NestFactory para iniciar o aplicativo usando o módulo raiz.

    Ele é análogo à classe Application no Spring Framework em Java.
    Além disso no **`main.ts`**, você pode definir configurações globais e lógica personalizada de inicialização, como configurações de portas, habilitação de CORS e assim por diante.

    ```typescript
    import { NestFactory } from "@nestjs/core"; // Importando o NestFactory
    import { AppModule } from "./app.module"; // Importando Módulo que será o Raiz

    // Criando método que será o ponto de partida da aplicação
    async function bootstrap() {
      const app = await NestFactory.create(AppModule); // Definição do Módulo Raiz
      await app.listen(3000); // Porta
    }
    bootstrap(); // Chamando método que é o ponto de partida da aplicação
    ```

    **NestFactory** : O NestFactory é responsável por criar uma instância da aplicação inteira com o comando **`create`**, incluindo todos os módulos, controladores, serviços e outros componentes que você tenha definido.

    **Módulo Raiz** : O módulo raiz, também conhecido como módulo principal, é o módulo fundamental em um aplicativo NestJS a partir do qual toda a aplicação é construída. Ele atua como o ponto de entrada principal e organiza os diferentes componentes e funcionalidades do aplicativo. O módulo raiz encapsula todos os outros módulos e serve como um contêiner

- **dist/ (diretório)**:
  Este diretório é gerado automaticamente quando você compila o código TypeScript para JavaScript de produção usando o comando **`nest build`**. Ele contém a versão compilada do seu aplicativo que é executada em produção.

- **.eslintrc.js**:
  Este é o arquivo de configuração do ESLint, que é uma ferramenta de linting para ajudar a manter o código consistente e livre de erros. Define as regras para formatação e estilo de código.

- **.prettierrc**:
  Arquivo de configuração do Prettier, uma ferramenta de formatação de código. Define como o código deve ser formatado para garantir consistência e legibilidade.

- **nest-cli.json**:
  Arquivo de configuração da CLI do NestJS. Permite personalizar as configurações da CLI ao executar comandos como **`nest generate`**.

- **package-lock.json**:
  Este arquivo é gerado automaticamente pelo npm e contém informações sobre as versões exatas das dependências instaladas. Ajuda a garantir que as mesmas versões das dependências sejam instaladas em diferentes máquinas.

- **package.json**:
  O arquivo package.json é um arquivo de configuração que contém informações sobre o projeto, como nome, versão, descrição, scripts de execução, dependências e outras informações relevantes. Ele também especifica as dependências necessárias para o projeto, mas geralmente apenas as versões mínimas permitidas das dependências. Ele trabalha em conjunto com o **package-lock.json** para gerenciar as dependências de um projeto.

- **tsconfig.json**:
  Arquivo de configuração do TypeScript que define as opções de compilação para o projeto. Define como o TypeScript deve ser compilado para JavaScript, incluindo configurações de módulos, tipo de alvo, caminhos de importação, etc.

- **tsconfig.build.json**:
  Um arquivo de configuração do TypeScript específico para a compilação de produção do projeto. Ele pode conter configurações diferentes das usadas no tsconfig.json, otimizando a compilação para produção.
