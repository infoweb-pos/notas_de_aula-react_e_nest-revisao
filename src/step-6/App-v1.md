# App.tsx - passo 6 - versão 1

arquivo `./src/App.tsx`
```ts
import { useState } from "react";

import AppLayout from "./componentes/AppLayout";
import AppNavBar from "./componentes/AppNavBar";
import AppTarefas from "./componentes/AppTarefas";

function App() {
	const [tarefaNova] = useState("");
	const [tarefas] = useState([
    {id: 1, titulo: "componentizar gui", realizado: false},
    {id: 2, titulo: "montar gui com componentes", realizado: false},
    {id: 3, titulo: "criar a API com método GET", realizado: true},
  ]);

	return (
    <AppLayout>
      <AppNavBar />
      <AppTarefas tarefa={tarefaNova} tarefas={tarefas} />
    </AppLayout>
	);
}

export default App;

```
