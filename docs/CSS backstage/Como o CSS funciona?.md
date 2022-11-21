#performance #css #crp

> [!info] Referências
> - https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_works
> - https://developer.mozilla.org/en-US/docs/Web/Performance/Critical_rendering_path
> - https://developer.mozilla.org/en-US/docs/Learn/Performance/CSS
> - https://developer.mozilla.org/en-US/docs/Web/Performance/How_browsers_work

### Início
- Para renderizar na tela um documento, o navegador combina o HTML e CSS dele.
- Cada navegador faz isso de formas diferentes, mas semelhantes no geral.

### Critical Rendering Path
- É o passo a passo para o navegador converter HTML + CSS + JS em pixels na tela.

### 5 passos do CRP
1. Navegador carrega o HTML e converte ele em DOM.
2. Depois é carregado o CSS e construído o CSSOM.
3. É feito a análise do CSS, onde é inserido os estilos para o nó correto da árvore do DOM (essa é a **render tree**: CSS + HTML juntos).
4. O layout é quando é calculado o tamanho e localização de cada node na tela.
5. A página é exibida na tela através do processo de **painting**. 

![[Pasted image 20221119223639.png]]

> Depois que é carregado o Javascript, pode ser que a árvore DOM seja modificada.

> Enquanto o CSS está sendo transformado, o Javascript está sendo baixo e compilado.

### DOM (Document Object Model)
- Árvore criada a partir do HMTL.
- A construção do DOM é incremental e não bloqueia a página.
- Quando mais nodes você tiver, mais tempo o CRP vai tomar.
- Alguns nodes a mais não fazem diferença, mas se tiver muitos pode impactar na performance.

Exemplo de DOM:
```html
<p>
  Let's use:
  <span>Cascading</span>
  <span>Style</span>
  <span>Sheets</span>
</p>
```

Como eles se organizam em nodes:
```
P
├─ "Let's use:"
├─ SPAN
|  └─ "Cascading"
├─ SPAN
|  └─ "Style"
└─ SPAN
    └─ "Sheets"
```


### CSSOM (CSS Object Model)
- Árvore criada a partir do CSS.
- Enquanto o navegador está carregando o CSS, a páhina é bloqueada.
- Isso acontece porque as regras do CSS podem ser reescritas até que a CSSOM seja completada.
- A criação da árvore do CSS é muito rápida.
- Seletores mais espefícios (como `.foo {}`) são mais rápidos do que os menos específicos (como `.bar .foo {}`).
- Isso acontece porque se você usa o `.foo`, então o navegador vai precisar procurar o ancestral dele `.bar`.
- Esse tipo de otimização é bem mínima, pois o navegador renderiza essa árvore do CSS **muito rápido**.

### Melhorando a performance do CSS
- As partes que mais travam no carregamento da tela são os scrollings e animações.
- Minimize os arquivos.
- Separe os arquivos de forma que o navegador só carregue aquilo que é necessário naquela hora, como:

```html
<!-- Loading and parsing styles.css is render-blocking -->
<link rel="stylesheet" href="styles.css" />

<!-- Loading and parsing print.css is not render-blocking -->
<link rel="stylesheet" href="print.css" media="print" />

<!-- Loading and parsing mobile.css is not render-blocking on large screens -->
<link
  rel="stylesheet"
  href="mobile.css"
  media="screen and (max-width: 480px)" />
```

### Render tree
- É gerada quando a árvore do CSS é incluída na árvore do DOM e é criado a Render Tree.
- Para construir a render tree, o navegador checa cada node.
- Nessa hora, o navegador determina quais são as regras do CSS agregadas para cada node.
- Na render tree só temos os elementos **visíveis na tela**.

### Layout
- O layout é o processo que determina o tamanho e a localização de tudo na página.
- Depois que o layout é determinado, os pixels são pintados na tela.
- Ele depende do tamanho da tela (viewport size).
- Determia o tamanho e altura de cada elemento.
- Determina onde cada elemento fica em relação aos outros.
- Toda vez que a render tree é modificada, o processo de layout é ativado.
- Modificações na render tree poden ser: adição de nodes, conteúdo alterado, atualizado mox model (block, inline), mudança de tamanho da tela (como mudar a orientação do celular).
- Tem que tomar cuidado para não causar muitas mudanças na render tree para não causar travamentos na hora do scroll ou durante animações.

### Painting
- O paint é o último passo, ele é responsável por pintar os pixels na tela.
- Ao carregar uma tela, a tela inteira sofre o painting.
	- Esse primeiro painting é chamado de "first meaningful paint".
- Depois, apenas a parte necessária da tela que sofrer mudanças sofrerá o re-painting.
- Paiting é um processo bem rápido, e não impacta tanto na performance.
- O tempo do paiting demora de acordo com o tipo de mudança que é feita.

### Camadas
- Para minimizar o tempo de **repaiting**, geralmente a tela é dividida em diversas camadas.
	- Você pode usar `will-change` e outras propriedades que vão gerar camadas.
	- No entanto camadas usa muito gerenciamento de memória, evite usar em excesso.
- **Compositing** acontece para desenhar as camadas na ordem correta.

### Reflow
- Reflow é quando é necessário ser feito mudanças de tamanho ou posição (mudanças de **layout**) após o primeiro carregamento da página.
- Exemplo:
	- Imagine que você carregou um documento HTML com uma imagem, e essa imagem vai ser baixada só depois.
	- Se você não determinou o tamanho dessa imagem no HTML, então quando ela for carrega será feito um processo de reflow.

### Otimizando o CRP
- Priorize a ordem e carregue os recursos prioritários primeiro.
- Diminuia o número de requests e o diminua o tamanho dos arquivos prioritários.
- Diminua a quantidade de arquivos principais e deixe com que os arquivos não-críticos sejam carregados depois ou de forma assíncrona.

### Problemas de performance
- Maiores problemas de performance na web:
	- 🟠  **Período de latência** (tempo do início de um evento até ele de fato iniciar a execução).
	- Navegadores são single-thread (executam um comando por vez).
- Para que o site seja rápido, é necessário minimizar as requisições da thread principal.

### Como é feito as requisições ao browser
- Quando o site carrega pela primeira vez, é necessário fazer uma busca de **DNS** do site.
	- A latência de uma rede de celular para fazer essa busca pode ser demorada.
	- Depois que o endereço de **IP** é localizado, será aberto uma comunicação entre o navegador e o servidor, através do **TCP**.
![[Pasted image 20221120184907.png]]

- Para começar a estabelecer uma conexão com o servidor e poder fazer as primeiras requisições, todo o caminho abaixo é feito:
![[Pasted image 20221120185434.png]]

### Primeira renderização
- Na primeira renderização geralmente é feito uma **chamada de 14kb**, e depois essa chamada vai aumentando de tamanho de acordo com o tanto que a rede aguenta.
	- Por isso é importante priorizar o que é trazido na primeira chamada ao servidor.
	- É preciso que já seja enviado nesses 14kb o HTML/CSS que deve ser exibido nessa primeira chamada.
	- Depois que é recebido o HTML/CSS e Javascript inicial, que eles começam a ser carregados e transformados em render tree, até que sejam renderizados na tela.
- Tags `<script>` sem `async` geralmente bloqueiam o carregamento da página (por isso costumamos deixar eles no fim do da tag `<body>`).

### Accessibility Tree
- Existe uma árvore de acessibilidade que é como se fosse o DOM semântico.
- Ela é a **AOM** - Accessibility Object Model.
- Enquanto a AOM não é construída, a página não é acessível a leitores de tela.