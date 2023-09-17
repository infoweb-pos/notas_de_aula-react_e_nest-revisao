# App.tsx - Passo 8 - Versão 2

- Adicionado `useEffect` para recuperar dados da API.


arquivo `./src/App.tsx`
```ts
import { useEffect, useState } from "react";

import AppLayout from "./componentes/AppLayout";
import AppNavBar from "./componentes/AppNavBar";
import AppTarefas from "./componentes/AppTarefas";
import { InterfaceTarefa } from "./interfaces/Tarefa";
import axios from "axios";

function App() {
	const [tarefaNova, setTarefaNova] = useState("");
	const [tarefas, setTarefas] = useState([
		{ id: 1, titulo: "componentizar gui", realizado: false },
		{ id: 2, titulo: "montar gui com componentes", realizado: false },
		{ id: 3, titulo: "criar a API com método GET", realizado: true },
	]);

	useEffect(() => {
		axios.get("http://localhost:3000/tarefas/").then((resposta) => {
			setTarefas(resposta.data.dados);
		});
	});

	const handleTarefaApagar = (tarefaParaExcluir: InterfaceTarefa) => {
		const novaLista = tarefas.filter(
			(tarefa) => tarefaParaExcluir.id !== tarefa.id
		);
		setTarefas(novaLista);
	};

	const handleTarefaFinalizar = (identificador: number) => {
		const novaLista = tarefas.map((tarefa) => {
			if (tarefa.id === identificador) {
				return {
					...tarefa,
					realizado: !tarefa.realizado,
				};
			} else {
				return tarefa;
			}
		});
		setTarefas(novaLista);
	};

	const handleTarefaAdicionar = () => {
		axios
			.post("http://localhost:3000/tarefas/", { titulo: tarefaNova })
			.then((resposta) => {
				setTarefas([...tarefas, resposta.data]);
				setTarefaNova("");
			});
	};

	return (
		<AppLayout>
			<AppNavBar />
			<AppTarefas
				tarefa={tarefaNova}
				funcaoTarefaNovaModificar={setTarefaNova}
				funcaoAdicionar={handleTarefaAdicionar}
				tarefas={tarefas}
				funcaoApagar={handleTarefaApagar}
				funcaoFinalizar={handleTarefaFinalizar}
			/>
		</AppLayout>
	);
}

export default App;

```

- Modificar a função `handleTarefaAdicionar` adicionando a chamada a API com axios
