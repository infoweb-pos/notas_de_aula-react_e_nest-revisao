# AppTarefas.tsx - Passo 7 - Versão 12


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

const TarefaNova = (props: {
	tarefa: string;
	funcaoTarefaNovaModificar: (texto: string) => void;
	funcaoAdicionar: () => void;
}) => {
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

- Adicionar 4 novas linhas após a linha 15;
- Modificar a linha 15 para `const TarefaNova = (props: {`
- Modificar a linha 16 para `tarefa: string;`
- Modificar a linha 17 para `funcaoTarefaNovaModificar: (texto: string) => void;`
- Modificar a linha 18 para `funcaoAdicionar: () => void;`
- Modificar a linha 19 para `}) => {`
