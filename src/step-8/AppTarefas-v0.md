# AppTarefas.tsx - Passo 8 - Versão inicial


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import {Box} from "@mui/material";

import { InterfaceTarefa } from "../interfaces/Tarefa";
import { TarefasLista } from "./Tarefa/TarefaLista";
import { TarefaNova } from "./Tarefa/TarefaNova";

const AppTarefas = (props: {
	tarefa: string;
	funcaoTarefaNovaModificar: (texto: string) => void;
	funcaoAdicionar: () => void;
	tarefas: Array<InterfaceTarefa>;
	funcaoApagar: (tarefa: InterfaceTarefa) => void;
	funcaoFinalizar: (id: number) => void;
}) => {
	return (
		<Box>
			<TarefaNova 
				tarefa={props.tarefa}
				funcaoModificar={props.funcaoTarefaNovaModificar}
				funcaoAdicionar={props.funcaoAdicionar}
			/>
			<TarefasLista
				tarefas={props.tarefas}
				funcaoApagar={props.funcaoApagar}
				funcaoFinalizar={props.funcaoFinalizar}
			/>
		</Box>
	);
};

export default AppTarefas;

```

- Adicioando linha 35 com `autoFocus` para o focu do teclado ir para a caixa de texto.
- Adicionado linha 36 a 40 com o tratamento de quando pressionar a tecla `Enter` adicionar nova tarefa.
