# AppTarefas.tsx - Passo 6 - Versão 7


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import List from "@mui/material/List";

import { InterfaceTarefa } from "../interfaces/Tarefa";
import { TarefaListaItem } from "./tarefa/TarefaListaItem";

const AppTarefas = (props: {
	tarefas: Array<InterfaceTarefa>;
}) => {
	return (
		<List sx={{ width: "100%", bgcolor: "background.paper" }}>
			{props.tarefas.map((tarefa) => (
				<TarefaListaItem
					key={tarefa.id}
					tarefa={tarefa}
				/>
			))}
		</List>
	);
};

export default AppTarefas;

```
