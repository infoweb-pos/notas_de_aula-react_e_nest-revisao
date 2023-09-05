# AppTarefas.tsx - Passo 6 - Versão 5


arquivo `./src/componentes/AppTarefas.tsx`
```ts
import * as React from "react";
import List from "@mui/material/List";
import ListItem from "@mui/material/ListItem";
import ListItemButton from "@mui/material/ListItemButton";
import ListItemIcon from "@mui/material/ListItemIcon";
import ListItemText from "@mui/material/ListItemText";
import Checkbox from "@mui/material/Checkbox";
import IconButton from "@mui/material/IconButton";
import DeleteIcon from "@mui/icons-material/Delete";

interface InterfaceTarefa {
	id: number;
	titulo: string;
	realizado: boolean;
}

const TarefaListaItem = (props: {tarefa: InterfaceTarefa}) => {
	const labelId = `checkbox-list-label-${props.tarefa.id}`;

	return (
		<ListItem
			secondaryAction={
				<IconButton edge="end" aria-label="comments">
					<DeleteIcon />
				</IconButton>
			}
			disablePadding
		>
			<ListItemButton
				role={undefined}
				dense
			>
				<ListItemIcon>
					<Checkbox
						edge="start"
						checked={props.tarefa.realizado}
						tabIndex={-1}
						disableRipple
						inputProps={{ "aria-labelledby": labelId }}
					/>
				</ListItemIcon>
				<ListItemText id={labelId} primary={props.tarefa.titulo} />
			</ListItemButton>
		</ListItem>
	);
};

const AppTarefas = (props: {tarefas: Array<InterfaceTarefa>}) => {

	return (
		<List sx={{ width: "100%", bgcolor: "background.paper" }}>
			{props.tarefas.map((tarefa) => <TarefaListaItem key={tarefa.id} tarefa={tarefa}/>)}
		</List>
	);
};

export default AppTarefas;

```
