# TarefaNova.tsx - Passo 7 - Versão única


arquivo `./src/componentes/Tarefa/TarefaNova.tsx`
```ts
import * as React from "react";
import {
	Box,
	FormControl,
	IconButton,
	Input,
	InputAdornment,
	InputLabel
} from "@mui/material";
import CheckIcon from "@mui/icons-material/Check";

export const TarefaNova = (props: {
	tarefa: string;
	funcaoModificar: (texto: string) => void;
	funcaoAdicionar: () => void;
}) => {
	return (
		<Box sx={{ maxWidth: "99%" }}>
			<FormControl fullWidth sx={{ m: 1 }} variant="standard">
				<InputLabel>Nova tarefa</InputLabel>
				<Input
					type={"text"}
					endAdornment={<InputAdornment position="end">
						<IconButton onClick={() => props.funcaoAdicionar()}>
							<CheckIcon />
						</IconButton>
					</InputAdornment>}
					value={props.tarefa}
					onChange={(e) => props.funcaoModificar(e.target.value)}
					autoFocus
					onKeyDown={(e) => {
						if (e.key == 'Enter') {
							props.funcaoAdicionar();
						}
					}} />
			</FormControl>
		</Box>
	);
};

```
