# AppTarefas.tsx - Passo 7 - Versão 1


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import { Box, List } from "@mui/material";

import { InterfaceTarefa } from "../interfaces/Tarefa";
import { TarefaListaItem } from "./Tarefa/TarefaListaItem";

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

- modificar linha 2
  - de `import List from "@mui/material/List";`
  - para `import { Box, List } from "@mui/material";`
- adicionar linha 13 e 14 com `<Box>` e `</Box>`
