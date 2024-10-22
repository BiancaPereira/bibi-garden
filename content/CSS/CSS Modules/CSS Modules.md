
> [!info] Leituras
> - https://github.com/css-modules/css-modules
> - https://dev.to/gmantovani97/porque-utilizar-css-modules-no-react-1a93


### O que é?
- Uma forma de dar escopo aos arquivos CSS.
- É escrito igual arquivos de CSS normais.
- É adicionado um hash na classe na hora da compilação, fazendo com que a classe seja única:
```start-multi-column
ID: ID_l9oy
Number of Columns: 2
Largest Column: standard
```
- **Sem module:**
![[Pasted image 20221117143913.png]]

--- column-end ---

- **Com module:**
![[Pasted image 20221117143920.png]]

=== end-multi-column

> ℹ  Se você usou `create-react-app` provavelmente você já está habilitado para usar o CSS Modules.

### Usando ele
- Crie um arquivo com a extensão `.module.css`:
```css
/* App.module.css */
.className {
  color: green;
}
```

- Para usar as classes, basta importar ele.
- O arquivo exporta um objeto mapeado com todas as classes.

```javascript
import styles from "./App.module.css";
// import { className } from "./App.module.css";

element.innerHTML = '<div class="' + styles.className + '">';
```

### Nomeando
- Dê preferência para usar **camelCase** invés de **kebab-case** por ser mais fácil de usar.
```scss
/* Exemplos */
style['class-name']
style.className
```

### Estilos globais
- Você pode usar `:global` parar criar estilos globais.
```scss
:global {
  .global-class-name {
    color: green;
  }
}
```

### Composição/herança
- Você pode usar composição para fazer uma classe herdar de outra.
```scss
.className {
  color: green;
  background: red;
}

.otherClassName {
  composes: className;
  color: yellow;
}

/* Composição de outros arquivos */
.otherClassNameTwo {
  composes: className from "./style.css";
}
```

