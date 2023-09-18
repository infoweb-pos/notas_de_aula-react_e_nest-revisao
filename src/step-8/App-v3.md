# App.tsx - Passo 8 - Versão 3

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
		api
			.post("/tarefas/", { titulo: tarefaNova })
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

- Inserir uma nova linha 10 com `const api = axios.create({ baseURL: "http://localhost:3000/" });` para criar uma instância personalizada do `axios`
- Modificar a linha 19 de `axios.get("http://localhost:3000/tarefas/")` para `api.get("/tarefas/")`
- Modificar a linha 46 de `axios` para `api`
- Modificar a linha 47 de `post("http://localhost:3000/tarefas/")` por `post("/tarefas/")`
