# AppTarefas.tsx - Passo 7 - Versão 3


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import { Box, List } from "@mui/material";

import { InterfaceTarefa } from "../interfaces/Tarefa";
import { TarefaListaItem } from "./Tarefa/TarefaListaItem";

const TarefasLista = () => {
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

- Copiar as linhas 20 a 29, do `<List>` até o `</List>`
- Colar na linha 9, substituindo o `null` pelo conteúdo de `<List>` até o `</List>`
