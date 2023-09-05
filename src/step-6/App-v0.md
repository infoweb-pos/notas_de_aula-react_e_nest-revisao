# App.tsx - passo 6 - versão inicial

arquivo `./src/App.tsx`
```ts
import { useState } from "react";

import AppLayout from "./componentes/AppLayout";
import AppNavBar from "./componentes/AppNavBar";
import AppTarefas from "./componentes/AppTarefas";

function App() {
	const [tarefaNova] = useState("");
	const [tarefas] = useState(undefined);

	return (
		<AppLayout>
			<AppNavBar />
			<AppTarefas tarefa={tarefaNova} tarefas={tarefas} />
		</AppLayout>
	);
}

export default App;

```
