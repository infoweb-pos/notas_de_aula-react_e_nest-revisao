# AppTarefas.tsx - Passo 7 - Versão 5


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

- Apagar as linas 33 a 42, conteúdos de `<List>` linha 33 até `</List> linha 42.
- Adicionar nova linha 33, após `<Box>`, e colocar `<TarefasLista tarefas={props.tarefas} funcaoApagar={props.funcaoApagar} funcaoFinalizar={props.funcaoFinalizar} />`
- (opticional) Pedir para o VSCode formatar o arquivo
