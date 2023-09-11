# AppTarefas.tsx - Passo 7 - Versão 11


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


- Modificado a linha 45 de `<TarefaNova />` para `<TarefaNova `
- Adicionado a linha 46 com `tarefa={props.tarefa}` 
- Adicionado a linha 47 com `funcaoModificar={props.funcaoTarefaNovaModificar}` 
- Adicionado a linha 48 com `funcaoAdicionar={props.funcaoAdicionar}`
- Adicionado a linha 49 com `/>`
