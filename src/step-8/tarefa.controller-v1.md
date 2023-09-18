# API - tarefa.controller.ts - passo 8 - versão 1

arquivo `./src/tarefas/tarefa.controller.ts`
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
  async remove(@Param('id') id: string) {
    const { affected } = await this.tarefasService.remove(+id);
    if (affected === 1) {
      return {
        estado: 'ok',
        mensagem: `tarefa ${id} removida com sucesso`,
      };
    } else {
      return {
        estado: 'nok',
        mensagem: `tarefa ${id} NÃO removida`,
      };
    }
  }
}

```


- Modificado na linha 47 a função `remove` para `async remove`
- O conteúdo da função `remove` saiu de `return this.tarefasService.remove(+id);` para as linhas 48 a 59 do arquivo acima
  - linha 48 requisita a exclusão da tarefa passando o `id` de forma síncrona usando  o `async`.
  - linha 48 define também um constante `affected` do objeto que resulta da chamada a `remove`. esta constante informa quantos registros foram afetados do repositório.
  - linha 49 verifica se foi afetado 1 registro e assim apagado a tarefa, retornando um objeto `json` nas linhas 50 a 53
  - linha 54 é o caso de não ter apagado a tarefa, retorna objeto `json` informando a não remoção nas linhas 55 a 58

