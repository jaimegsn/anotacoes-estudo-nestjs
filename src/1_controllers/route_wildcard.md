# Personalizando mais ainda a rota dos controllers com 'Route Wildcard'

No NestJS, você pode personalizar as rotas dos controladores de forma muito flexível, permitindo que você atenda a diferentes URLs e padrões de URL. Existem caracteres especiais que você pode usar para criar rotas mais dinâmicas e poderosas. Vamos olhar elas:

- **Asterisco(\*)**: ele indica que naquele espaço onde está ocupando pode exister 0 ou até muitos caracteres na url. Por exemplo:

  ```typescript
  @Get('ab*cd')
  findAll() {
    return 'This route uses a wildcard';
  }
  ```

  Logo a rota poderia ser todas essas opções: **'abcd'**, **'ab_cd'**, **'abecd'**

- **Ponto de Interrogação (?)**: O ponto de interrogação indica que o caractere anterior ou grupo de caracteres é opcional. Isso permite criar rotas que correspondem a URLs com ou sem um determinado trecho. Por exemplo:

  ```typescript
    @Get('users?')
    findUsers() {
        return 'This route matches "users" and "user"';
    }
  ```

  Nesse exemplo, a rota corresponderá a ambas as URLs **"/users"** e **"/user"**.

- **Hífen (-)**: O hífen é um caractere comum que você pode usar diretamente em suas rotas. Não possui um significado especial em termos de roteamento, então você pode usá-lo para criar URLs com hífens. Por exemplo:

  ```typescript
    @Get('custom-route')
    customRoute() {
        return 'This route matches "/custom-route"';
    }
  ```

- **Ponto (.)**: O ponto é outro caractere comum que você pode usar diretamente em suas rotas. Ele também não possui um significado especial em termos de roteamento. Você pode usá-lo para criar URLs com pontos. Por exemplo:

  ```typescript
    @Get('version.1')
    getVersion() {
        return 'This route matches "/version.1"';
    }
  ```

- **Parênteses ()**: Os parênteses são usados para criar grupos de caracteres em suas rotas. Isso é útil quando você deseja aplicar modificadores, como o ponto de interrogação ou o mais, a um grupo específico. Por exemplo:

  ```typescript
    @Get('user(s)?')
    findUser() {
        return 'This route matches "user" and "users"';
    }
  ```

  Nesse exemplo, a rota corresponderá a ambas as URLs **"/user"** e **"/users"**.
