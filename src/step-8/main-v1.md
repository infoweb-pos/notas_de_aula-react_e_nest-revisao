# API - main.ts - passo 8 - versão 1

arquivo `./src/main.ts`
```ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  app.enableCors();
  await app.listen(3000);
}
bootstrap();

```

- Adicionado a linha 6 com `app.enableCors();` habilitando o CORS na API
