---
tags:
  - livro
  - cleancode
  - programação
  - carreira
---
## Início
* Nós como devs somos responsáveis em **proteger a qualidade do código**.
* Um casa com janela quebrada parece que ninguém cuida dela.
	* Dessa forma, outras pessoas deixam de cuidar dela também.
	* Uma única janela começa o processo de degradação da casa.
	* Com o código é a mesma coisa.
* Um código sem testes não é limpo.
* O código ruim diminui a produtividade com o tempo.

## Nomes
- Evite informações erradas nos nomes. Exemplos:
	- `accountArray` é realmente um array?
	- `car` é realmente um carro? Se for vários, você deveria usar `cars`
- Use nomes pronunciáveis. Exemplo:
	- Função `dhms` poderia ser `dateAndHour`
- Não adicione contextos desnecessários. Exemplo:
	- Você está construindo uma aplicação chamada Gas Station Deluxe.
	- Você decide adotar a sigla GSD para todas variáveis.
	- Quando você for usar o auto-complete do código, ao digitar G, você recebe uma lista quilométrica de opções, sendo contra-produtivo.
- Não tenha medo de **renomear** para nomes melhores e mais claros.

## Funções
* As funções devem ser pequenas.
* As funções devem fazer apenas uma coisa (sempre que possível).
* O código deve ser lido de cima para baixo, como uma **narrativa**.
* Use o mínimo de **parâmetros** possível. De preferência, zero, um e até dois parâmetros. Ao passar de 3 ou mais, deve-se revisar o código.
* **Efeitos colaterais** são mentiras, são coisas que seu código faz escondido.
* O sistema é construído a partir de uma linguagem que o programador usa para descrever o sistema:
	* as funções são os verbos,
	* as classes os substantivos.


> [!attention] 
> Não esquecer tratativas de erro!


## Comentários
* Quando fazer um **comentário**, verifique se você pode deixar o código mais claro para substituir esse comentário.
* Para repositórios open source, comentários como documentação são muito utilizados e bem detalhados, porque são códigos que todas as pessoas devem entender plenamente para poder contribuir.
* Tomar muito cuidado para os comentários não ficarem **desatualizados** (ex: alterar o código e esquecer de alterar ou deletar comentário).
* É bom comentar códigos cabulosos que precisaram ser feitos e que dificilmente vão ser compreendidos sem essa documentação no futuro.

## Testes
* Devemos deixar os testes limpos.
* A melhor forma de deixar os testes limpos é focar na **legibilidade**.
* Deixe seus testes sucintos e expressivos.
* É recomendado fazer um assert por teste unitário.
* F.I.R.S.T:
	* Fast
	* Independent
	* Repeatable
	* Self-validating (resultado deve ser auto-explicativo: falhou/passou)
	* Timely (escrever testes antes do código)
* Se seus testes se degradarem, seu código também degradará.


