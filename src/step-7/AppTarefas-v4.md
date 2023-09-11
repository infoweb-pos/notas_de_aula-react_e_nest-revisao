# AppTarefas.tsx - Passo 7 - Versão 4


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import { Box, List } from "@mui/material";

import { InterfaceTarefa } from "../interfaces/Tarefa";
import { TarefaListaItem } from "./tarefa/TarefaListaItem";

const TarefasLista = (props: {
	tarefas: Array<InterfaceTarefa>;
	funcaoApagar: (tarefa: InterfaceTarefa) => void;
	funcaoFinalizar: (id: number) => void;
}) => {
	return (
		<List sx={{ width: "100%", bgcolor: "background.paper" }}>
			{props.tarefas.map((tarefa) => (
				<TarefaListaItem
					key={tarefa.id}
					tarefa={tarefa}
					cliqueParaApagar={props.funcaoApagar}
					cliqueParaFinalizar={props.funcaoFinalizar}
				/>
			))}
		</List>
	);
};

const AppTarefas = (props: {
	tarefas: Array<InterfaceTarefa>;
	funcaoApagar: (tarefa: InterfaceTarefa) => void;
	funcaoFinalizar: (id: number) => void;
}) => {
	return (
		<Box>
			<List sx={{ width: "100%", bgcolor: "background.paper" }}>
				{props.tarefas.map((tarefa) => (
					<TarefaListaItem
						key={tarefa.id}
						tarefa={tarefa}
						cliqueParaApagar={props.funcaoApagar}
						cliqueParaFinalizar={props.funcaoFinalizar}
					/>
				))}
			</List>
		</Box>
	);
};

export default AppTarefas;

```

- Copiar conteúdo da linha 22 até 26, do conteúdo de `props` linha 22 até `}` linha 22
- Colar na linha 7 entre os parenteses `()`, definindo `props` do componente interno `TarefasLista`
