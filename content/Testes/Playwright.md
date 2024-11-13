---
tags:
  - frontend
  - testes
  - e2e
  - playwright
---
### Filosofia de testes
- Faça os testes os mais isolados e independentes possível.
	- Use o `test()` para separar os cenários.
	- Em caso de repetições use o `beforeEach` para coisas como ir para a URL desejada.
- Não teste APIs/sites de terceiros.
	- Você pode usar a [API de Network](https://playwright.dev/docs/network#handle-requests).
- Se está testando um banco de dados:
	- Teste no ambiente de staging/homolog.
	- Tenha certeza de que os dados não vão mudar.

### Melhores práticas
- Sempre seleciones textos visíveis para o usuário.
- Use o [codegen](https://playwright.dev/docs/codegen) para obter os melhores locators (selects de elemento).

- Não use asserts manuais ou coloque o await no local errado:
```ts
// 👎
expect(await page.getByText('welcome').isVisible()).toBe(true);

// 👍
await expect(page.getByText('welcome')).toBeVisible();
```

- É recomendado fazer o debug com a [extensão do VSCode](https://marketplace.visualstudio.com/items?itemName=ms-playwright.playwright).
![[debug-vscode-playwright.png]]
- Você também pode debugar com os seguintes comandos:
```bash
npx playwright test --debug

# ou

npx playwright test example.spec.ts:9 --debug
```

- Para debugar na pipeline/CI, use o [TraceViewer](https://playwright.dev/docs/trace-viewer):
```bash
npx playwright test --trace on
```

- Ative essa opção de lint:
```json
{
	'@typescript-eslint/no-floating-promises': 'warn',
}
```


- Paralelismo:
	- O playwright roda os testes em paralelo como padrão.
	- Você pode alterar essa configuração assim:
```ts
import { test } from '@playwright/test';

test.describe.configure({ mode: 'parallel' });

test('runs in parallel 1', async ({ page }) => { /* ... */ });
test('runs in parallel 2', async ({ page }) => { /* ... */ });
```

### Produtividade
- Você pode usar o soft para que seus testes não parem se quebrar:
```ts
// Make a few checks that will not stop the test when failed...  
await expect.soft(page.getByTestId('status')).toHaveText('Success');  
  
// ... and continue the test to check more things.  
await page.getByRole('link', { name: 'next page' }).click();
```

### Exemplos
1. Testes variados: https://github.com/akshayp7/playwright-typescript-playwright-test/tree/main/tests
2. Testes com mock de APIs: https://github.com/codewithmmak/playwright-api-testing/tree/master/tests
3. Esse é o exemplo que vem quando você instala o Playwright: https://github.com/BakkappaN/PlaywrightTutorialFullCourse/blob/main/tests-examples/demo-todo-app.spec.js
4. Testes feitos durante um curso do Youtube: https://github.com/BakkappaN/PlaywrightTutorialFullCourse/tree/main/tests
