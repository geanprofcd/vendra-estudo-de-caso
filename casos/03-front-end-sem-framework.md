# 105 telas e nenhum framework de front-end

## A decisão
O VENDRA renderiza as telas no servidor com FastAPI e Jinja2. O JavaScript e o CSS são escritos à mão, sem React, Vue ou Tailwind. O Three.js aparece só no mapa 3D.

## Por quê
- **Um serviço só no Railway**, sem etapa de build de front-end. Deploy simples e menos coisa para quebrar.
- **App leve.**
- **Mudança por pacotes pequenos.** Dá para trocar o visual tela por tela, sem reescrever o produto.
- **Preservar o original.** A regra do projeto era manter a interface e a estrutura do produto que já estava em uso enquanto o visual novo era construído.

## O que existe no front hoje
- Design system próprio, com tokens de cor, tipografia e movimento, num pacote de CSS gerado por script
- O V, um assistente de IA num widget de chat dentro do app
- Extensão Chrome Manifest V3 que lê os sistemas do cliente
- Testes com clique real no navegador (Playwright) na suíte do app

## O plano
Não há plano de migrar para uma SPA. Quando a estrutura estabilizar, o próximo passo previsto é HTMX + Alpine.js, componentes Jinja, TypeScript com esbuild e ECharts nos gráficos. Isso ainda é plano, não está no código.

## O que eu levo
Nem todo produto precisa de SPA. Para um time pequeno com deploy simples, HTML no servidor resolve bem e deixa o esforço onde o cliente sente.
