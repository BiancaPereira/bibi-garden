---
tags:
  - react
  - frontend
  - tanstack
---
> [!NOTE] Leituras
> - https://tkdodo.eu/blog/react-query-as-a-state-manager
> - https://dev.to/juandj/using-react-query-to-solve-state-management-in-your-react-app-4kf9

- O [[React Query]] não é uma biblioteca de data fetching
- São poucas as features que são ligadas a networking

> **React Query é um gerenciador de estados assíncrono**

- O React Query mantém os dados que são server-side armazenados, enquanto os outros dados podem ser armazenados com `useContext`
	- Geralmente os dados armazenados direto no frontend são dados como *a modal está aberta*?
	- Manter os 2 tipos de dados faz muito sentido nesses casos
- A `QueryKey` identifica sua query e se você chamar ela em dois locais diferentes, ele vai te trazer os mesmos dados
- Isso pode ser abstraído em um hook, como no exemplo abaixo:

```javascript
export const useTodos = () => useQuery(['todos'], fetchTodos)

function ComponentOne() {
  const { data } = useTodos()
}

function ComponentTwo() {
  // ✅ will get exactly the same data as ComponentOne
  const { data } = useTodos()
}

const queryClient = new QueryClient()

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <ComponentOne />
      <ComponentTwo />
    </QueryClientProvider>
  )
}
```


### Deduplicação de dados
- **Deduplicar** é uma técnica para eliminar cópias de dados repetidos
- React Query faz a *deduplicação* das chamadas de API que acontecem ao mesmo tempo

### Cache
- O React Query cacheia os resultados para você, dessa forma ele não precisa ficar chamando o endpoint a todo momento
- Enquando o frontend exibe um resultado cacheado, o React Query revalida esses dados novamente para ver se o backend não atualizou ele

### Gatilhos para refetch
- `refetchOnMount`
- `refetchOnWindowFocus`
- `refetchOnReconnect`
- Invalidação manual: `queryClient.invalidateQueries`

### Evitando refresh desnecessário
- Padrões de comportamento: https://tanstack.com/query/v4/docs/guides/important-defaults
- Geralmente esses padrões funcionam bem, mas podemos subescrevê-los
- Você pode desabilitar gatilhos como o `refetchOnMount`
- Ou pode usar o `staleTime`:
	- O padrão é que assim que é feita a chamada dos dados, eles são considerados **stale** ou *desatualizados*
	- Configurando o `staleTime` você pode definir um tempo maior para considerar os dados como *desatualizados* e diminuir as chamadas do endpoint

### Resultado e tipos de erros
Quando você usa um hook de `useQuery`, o React Query te permite prover os tipos de resultado e erro. 

Exemplo:

```javascript
const useGetUsers = () => {
   return useQuery<User[], Error>('users', fetchUsers)
}
```

