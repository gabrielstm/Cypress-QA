(The file `c:\Users\gos\Desktop\projetos\Cypress-QA\README.md` exists, but is empty)
# Cypress-QA

Projeto de testes de UI usando Cypress com suporte a Cucumber (BDD). Este repositório contém exemplos e testes organizados em `cypress/` que cobrem interações com formulários, uploads/downloads, validações de texto, hooks e um fluxo de checkout.

## Recursos

- Cypress para testes end-to-end.
- cypress-cucumber-preprocessor para escrever testes no estilo BDD (.feature).
- Geração de relatório com `multiple-cucumber-html-reporter` (script de pós-execução já configurado).

## Pré-requisitos

- Node.js (recomendo v14+). Verifique com:

```powershell
node -v
npm -v
```

- PowerShell (Windows) — os exemplos abaixo usam PowerShell.

## Instalação

1. Abra um terminal (PowerShell) no diretório do projeto (`c:\Users\gos\Desktop\projetos\Cypress-QA`).
2. Instale as dependências:

```powershell
# Instala as dependências do projeto
npm install
```

## Scripts úteis

O `package.json` já contém alguns scripts úteis:

- `npm run cypress:run` — executa os testes em modo headless (CLI). Após a execução, o script `postcypress:run` executará o gerador de relatório (`cucumber-html-reporter.js`).

Você também pode usar o Cypress instalado localmente com `npx`:

```powershell
# Abrir o Cypress Test Runner (interface gráfica)
npx cypress open

# Executar todos os testes em modo headless (linha de comando)
npm run cypress:run

# Executar um arquivo/feature específico (use aspas no PowerShell)
# Exemplo: rodar todos os .feature na pasta de features
npx cypress run --spec "cypress/integration/features/**/*.feature"

# Ou rodar um spec JS específico (por exemplo um spec do diretório specs)
npx cypress run --spec "cypress/integration/specs/Assercao.spec.js"
```

Observação: o `--spec` aceita glob patterns; ajuste conforme sua organização de arquivos.

## Relatórios (Cucumber HTML)

O projeto já possui um script de pós-execução configurado: ao rodar `npm run cypress:run`, será executado `node cucumber-html-reporter.js` (conforme `package.json`).

Se preferir executar manualmente:

```powershell
# Gera o relatório a partir dos JSONs gerados pelo preprocessor
node cucumber-html-reporter.js
```

Os arquivos JSON do Cucumber são gerados em `cypress/cucumber-json` (configurado no `package.json`). O relatório gerado normalmente ficará em `reports/` ou conforme configuração do `cucumber-html-reporter.js`.

## Estrutura principal do projeto

Principais pastas e arquivos (resumo):

- `cypress/fixtures/` — dados de teste (JSONs, textos, etc.)
- `cypress/integration/features/` — arquivos `.feature` (BDD)
- `cypress/integration/specs/` — specs de exemplo em JS
- `cypress/pages/` — Page Objects (Pages e Elements)
- `cypress/plugins/index.js` — plugins do Cypress (incluindo Cucumber preprocessor)
- `cypress/support/` — comandos customizados e hooks
- `cucumber-html-reporter.js` — script para gerar relatório HTML a partir dos JSONs
- `cypress.json` — configuração do Cypress

Explore as pastas `cypress/steps/` para ver as implementações dos steps do Cucumber.

## Como contribuir

1. Fork o repositório.
2. Crie uma branch com sua feature: `git checkout -b feature/minha-feature`.
3. Adicione testes e/ou correções.
4. Abra um pull request descrevendo as mudanças.

## Dicas e resolução de problemas

- Se o Cypress não abrir, verifique se as dependências foram instaladas corretamente: `npm install`.
- Para limpar vídeos e screenshots entre execuções, remova as pastas `cypress/videos` e `cypress/screenshots` (se existirem).
- Se os `.feature` não forem reconhecidos, confirme que o plugin `cypress-cucumber-preprocessor` está configurado em `cypress/plugins/index.js` e que `cypress-cucumber-preprocessor` está listado em `devDependencies`.

## Contato

Autor / referência no package.json: Thairam Michel Santos Ataíde

---

Resumo: este README explica como instalar dependências, abrir o Test Runner (`npx cypress open`), executar todos os testes em modo headless (`npm run cypress:run`), executar specs/feature específicas com `--spec` e gerar relatórios com `node cucumber-html-reporter.js`.

Se quiser, eu posso também: adicionar exemplos de comando para CI (GitHub Actions), criar um script `cypress:open` em `package.json`, ou atualizar `cucumber-html-reporter.js` para personalizar saída do relatório. Diga qual você prefere seguir em seguida.
