# API - tarefa.service.ts - passo 8 - versão inicial

arquivo `./src/tarefas/tarefa.service.ts`
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
