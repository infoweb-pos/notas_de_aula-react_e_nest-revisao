# AppTarefas.tsx - Passo 7 - Versão 6


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import { Box } from "@mui/material";

import { InterfaceTarefa } from "../interfaces/Tarefa";
import { TarefasLista } from "./Tarefa/TarefaLista";

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

- Apagar as linhas de 7 a 25 que são do componente interno `TarefasLista`
- Apagar a linha 5 de importação do componente `TarefaListaItem`
- Adiocionar a linha 5 com `import { TarefasLista } from "./Tarefa/TarefaLista";`
- Modificar a linha 2 para `import { Box } from "@mui/material";`
