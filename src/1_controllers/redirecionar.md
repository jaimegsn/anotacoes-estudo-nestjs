# Redirection/Redirecionar para uma URL

O redirecionamento de resposta é uma técnica usada para enviar o cliente para uma URL diferente em vez de retornar o conteúdo regular. Isso é frequentemente usado para redirecionar o usuário após a conclusão de uma ação, como após o login ou o envio de um formulário.

No NestJS, você pode realizar redirecionamentos usando o decorator **`@Redirect()`** de `@nestjs/common` ou diretamente chamando o método **`.redirect()` do Response Object** específico da biblioteca (como o Express).

Por exemplo:

```typescript
@Get()
@Redirect('https://nestjs.com', 301)
redirectToNestJS(): void {
  // Este método não precisa retornar nada
}
```

A operação redireciona para a URL **"https://nestjs.com"** com o **código de status HTTP 301 (Moved Permanently)**. Se você não fornecer o código de status, o valor padrão será 302 (Found).

Se você quiser **determinar dinamicamente a URL de redirecionamento** e/ou o código de status com base em certas condições, você pode retornar um objeto com as propriedades **"url"** e **"statusCode"** a partir do método do manipulador de rota:

```typescript
@Get('docs')
@Redirect('https://docs.nestjs.com', 302)
getDocs(@Query('version') version): any {
  if (version && version === '5') {
    return { url: 'https://docs.nestjs.com/v5/', statusCode: 301 };
  }
}
```
