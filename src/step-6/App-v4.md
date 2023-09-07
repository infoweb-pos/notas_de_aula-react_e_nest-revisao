# App.tsx - Passo 6 - Versão 3


arquivo `./src/App.tsx`
```ts
import { useState } from "react";

import AppLayout from "./componentes/AppLayout";
import AppNavBar from "./componentes/AppNavBar";
import AppTarefas from "./componentes/AppTarefas";
import { InterfaceTarefa } from "./interfaces/Tarefa";

function App() {
	const [tarefaNova] = useState("");
	const [tarefas, setTarefas] = useState([
		{ id: 1, titulo: "componentizar gui", realizado: false },
		{ id: 2, titulo: "montar gui com componentes", realizado: false },
		{ id: 3, titulo: "criar a API com método GET", realizado: true },
	]);

	const handleTarefaApagar = (tarefaParaExcluir: InterfaceTarefa) => {
		const novaLista = tarefas.filter(
			(tarefa) => tarefaParaExcluir.id !== tarefa.id
		);
		setTarefas(novaLista);
	};

	const handleTarefaFinalizar = (identificador: number) => {
		return tarefas.map((tarefa) => {
			if (tarefa.id === identificador) {
				return {
					...tarefa,
					realizado: !tarefa.realizado,
				};
			} else {
				return tarefa;
			}
		});
	};

	return (
		<AppLayout>
			<AppNavBar />
			<AppTarefas
				tarefa={tarefaNova}
				tarefas={tarefas}
				cliqueParaApagar={handleTarefaApagar}
			/>
		</AppLayout>
	);
}

export default App;

```


- adicionado linhas 23 a 34 com a função `handleTarefaFinalizar`