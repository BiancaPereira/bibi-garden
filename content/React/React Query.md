> [!info] Código de Exemplo
> Link no Replit: https://replit.com/@biibis/Axios-React-Query-Test

### O que é?
- Biblioteca Javascript
- Simplifica como obtemos, cacheamos e sincronizamos dados que obtemos de APIs

### Como era antes dele?
- Usando o **FetchAPI** (padrão) acaba complicando quando precisamos fazer coisas comuns como *retry* numa chamada

### O que podemos fazer com ele?
- Exemplos:
	- `refetchOnWindowFocus`: atualiza quando o usuário sai da aba do browser e depois volta
	- `useInfiniteQuery()`: hook para ajudar em paginação infinita
- Eles tem um dev tools só deles 💕
- Ele é tão bom que pode eliminar Redux e outras bibliotecas de **gerenciamento de estado**
- Você pode adicionar diversas chamadas de `useQuery` e ele automaticamente vai chamar elas em **paralelo**

### Como usar?
- Comece instalando ele:
```bash
npm install react-query
```

- Depois você deve instanciar o `query client` e criar um `provider` pra ele:
```jsx
const queryClient = new QueryClient(); // Instância do query client

function App() {
	return (
		<QueryClientProvider client={queryClient}> // Provider
			<Cars />
			<ReactQueryDevtools> // Adiciona o dev tools
		</QueryClientProvider>
	)
}
```

- Criando uma chamada de API básica:
```javascript
async function fetchCars() {
	const res = await fetch('/data.json')
	return res.json()
}
```

- Usando o `useQuery` em um componente:
```jsx
function Cars() {
	// cars é uma key
	// fetchCars é o nome da função que faz o fetch
	const { data, status } = useQuery('cars', fetchCars)

	if (status === 'loading') {
		return <p>Loading...</p>
	}

	if (status === 'error') {
		return <p>Error!</p>
	}

	return (
		<ul>
			{data.map((car) => (
				<li key={car.id}>{car.make}</li>
			))}
		</ul>
	)
}
```

* OBS: Se a `request` falhar, o ReactQuery faz um `retry` 3x antes de jogar um erro.

### Mutation
- Quando fazemos um `post`, podemos atualizar os dados automaticamente da seguinte forma:
```jsx
function Cars() {
	// essa key é a que você usa para invalidar a query
	const postTodo = useQuery('todo', fetchTodos)

	const = useMutation(postTodo, {
		onSuccess: () => {
			// Invalida a query e faz uma nova chamada
			queryClient.invalidateQueries('todo')
		},
	})

	const onButtonClick = () => mutate(apiResponseData);
	
	return (
		<button onClick={onButtonClick}>
			Create new Todo
		</button>;
	)
}
```

### Enabled
* Caso exista um endpoint que depende de outro endpoint ser completado, você também pode usar o `enabled`:
```javascript
function Cars() {
	// Primeiro pega os usuários
	const { data: user } = useQuery<User[], Error>('user', getUser)

	const { data: cars } = useQuery<Car[], Error>(
		['cars', user],
		getProjectsByUser,
		{
			// A query não vai executar até que user exista
			enabled: !!user, 
		}
	)
}
```

### Dica - String das keys
- Use constants para criar a string das keys, exemplo:
```javascript
const USERS_KEY = "users";

const { data: user } = useQuery<User[], Error>(USERS_KEY, getUser)
```

