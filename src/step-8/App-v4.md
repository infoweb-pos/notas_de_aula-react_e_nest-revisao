

```ts
import { useEffect, useState } from "react";

import AppLayout from "./componentes/AppLayout";
import AppNavBar from "./componentes/AppNavBar";
import AppTarefas from "./componentes/AppTarefas";
import { InterfaceTarefa } from "./interfaces/Tarefa";
import axios from "axios";

function App() {
	const api = axios.create({ baseURL: "http://localhost:3000/" });
	const [tarefaNova, setTarefaNova] = useState("");
	const [tarefas, setTarefas] = useState([
		{ id: 1, titulo: "componentizar gui", realizado: false },
		{ id: 2, titulo: "montar gui com componentes", realizado: false },
		{ id: 3, titulo: "criar a API com método GET", realizado: true },
	]);

	useEffect(() => {
		api.get("/tarefas/").then((resposta) => {
			setTarefas(resposta.data.dados);
		});
	});

	const handleTarefaApagar = (tarefaParaExcluir: InterfaceTarefa) => {
		api.delete(`/tarefas/${tarefaParaExcluir.id}`).then((resposta) =>
			console.log(resposta.data)
		);
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
		api.post("/tarefas/", { titulo: tarefaNova }).then((resposta) => {
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
