# Revisão de conceitos básicos sobre aplicação web com React e API Rest com Nest

## Informações gerais

- **Público alvo**: alunos da disciplina de POS (Programação Orientada a Serviços) do curso de Infoweb (Técnico Integrado em Informática para Internet) no CNAT-IFRN (Instituto Federal de Educação, Ciência e Tecnologia do Rio Grande do Norte - Campus Natal-Central)
- **Professor**: [L A Minora](https://github.com/leonardo-minora/)
- **Repositórios**
  - **aplicação web** [github](https://github.com/infoweb-pos/2023-revisao-web/)
  - **api rest** [github](https://github.com/infoweb-pos/2023-revisao-api/)

## Sumário
1. Criar os projetos iniciais
2. Configurar projeto app-api
3. Adicionar rota `/tarefas` e suas sub-rotas (criar e recuperar todas)
4. Configurar projeto app-web
5. 

# 1. Criar os projetos iniciais
1. Criar diretório da aplicação
2. Criar aplicação web react + typescript usando vite
   - Lembrar de responder
     - quando perguntar se deseja instalar/baixar a nova versão **Ok to proceed? (y)** responder com **y**
     - quando perguntar o nome do projeto a ser criado **Project name:** responder com **app-web**
     - quando perguntar qual a biblioteca de UI vai usar **Select a framework:** responder com **React**
     - quando perguntar qual a linguagem vai usar **Select a variant:** responder com **TypeScript**
3. Criar api rest nest
   - Lembrar de responder
     - quando perguntar se deseja instalar/baixar a nova versão **Ok to proceed? (y)** responder com **y**
     - quando perguntar qual gerenciador de bibliotecas vai usar **? Which package manager would you ❤️  to use?** responder com **npm**

```console
$ mkdir app-revisao && cd $_

$ npm create vite@latest

Need to install the following packages:
create-vite@4.4.1
Ok to proceed? (y) y
✔ Project name: … app-web
✔ Select a framework: › React
✔ Select a variant: › TypeScript

Scaffolding project in /home/minora/minora/app/app-web...

Done. Now run:

  cd app-web
  npm install
  npm run dev

$ code app-web

$ npx @nestjs/cli new app-api
Need to install the following packages:
@nestjs/cli@10.1.16
Ok to proceed? (y) y
⚡  We will scaffold your app in a few seconds..

? Which package manager would you ❤️  to use? npm
CREATE app-api/.eslintrc.js (663 bytes)
CREATE app-api/.prettierrc (51 bytes)
CREATE app-api/README.md (3347 bytes)
CREATE app-api/nest-cli.json (171 bytes)
CREATE app-api/package.json (1952 bytes)
CREATE app-api/tsconfig.build.json (97 bytes)
CREATE app-api/tsconfig.json (546 bytes)
CREATE app-api/src/app.controller.spec.ts (617 bytes)
CREATE app-api/src/app.controller.ts (274 bytes)
CREATE app-api/src/app.module.ts (249 bytes)
CREATE app-api/src/app.service.ts (142 bytes)
CREATE app-api/src/main.ts (208 bytes)
CREATE app-api/test/app.e2e-spec.ts (630 bytes)
CREATE app-api/test/jest-e2e.json (183 bytes)

✔ Installation in progress... ☕

🚀  Successfully created project app-api
👉  Get started with the following commands:

$ cd app-api
$ npm run start

                                         
                          Thanks for installing Nest 🙏
                 Please consider donating to our open collective
                        to help us maintain this package.
                                         
                                         
               🍷  Donate: https://opencollective.com/nest

$ code app-api

```



# 2. Configurar projeto app-api
1. Adicionar bibliotecas ao projeto app-api
2. Criar o arquivo `./src/ormconfig.ts`
3. Configurar o repositório SQLite para memória modificando o arquivo `./src/ormconfig.ts`
4. Modificar o arquivo `./src/app.module.ts` para usar a configuração de acesso ao repositório.
5. Configurar rota raiz `/` editando os arquivos `./src/app.controller.ts` e `./src/app.service.ts`.
6. Executar projeto API em modo desenvolvedor.

```console
$ npm add @nestjs/typeorm typeorm sqlite3
npm WARN deprecated @npmcli/move-file@1.1.2: This functionality has been moved to @npmcli/fs

added 782 packages, and audited 783 packages in 2m

103 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

```

arquivo `./src/ormconfig.ts`
```ts
import { DataSourceOptions } from 'typeorm';

export const config: DataSourceOptions = {
  type: 'sqlite',
  database: ':memory:',
  dropSchema: true,
  synchronize: true,
  entities: [__dirname + '/**/entities/*.entity{.ts,.js}'],
};

```

arquivo `./src/app.module.ts`
```ts
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';

import { config } from './ormconfig';

import { AppController } from './app.controller';
import { AppService } from './app.service';

@Module({
  imports: [TypeOrmModule.forRoot(config)],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}

```

arquivos `./src/app.controller.ts`
```ts
import { Controller, Get, Res, HttpStatus } from '@nestjs/common';
import { AppService } from './app.service';
import { Response } from 'express';

@Controller()
export class AppController {
  constructor(private readonly appService: AppService) {}

  @Get()
  getHello(@Res() response: Response) {
    response.status(HttpStatus.OK).json(this.appService.getHello());
  }
}

```

arquivos `./src/app.service.ts`
```ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class AppService {
  getHello() {
    return {
      estado: 'ok',
      mensagem: 'API Online',
      dados: 'API exemplo da disciplina de POS',
    };
  }
}

```

```console
$ npm run start:dev
[06:05:25] Starting compilation in watch mode...

[06:05:28] Found 0 errors. Watching for file changes.

[Nest] 50578  - 04/09/2023, 06:05:29     LOG [NestFactory] Starting Nest application...
[Nest] 50578  - 04/09/2023, 06:05:29     LOG [InstanceLoader] TypeOrmModule dependencies initialized +92ms
[Nest] 50578  - 04/09/2023, 06:05:29     LOG [InstanceLoader] AppModule dependencies initialized +1ms
[Nest] 50578  - 04/09/2023, 06:05:29     LOG [InstanceLoader] TypeOrmCoreModule dependencies initialized +25ms
[Nest] 50578  - 04/09/2023, 06:05:29     LOG [RoutesResolver] AppController {/}: +13ms
[Nest] 50578  - 04/09/2023, 06:05:29     LOG [RouterExplorer] Mapped {/, GET} route +3ms
[Nest] 50578  - 04/09/2023, 06:05:29     LOG [NestApplication] Nest application successfully started +4ms

```


# 3. Adicionar rota `/tarefas` e suas sub-rotas  (criar e recuperar todas)
1. Abrir um novo terminal.
2. Criar rota `/tarefas` para um CRUD Rest API.
   - Lembrar de responder
     - Para a pergunta **? What transport layer do you use?** responder **REST API**.
     - Para a pergunta **? Would you like to generate CRUD entry points?** responder **Yes**.
3. Verificar no log de desenvolvedor se as rotas `/tarefas` foram adicionadas.
4. Configurar o entidade e dto de criação de `tarefas` editando os arquivos `./src/tarefas/entities/tarefa.entity.ts` e `./src/tarefas/dto/create-tarefa.dto.ts`.
5. Configurar (repositório e entidade) o módulo de `tarefas` editando o arquivo `./src/tarefas/tarefas.module.ts`.
6. Configurar (repositório e entidade) o serviço de `tarefas` editando o arquivo (importações e adicionando construtor) `./src/tarefas/tarefas.service.ts`.
7. Adicionar ao serviço `tarefas` o criar nova tarefa e recuperar todas as tarefas - `./src/tarefas/tarefas.service.ts`.
8. Modificar o controlador de rotas `tarefas` (`/tarefas`) para retornar a tarefa nova (`POST`) e todas as tarefas (`GET`).

```console
$ npx nest generate resource tarefas --no-spec
? What transport layer do you use? REST API
? Would you like to generate CRUD entry points? Yes
CREATE src/tarefas/tarefas.controller.ts (936 bytes)
CREATE src/tarefas/tarefas.module.ts (262 bytes)
CREATE src/tarefas/tarefas.service.ts (637 bytes)
CREATE src/tarefas/dto/create-tarefa.dto.ts (32 bytes)
CREATE src/tarefas/dto/update-tarefa.dto.ts (177 bytes)
CREATE src/tarefas/entities/tarefa.entity.ts (23 bytes)
UPDATE package.json (2070 bytes)
UPDATE src/app.module.ts (440 bytes)
✔ Packages installed successfully.

$ 

```

```console
...
[06:12:02] Found 0 errors. Watching for file changes.

[Nest] 51213  - 04/09/2023, 06:12:03     LOG [NestFactory] Starting Nest application...
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [InstanceLoader] TypeOrmModule dependencies initialized +79ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [InstanceLoader] AppModule dependencies initialized +0ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [InstanceLoader] TarefasModule dependencies initialized +0ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [InstanceLoader] TypeOrmCoreModule dependencies initialized +30ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [RoutesResolver] AppController {/}: +13ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [RouterExplorer] Mapped {/, GET} route +5ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [RoutesResolver] TarefasController {/tarefas}: +0ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [RouterExplorer] Mapped {/tarefas, POST} route +1ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [RouterExplorer] Mapped {/tarefas, GET} route +1ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [RouterExplorer] Mapped {/tarefas/:id, GET} route +2ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [RouterExplorer] Mapped {/tarefas/:id, PATCH} route +1ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [RouterExplorer] Mapped {/tarefas/:id, DELETE} route +1ms
[Nest] 51213  - 04/09/2023, 06:12:03     LOG [NestApplication] Nest application successfully started +5ms

```

arquivo `./src/tarefas/entities/tarefa.entity.ts`
```ts
import { Column, Entity, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class Tarefa {
  @PrimaryGeneratedColumn('increment')
  id: number;

  @Column()
  titulo: string;

  @Column({ default: false })
  realizado: boolean;
}

```

arquivo `./src/tarefas/dto/create-tarefa.dto.ts`
```ts
export class CreateTarefaDto {
  titulo: string;
}

```

arquivo `./src/tarefas/tarefas.module.ts`
```ts
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';

import { TarefasService } from './tarefas.service';
import { TarefasController } from './tarefas.controller';
import { Tarefa } from './entities/tarefa.entity';

@Module({
  imports: [TypeOrmModule.forFeature([Tarefa])],
  controllers: [TarefasController],
  providers: [TarefasService],
})
export class TarefasModule {}

```


arquivo `./src/tarefas/tarefas.service.ts` - importações e construtor
```ts
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';

import { CreateTarefaDto } from './dto/create-tarefa.dto';
import { UpdateTarefaDto } from './dto/update-tarefa.dto';
import { Tarefa } from './entities/tarefa.entity';

@Injectable()
export class TarefasService {
  constructor(
    @InjectRepository(Tarefa) private tarefaRepository: Repository<Tarefa>,
  ) {}

  create(createTarefaDto: CreateTarefaDto) {
    return 'This action adds a new tarefa';
  }

  findAll() {
    return `This action returns all tarefas`;
  }

  findOne(id: number) {
    return `This action returns a #${id} tarefa`;
  }

  update(id: number, updateTarefaDto: UpdateTarefaDto) {
    return `This action updates a #${id} tarefa`;
  }

  remove(id: number) {
    return `This action removes a #${id} tarefa`;
  }
}

```

arquivo `./src/tarefas/tarefas.service.ts` - criar entidade no repositório e recuperar todas tarefas
```ts
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';

import { CreateTarefaDto } from './dto/create-tarefa.dto';
import { UpdateTarefaDto } from './dto/update-tarefa.dto';
import { Tarefa } from './entities/tarefa.entity';

@Injectable()
export class TarefasService {
  constructor(
    @InjectRepository(Tarefa) private tarefaRepository: Repository<Tarefa>,
  ) {}

  create(createTarefaDto: CreateTarefaDto) {
    return this.tarefaRepository.save(createTarefaDto);
  }

  findAll() {
    return this.tarefaRepository.find();
  }

  findOne(id: number) {
    return `This action returns a #${id} tarefa`;
  }

  update(id: number, updateTarefaDto: UpdateTarefaDto) {
    return `This action updates a #${id} tarefa`;
  }

  remove(id: number) {
    return `This action removes a #${id} tarefa`;
  }
}

```

arquivo `./src/tarefas/tarefas.controller.ts`
```ts
import {
  Controller,
  Get,
  Post,
  Body,
  Patch,
  Param,
  Delete,
} from '@nestjs/common';
import { TarefasService } from './tarefas.service';
import { CreateTarefaDto } from './dto/create-tarefa.dto';
import { UpdateTarefaDto } from './dto/update-tarefa.dto';

@Controller('tarefas')
export class TarefasController {
  constructor(private readonly tarefasService: TarefasService) {}

  @Post()
  async create(@Body() createTarefaDto: CreateTarefaDto) {
    return {
      estado: 'ok',
      mensagem: 'tarefa criada',
      dados: await this.tarefasService.create(createTarefaDto),
    };
  }

  @Get()
  async findAll() {
    return {
      estado: 'ok',
      mensagem: 'todas as tarefas listadas',
      dados: await this.tarefasService.findAll(),
    };
  }

  @Get(':id')
  findOne(@Param('id') id: string) {
    return this.tarefasService.findOne(+id);
  }

  @Patch(':id')
  update(@Param('id') id: string, @Body() updateTarefaDto: UpdateTarefaDto) {
    return this.tarefasService.update(+id, updateTarefaDto);
  }

  @Delete(':id')
  remove(@Param('id') id: string) {
    return this.tarefasService.remove(+id);
  }
}

```

# 4. Configurar projeto app-web
1. Abrir novo terminarl
2. Entrar na pasta do projeto
3. Adicionar bibliotecas ao projeto
4. Abrir o projeto no VS Code
5. Executar o projeto web

```console
$ $ npm i axios

added 212 packages, and audited 213 packages in 41s

41 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

$  npm i @mui/material @mui/styled-engine-sc styled-components

added 46 packages, and audited 259 packages in 19s

52 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities

$ code .

$ npm run dev

VITE v4.4.9  ready in 612 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h to show help

```

# 5. 
arquivo ``
```ts
```
