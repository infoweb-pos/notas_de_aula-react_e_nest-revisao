# Revisão de conceitos básicos sobre aplicação web com React e API Rest com Nest

## Informações gerais

- **Público alvo**: alunos da disciplina de POS (Programação Orientada a Serviços) do curso de Infoweb (Técnico Integrado em Informática para Internet) no CNAT-IFRN (Instituto Federal de Educação, Ciência e Tecnologia do Rio Grande do Norte - Campus Natal-Central)
- **Professor**: [L A Minora](https://github.com/leonardo-minora/)
- **Repositórios**
  - **aplicação web** [github](https://github.com/infoweb-pos/2023-revisao-web/)
  - **api rest** [github](https://github.com/infoweb-pos/2023-revisao-api/)

## Sumário

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

[app-revisao] $ npm create vite@latest
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

[app-revisao] $ code app-web

[app-revisao] $ npx @nestjs/cli new app-api
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

[app-revisao] $ code app-api

```
