# TarefasLista.tsx - Passo 7 - Versão única


arquivo `./src/componentes/Tarefa/TarefaLista.tsx`
```ts
import * as React from "react";
import { List } from "@mui/material";

import { InterfaceTarefa } from "../../interfaces/Tarefa";
import { TarefaListaItem } from "./TarefaListaItem";

export const TarefasLista = (props: {
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

```

- Criar arquivo novo em `./src/componentes/Tarefa/TarefaLista.tsx`
- Copiar conteúdo do componente interno `TarefasLista` do arquivo `./src/componentes/AppTarefas.tsx`
- Importar os componentes
- Exportar o componente `TarefasLista`
