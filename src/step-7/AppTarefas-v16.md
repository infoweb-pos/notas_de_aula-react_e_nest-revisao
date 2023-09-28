# AppTarefas.tsx - Passo 7 - Versão 16


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import { Box } from "@mui/material";

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

- Apagar as linhas 15 a 45 do componente `TarefaNova`
- Inserir uma linha nova, na linha 14, com `import { TarefaNova } from "./Tarefa/TarefaNova";`
- Apagar a linha 10 `import CheckIcon from "@mui/icons-material/Check";`
- Modificado as importações do `@mui/material`, das linha 2 a 9, para `import {Box} from "@mui/material";`
