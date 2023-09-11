# AppTarefas.tsx - Passo 7 - Versão 9


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import {
	Box,
	FormControl,
	IconButton,
	Input,
	InputAdornment,
	InputLabel,
} from "@mui/material";
import CheckIcon from "@mui/icons-material/Check";

import { InterfaceTarefa } from "../interfaces/Tarefa";
import { TarefasLista } from "./Tarefa/TarefaLista";

const TarefaNova = () => {
	return (
		<Box sx={{ maxWidth: "99%" }}>
			<FormControl fullWidth sx={{ m: 1 }} variant="standard">
				<InputLabel>Nova tarefa</InputLabel>
				<Input
					type={"text"}
					endAdornment={
						<InputAdornment position="end">
							<IconButton>
								<CheckIcon />
							</IconButton>
						</InputAdornment>
					}
				/>
			</FormControl>
		</Box>
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

- Subistituir o `null` por uma descrição com entrada de texto com botão, linhas 17 a 31 com `<Box>...</Box>`
- Importar componente do Material UI, formatando o documento, ficará conforme as linhas 2 a 9
