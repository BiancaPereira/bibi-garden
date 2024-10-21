> [!info] Código de Exemplo
> Link no Replit: [Test Axios React](https://replit.com/@biibis/Test-Axios-React#src/App.tsx)

[[react]]

- Biblioteca Javascript
- Usada parea fazer **HttpRequests**
- Fácil de usar 
- Ele pode criar uma URL base

- Não precisa transformar a response em `json()` como no **FetchAPI**
	- O Axios faz isso sozinho

- Axios suporta interceptors
	- Usa para interceptar o cors sempre que uma API é chamada
	- É útil quando você quer automaticamente adicionar headers a todas as suas chamadas

* Maior diferença entre Axios e FetchAPI: Tratamento de erros
	* Se uma API retorna um erro, o FetchAPI não vai fazer um `trown Error`
	* Já o Axios faz isso para você 
	* Você pode realizar a chamada da api em um bloco `try...catch`
