# Formulário — Sessão Estratégica 8Rs

Página pronta para publicar. É um site estático: não precisa de servidor, banco de dados nem plugin.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | O formulário. Página única, com CSS e JavaScript embutidos. |
| `og-cover.png` | Imagem de prévia do link (1200 × 630). É o que aparece quando você cola o link no WhatsApp, Instagram ou LinkedIn. |
| `og-cover.html` | O gerador da imagem acima, caso você queira editar o texto e exportar de novo. Não precisa ir para o ar. |
| `README.md` | Este arquivo. |

---

## Antes de publicar: 1 ajuste obrigatório

Abra o `index.html` num editor de texto e troque **`https://SEU-DOMINIO.com.br`** pelo endereço final do site. Ele aparece em 3 linhas, todas logo no começo do arquivo:

```html
<link rel="canonical" href="https://SEU-DOMINIO.com.br/">
<meta property="og:url"   content="https://SEU-DOMINIO.com.br/">
<meta property="og:image" content="https://SEU-DOMINIO.com.br/og-cover.png">
```

Se você usar o GitHub Pages, o endereço será algo como
`https://seuusuario.github.io/sessao-8rs` — use exatamente esse.

**Por que isso importa:** sem o endereço completo, o WhatsApp e o Instagram não conseguem carregar a imagem de prévia, e o link vai aparecer "pelado" para o lead.

---

## Publicar no GitHub Pages

1. Crie um repositório novo no GitHub (pode ser público). Sugestão de nome: `sessao-8rs`.
2. Envie os arquivos `index.html` e `og-cover.png` para a raiz do repositório
   (botão **Add file → Upload files**, arrasta e dá commit).
3. Vá em **Settings → Pages**.
4. Em *Source*, escolha **Deploy from a branch**; em *Branch*, escolha **main** e a pasta **/ (root)**. Salve.
5. Aguarde 1 a 2 minutos. O endereço aparece no topo dessa mesma tela.
6. Volte no `index.html`, troque o `SEU-DOMINIO` pelo endereço real e suba o arquivo de novo.

Pela linha de comando, se preferir:

```bash
git init
git add index.html og-cover.png
git commit -m "Formulário Sessão Estratégica 8Rs"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/sessao-8rs.git
git push -u origin main
```

Depois é só ativar o Pages em *Settings → Pages*.

---

## Alternativa sem repositório: Netlify Drop

Se você só quer o link no ar em 30 segundos:

1. Acesse **app.netlify.com/drop**.
2. Arraste a pasta inteira para a área indicada.
3. O link sai na hora (algo como `https://nome-aleatorio.netlify.app`).
4. Crie uma conta gratuita para renomear o endereço e ligar um domínio próprio.

A Vercel funciona do mesmo jeito, em **vercel.com/new**.

---

## Domínio próprio

Com um domínio na mão (ex.: `sessao.ideafoodservice.com.br`):

- **GitHub Pages:** *Settings → Pages → Custom domain*. Depois aponte um registro `CNAME` do subdomínio para `seuusuario.github.io` no painel do seu registrador.
- **Netlify / Vercel:** *Domain settings → Add domain* e siga o DNS que a plataforma indicar.

O HTTPS é emitido automaticamente nas três plataformas.

---

## Trocar o número do WhatsApp

No `index.html`, procure por `CONFIGURAÇÃO` (fica no bloco de script, perto do fim do arquivo):

```js
var WHATS = "5548999267960";
```

O formato é **DDI + DDD + número**, só dígitos, sem espaço, parêntese ou traço.
Se trocar o número, troque também no texto do painel de fallback e no `<noscript>`, que hoje mostram `(48) 99926-7960`.

---

## Rastreamento de conversão (opcional)

O formulário já dispara os eventos padrão quando o lead clica em enviar:

- Meta Pixel → `fbq('track', 'Lead')`
- Google Analytics 4 → `gtag('event', 'generate_lead')`

Para ativar, cole o código do pixel no espaço reservado dentro do `<head>` — está comentado e sinalizado como **RASTREAMENTO**. Se você não colar nada, o formulário funciona igual; os eventos simplesmente não disparam.

---

## Como as respostas chegam

Não existe banco de dados. Quando o lead completa o formulário e clica em enviar, o navegador abre o WhatsApp dele com a mensagem já formatada, endereçada ao seu número. Ele só aperta enviar.

Se o WhatsApp não abrir (bloqueador de pop-up, navegador dentro do Instagram), aparece um painel com as respostas e um botão **Copiar respostas**, mais o seu número para contato manual.

Quando o volume crescer e você quiser as respostas caindo direto numa planilha, dá para plugar o formulário num Google Sheets via Apps Script ou usar um serviço como o Formspree — aí passa a existir um registro além da conversa.

---

## Atualizar a imagem de prévia

Abra o `og-cover.html` no navegador, edite o texto direto no arquivo e capture a tela em 1200 × 630. Ou, com o Node instalado:

```bash
npx playwright screenshot --viewport-size=1200,630 og-cover.html og-cover.png
```

Depois de trocar a imagem, o WhatsApp pode continuar mostrando a antiga por causa do cache. Force a atualização no **Facebook Sharing Debugger** (`developers.facebook.com/tools/debug`), colando o link e clicando em *Scrape Again*.

---

## Identidade visual

A página segue o **Guia de Referência Visual da Plataforma IDEA (v1 · agosto 2026)**: paleta verde profundo com acento dourado, fundo radial com grid e grão, cartão em glassmorphism, e as três famílias tipográficas — Playfair Display nos títulos, Inter na interface, Montserrat nas etiquetas em caixa alta. As fontes vêm do Google Fonts; se você publicar num ambiente sem internet aberta, precisará hospedá-las junto.

**Pendências de marca:**

- O guia grafa o programa como *Mentoria 8R*; a página usa *8Rs*. Vale padronizar.
- O símbolo IDEA ainda não está aplicado — hoje a marca aparece só como texto. Com o PNG transparente em mãos, dá para colocá-lo acima do título.
