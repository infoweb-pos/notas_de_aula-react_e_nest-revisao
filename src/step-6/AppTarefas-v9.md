# AppTarefas.tsx - Passo 6 - Versão 9


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import List from "@mui/material/List";

import { InterfaceTarefa } from "../interfaces/Tarefa";
import { TarefaListaItem } from "./tarefa/TarefaListaItem";

const AppTarefas = (props: {
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

export default AppTarefas;

```

- adicionado linha 10 com `funcaoFinalizar: (id: number) => void;`
- adicionado linha 19 com `cliqueParaFinalizar={props.funcaoFinalizar}`
