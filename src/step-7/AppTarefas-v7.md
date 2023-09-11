# AppTarefas.tsx - Passo 7 - Versão 7


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import { Box } from "@mui/material";

import { InterfaceTarefa } from "../interfaces/Tarefa";
import { TarefasLista } from "./Tarefa/TarefaLista";

const TarefaNova = () => {
	return (
		null
	);
};

const AppTarefas = (props: {
	tarefas: Array<InterfaceTarefa>;
	funcaoApagar: (tarefa: InterfaceTarefa) => void;
	funcaoFinalizar: (id: number) => void;
}) => {
	return (
		<Box>
			<TarefaNova />
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

- Criar o componente interno `TarefaNova` conforme linhas 7 a 11
