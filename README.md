# Ficha 2 - Template Node + Express

Template base para a ficha 2 da unidade curricular de Programacao. O objetivo e dar-te uma estrutura inicial em Node.js/Express com EJS e Bootstrap para que possas focar-te na logica de negocio e boas praticas MVC.

## Principais componentes

- **Express 5** para o servidor HTTP e gestao de rotas.
- **EJS** para views server-side com partials reutilizaveis (`src/views/partials`).
- **Bootstrap 5** + `public/style.css` para o layout inicial.
- **Mock data** em `src/data/lembretes.js` que simula uma base de dados (CRUD basico de lembretes).

## Requisitos

- Node.js 18+ (recomendado 20 LTS).
- npm 9+.

## Como arrancar

```bash
npm install
npm start # corre node index.js (adiciona a tua app Express aqui)
```

Caso estejas a trabalhar com Nodemon/ts-node, adiciona os teus scripts ao `package.json` conforme necessario.

## Estrutura de pastas

```
.
|-- public/
|   `-- style.css            # Overrides visuais sobre Bootstrap
|-- src/
|   |-- controllers/         # Coloca aqui a logica de cada view/feature
|   |-- data/
|   |   `-- lembretes.js     # Fonte de dados simulada
|   |-- routes/              # Define as rotas Express (dividir por modulo)
|   `-- views/
|       |-- home.ejs
|       |-- lembretes.ejs
|       |-- detalhe.ejs
|       |-- novo.ejs
|       |-- 404.ejs
|       `-- partials/
|           |-- _head.ejs
|           |-- _navbar.ejs
|           |-- _alerts.ejs
|           |-- _statsSummary.ejs
|           `-- _footer.ejs
|-- package.json
`-- LICENSE
```

## Fluxo sugerido

1. **Entry-point**: cria `index.js` (ou `src/app.js`) com `express()` e faz `app.use(express.static("public"))`, `app.set("view engine", "ejs")` e `app.set("views", "src/views")`.
2. **Rotas**: dentro de `src/routes` cria um router por dominio (`home`, `lembretes`, etc.) e exporta-os para o entry-point.
3. **Controladores**: em `src/controllers` coloca funcoes puras que recebem `req/res`, leem dados de `src/data/lembretes.js` e devolvem a view correta.
4. **Views**: usa os partials existentes para manter a consistencia visual; adiciona novos partials sempre que repetires marcado HTML.
5. **Dados**: enquanto nao existe base de dados real, usa as funcoes em cima de `lembretes.js` (array em memoria). Quando trocares para Mongo/Postgres, mantem a mesma API de controlador para evitar refatoracao.

## Scripts npm

- `npm start`: corre `node index.js`. Usa este script para arrancar o servidor em modo producao/dev simples.
- `npm test`: placeholder. Substitui por testes automatizados (p.ex. Vitest, Jest ou supertest) quando estruturares a API.

## Boas praticas para a ficha

- Mantem o **MVC** bem separado (routes -> controllers -> views/dados).
- Reutiliza partials e segue a nomenclatura `_nome.ejs`.
- Adiciona comentarios curtos no topo dos ficheiros a explicar o objetivo (ver exemplos nas views e em `style.css`).
- Quando evoluires para base de dados, mantem uma camada de servicos para isolar o acesso aos dados.

## Licenca

Este template usa a licenca ISC (ver `LICENSE`). Sente-te livre para reutilizar e adaptar nas proximas fichas ou projetos.
