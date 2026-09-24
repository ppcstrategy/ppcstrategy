# PPC Strategy Consultoria de Negócios — Site Institucional

Site estático (HTML/CSS/JS puro, sem build step) para divulgação da PPC Strategy Consultoria de Negócios.

## Estrutura

```
index.html          Landing page (Seção 01 hero, Seção 02 solução/BI, Seção 03 contato no footer)
servicos.html        Página com os 6 serviços da consultoria
css/style.css        Estilos globais
js/script.js         Menu mobile, scroll reveal, contadores animados
```

## Tema claro/escuro

O site abre no tema escuro (padrão do design) e o usuário pode alternar para o tema claro pelo botão de
sol/lua no cabeçalho. A preferência é salva no `localStorage` do navegador (`ppc-theme`) e mantida entre
`index.html` e `servicos.html`. Toda a paleta é controlada por variáveis CSS em `css/style.css` (bloco
`:root` para o tema escuro e `:root[data-theme="light"]` para o claro).

## Responsividade

Layout construído com CSS Grid/Flexbox e breakpoints em 960px, 720px e 480px: menu vira um dropdown com
botão hambúrguer, grids de cards colapsam para 1–2 colunas, tipografia usa `clamp()` para escalar
fluidamente, e o gráfico do hero é redimensionado para telas pequenas.

## Decisão de arquitetura: banco de dados

Não é necessário banco de dados. O site é puramente informacional (institucional + contato), sem
formulários, login ou conteúdo dinâmico gerado pelo usuário. O contato acontece via link direto para
WhatsApp (`wa.me`, que redireciona automaticamente para app mobile, WhatsApp Web ou desktop conforme o
dispositivo) e via e-mail exibido em texto (sem link `mailto:`, conforme especificado no escopo).

Se no futuro for necessário um formulário de contato com persistência, a recomendação é usar um serviço
free-tier compatível com GitHub Pages (site estático), como Formspree ou Google Forms embutido — sem
precisar de servidor/backend próprio.

## Validar localmente antes de publicar

Não é preciso instalar nada além de um servidor estático simples. Duas opções:

**Opção 1 — Python (já vem no Windows/Mac/Linux normalmente):**
```bash
python -m http.server 8000
```
Depois acesse http://localhost:8000 no navegador.

**Opção 2 — VS Code:** instale a extensão "Live Server" e clique em "Go Live" com `index.html` aberto.

Revise em telas de desktop e mobile (redimensione a janela ou use o modo responsivo do navegador) antes
de publicar.

## Deploy no GitHub Pages

1. Crie um repositório novo na conta específica do projeto (ex: `ppc-strategy-site`).
2. Envie todos os arquivos desta pasta para a branch `main`:
   ```bash
   git init
   git add .
   git commit -m "Site institucional PPC Strategy Consultoria"
   git branch -M main
   git remote add origin https://github.com/<usuario>/<repositorio>.git
   git push -u origin main
   ```
3. No GitHub, vá em **Settings → Pages**.
4. Em "Build and deployment", selecione **Deploy from a branch**, branch `main`, pasta `/ (root)`.
5. Salve. O site ficará disponível em `https://<usuario>.github.io/<repositorio>/` em alguns minutos.

Como é um site 100% estático (sem dependências de build), qualquer novo `git push` na branch `main`
atualiza o site publicado automaticamente.

## Configuração de contato

O número de WhatsApp está configurado como `5561991180117` (formato `wa.me`). Para alterar, substitua
esse número nos arquivos `index.html`, `servicos.html` (todos os links `https://wa.me/...`).
