# 🧬 Receita para recriar: Meu Chat

_Gerada sem IA, lendo 57 arquivo(s). Serve para remontar este app como HTML modular — com qualquer IA, um arquivo por vez._

## 1. O que é

- **Nome:** Meu Chat
- **Partes de código:** 46 (3 tela, 42 logica, 0 servidor, 0 dados, 1 estilo)
- **Tem servidor (rotas /api):** não — dá para ser só HTML
- **Peças de fora (bibliotecas):** fs, http, os, path, x

## 2. Estrutura modular proposta

```
index.html            ← a página; chama os módulos NA ORDEM
css/app.css           ← o visual
js/00-core.js         ← a "locomotiva": cria window.APP (registrar, guardar, avisar)
js/10-base.js         ← Meu Chat — 00-base.js: peças comuns (MC) (era ferramentas/meu-chat/js/00-base.js)
js/15-banco.js        ← Meu Chat — 10-banco.js: onde tudo fica guardado (IndexedDB do aparelho (era ferramentas/meu-chat/js/10-banco.js)
js/20-provedores.js   ← Meu Chat — 20-provedores.js: conversar com as IAs (Gemini, Groq, OpenR (era ferramentas/meu-chat/js/20-provedores.js)
js/25-memoria.js      ← Meu Chat — 30-memoria.js: 🧠 a memória que vai junto em TODA conversa. (era ferramentas/meu-chat/js/30-memoria.js)
js/30-contextos.js    ← Meu Chat — 33-contextos.js: 📌 CONTEXTOS — "cartões" de assunto que vo (era ferramentas/meu-chat/js/33-contextos.js)
js/35-jeito.js        ← Meu Chat — 35-jeito.js: 🎭 O JEITO DE CADA IA. Para não ter "mudança d (era ferramentas/meu-chat/js/35-jeito.js)
js/40-voz.js          ← Meu Chat — 40-voz.js: 🎤 falar (ditado) e 🔊 ouvir a resposta. 🔊 DOIS (era ferramentas/meu-chat/js/40-voz.js)
js/45-internet.js     ← Meu Chat — 50-internet.js: 🌐 pesquisar e 🔗 ler links. - Gemini e Cla (era ferramentas/meu-chat/js/50-internet.js)
js/50-previa.js       ← Meu Chat — 60-previa.js: 👁 ver o código funcionando, na hora. - HTML: (era ferramentas/meu-chat/js/60-previa.js)
js/55-texto.js        ← Meu Chat — 70-texto.js: mostra a resposta da IA bonitinha (negrito, li (era ferramentas/meu-chat/js/70-texto.js)
js/60-chat.js         ← Meu Chat — 80-chat.js: a conversa (mensagens, fotos, mandar, parar, li (era ferramentas/meu-chat/js/80-chat.js)
js/65-config.js       ← Meu Chat — 85-config.js: ⚙️ chaves das IAs, modelo, busca, voz, instru (era ferramentas/meu-chat/js/85-config.js)
js/70-cofre.js        ← Meu Chat — 87-cofre.js: 🔐 Cofre de chaves. Mostra cada chave guardada (era ferramentas/meu-chat/js/87-cofre.js)
js/75-backup.js       ← Meu Chat — 90-backup.js: 💾 backup de tudo (conversas + memória + ajus (era ferramentas/meu-chat/js/90-backup.js)
js/80-ponte-lab.js    ← 🔬 Ponte com o Laboratório: quando o Meu Chat está DENTRO do Laboratór (era ferramentas/meu-chat/js/95-ponte-lab.js)
js/85-cofre-arquivo.js← 🔐 Arquivo de chaves do Maikon — o MESMO formato no Mini SK, no Meu Ch (era ferramentas/meu-chat/js/lib/cofre-arquivo.js)
js/90-guia-maikon.js  ← 🧭 Guia das ferramentas do Maikon — o MESMO texto em todos os apps (Mi (era ferramentas/meu-chat/js/lib/guia-maikon.js)
js/91-voz-francisco.js← !/usr/bin/env python3 -*- coding: utf-8 -*- (era ferramentas/meu-chat/voz-francisco.py)
js/92-casca.js        ← js/00-casca.js (era js/00-casca.js)
js/93-importar.js     ← js/02-importar.js (era js/02-importar.js)
js/94-dependencias.js ← js/03-dependencias.js (era js/03-dependencias.js)
js/95-analisar.js     ← js/04-analisar.js (era js/04-analisar.js)
js/96-plano.js        ← js/05-plano.js (era js/05-plano.js)
js/97-05a-markdown.js ← js/05a-markdown.js (era js/05a-markdown.js)
js/98-scripts.js      ← js/06-scripts.js (era js/06-scripts.js)
js/98-06b-scripts-fim.js← js/06b-scripts-fim.js (era js/06b-scripts-fim.js)
js/98-terminal.js     ← js/07-terminal.js (era js/07-terminal.js)
js/98-07a-busca-npm.js← js/07a-busca-npm.js (era js/07a-busca-npm.js)
js/98-exportar.js     ← js/08-exportar.js (era js/08-exportar.js)
js/98-integracao.js   ← js/09-integracao.js (era js/09-integracao.js)
js/98-celular.js      ← js/10-celular.js (era js/10-celular.js)
js/98-lab-base.js     ← js/11-lab-base.js (era js/11-lab-base.js)
js/98-lab-mapa.js     ← js/12-lab-mapa.js (era js/12-lab-mapa.js)
js/98-lab-previa.js   ← js/13-lab-previa.js (era js/13-lab-previa.js)
js/98-lab-pesquisa.js ← js/14-lab-pesquisa.js (era js/14-lab-pesquisa.js)
js/98-lab-comparar.js ← js/15-lab-comparar.js (era js/15-lab-comparar.js)
js/98-15a-tar.js      ← js/15a-tar.js (era js/15a-tar.js)
js/98-lab-ferramentas.js← js/16-lab-ferramentas.js (era js/16-lab-ferramentas.js)
js/98-lab-termux.js   ← LABORATÓRIO 2 — 17-lab-termux.js · 💻 TERMINAL DE VERDADE (16/11) Troc (era js/17-lab-termux.js)
js/98-lab-desmontar.js← js/18-lab-desmontar.js (era js/18-lab-desmontar.js)
js/98-embutido.js     ← logica (era js/19-embutido.js)
js/98-colador.js      ← Colador de Links — 🔗 Colador de Links (era ferramentas/colador.html)
js/98-meu-chat.js     ← Meu Chat (era ferramentas/meu-chat/index.html)
js/98-inicio.js       ← 🔬 Laboratório 2 — 🔬 Laboratório 2 (era index.html)
js/99-app.js          ← o último: monta a tela com o que embarcou
```

## 3. As partes, uma por uma

| # | Era | Vira | Tipo | O que faz | Usa |
|---|---|---|---|---|---|
| 1 | `ferramentas/meu-chat/js/00-base.js` | `js/10-base.js` | logica | Meu Chat — 00-base.js: peças comuns (MC) | — |
| 2 | `ferramentas/meu-chat/js/10-banco.js` | `js/15-banco.js` | logica | Meu Chat — 10-banco.js: onde tudo fica guardado (IndexedDB do aparelho — não some ao fecha | — |
| 3 | `ferramentas/meu-chat/js/20-provedores.js` | `js/20-provedores.js` | logica | Meu Chat — 20-provedores.js: conversar com as IAs (Gemini, Groq, OpenRouter, OpenAI, DeepS | — |
| 4 | `ferramentas/meu-chat/js/30-memoria.js` | `js/25-memoria.js` | logica | Meu Chat — 30-memoria.js: 🧠 a memória que vai junto em TODA conversa. A IA guarda sozinha | — |
| 5 | `ferramentas/meu-chat/js/33-contextos.js` | `js/30-contextos.js` | logica | Meu Chat — 33-contextos.js: 📌 CONTEXTOS — "cartões" de assunto que você LIGA e DESLIGA. D | — |
| 6 | `ferramentas/meu-chat/js/35-jeito.js` | `js/35-jeito.js` | logica | Meu Chat — 35-jeito.js: 🎭 O JEITO DE CADA IA. Para não ter "mudança drástica" quando troc | — |
| 7 | `ferramentas/meu-chat/js/40-voz.js` | `js/40-voz.js` | logica | Meu Chat — 40-voz.js: 🎤 falar (ditado) e 🔊 ouvir a resposta. 🔊 DOIS "motores" de voz (⚙ | — |
| 8 | `ferramentas/meu-chat/js/50-internet.js` | `js/45-internet.js` | logica | Meu Chat — 50-internet.js: 🌐 pesquisar e 🔗 ler links. - Gemini e Claude pesquisam sozinh | — |
| 9 | `ferramentas/meu-chat/js/60-previa.js` | `js/50-previa.js` | logica | Meu Chat — 60-previa.js: 👁 ver o código funcionando, na hora. - HTML: abre a página como  | — |
| 10 | `ferramentas/meu-chat/js/70-texto.js` | `js/55-texto.js` | logica | Meu Chat — 70-texto.js: mostra a resposta da IA bonitinha (negrito, listas, links, blocos  | — |
| 11 | `ferramentas/meu-chat/js/80-chat.js` | `js/60-chat.js` | logica | Meu Chat — 80-chat.js: a conversa (mensagens, fotos, mandar, parar, lista de conversas). C | — |
| 12 | `ferramentas/meu-chat/js/85-config.js` | `js/65-config.js` | logica | Meu Chat — 85-config.js: ⚙️ chaves das IAs, modelo, busca, voz, instruções, tema | — |
| 13 | `ferramentas/meu-chat/js/87-cofre.js` | `js/70-cofre.js` | logica | Meu Chat — 87-cofre.js: 🔐 Cofre de chaves. Mostra cada chave guardada (👁 ver, 📋 copiar) | — |
| 14 | `ferramentas/meu-chat/js/90-backup.js` | `js/75-backup.js` | logica | Meu Chat — 90-backup.js: 💾 backup de tudo (conversas + memória + ajustes) e restaurar SEM | — |
| 15 | `ferramentas/meu-chat/js/95-ponte-lab.js` | `js/80-ponte-lab.js` | logica | 🔬 Ponte com o Laboratório: quando o Meu Chat está DENTRO do Laboratório (aba 🤖 IA), o La | — |
| 16 | `ferramentas/meu-chat/js/99-app.js` | css/app.css | logica | Meu Chat — 99-app.js: liga tudo quando abre | — |
| 17 | `ferramentas/meu-chat/js/lib/cofre-arquivo.js` | `js/85-cofre-arquivo.js` | logica | 🔐 Arquivo de chaves do Maikon — o MESMO formato no Mini SK, no Meu Chat e no que vier dep | — |
| 18 | `ferramentas/meu-chat/js/lib/guia-maikon.js` | `js/90-guia-maikon.js` | logica | 🧭 Guia das ferramentas do Maikon — o MESMO texto em todos os apps (Mini SK, Meu Chat…). A | — |
| 19 | `ferramentas/meu-chat/voz-francisco.py` | `js/91-voz-francisco.js` | logica | !/usr/bin/env python3 -*- coding: utf-8 -*- | — |
| 20 | `js/00-casca.js` | `js/92-casca.js` | logica | js/00-casca.js | — |
| 21 | `js/02-importar.js` | `js/93-importar.js` | logica | js/02-importar.js | — |
| 22 | `js/03-dependencias.js` | `js/94-dependencias.js` | logica | js/03-dependencias.js | ${url} |
| 23 | `js/04-analisar.js` | `js/95-analisar.js` | logica | js/04-analisar.js | — |
| 24 | `js/05-plano.js` | `js/96-plano.js` | logica | js/05-plano.js | — |
| 25 | `js/05a-markdown.js` | `js/97-05a-markdown.js` | logica | js/05a-markdown.js | — |
| 26 | `js/06-scripts.js` | `js/98-scripts.js` | logica | js/06-scripts.js | — |
| 27 | `js/06b-scripts-fim.js` | `js/98-06b-scripts-fim.js` | logica | js/06b-scripts-fim.js | — |
| 28 | `js/07-terminal.js` | `js/98-terminal.js` | logica | js/07-terminal.js | — |
| 29 | `js/07a-busca-npm.js` | `js/98-07a-busca-npm.js` | logica | js/07a-busca-npm.js | — |
| 30 | `js/08-exportar.js` | `js/98-exportar.js` | logica | js/08-exportar.js | — |
| 31 | `js/09-integracao.js` | `js/98-integracao.js` | logica | js/09-integracao.js | — |
| 32 | `js/10-celular.js` | `js/98-celular.js` | logica | js/10-celular.js | — |
| 33 | `js/11-lab-base.js` | `js/98-lab-base.js` | logica | js/11-lab-base.js | — |
| 34 | `js/12-lab-mapa.js` | `js/98-lab-mapa.js` | logica | js/12-lab-mapa.js | — |
| 35 | `js/13-lab-previa.js` | `js/98-lab-previa.js` | logica | js/13-lab-previa.js | — |
| 36 | `js/14-lab-pesquisa.js` | `js/98-lab-pesquisa.js` | logica | js/14-lab-pesquisa.js | — |
| 37 | `js/15-lab-comparar.js` | `js/98-lab-comparar.js` | logica | js/15-lab-comparar.js | — |
| 38 | `js/15a-tar.js` | `js/98-15a-tar.js` | logica | js/15a-tar.js | — |
| 39 | `js/16-lab-ferramentas.js` | `js/98-lab-ferramentas.js` | logica | js/16-lab-ferramentas.js | — |
| 40 | `js/17-lab-termux.js` | `js/98-lab-termux.js` | logica | LABORATÓRIO 2 — 17-lab-termux.js · 💻 TERMINAL DE VERDADE (16/11) Trocado pelo terminal AT | — |
| 41 | `js/18-lab-desmontar.js` | `js/98-lab-desmontar.js` | logica | js/18-lab-desmontar.js | — |
| 42 | `js/19-embutido.js` | `js/98-embutido.js` | logica | — | — |
| 43 | `ferramentas/colador.html` | `js/98-colador.js` | tela | Colador de Links — 🔗 Colador de Links | manifest.json |
| 44 | `ferramentas/meu-chat/css/app.css` | css/app.css | estilo | — | — |
| 45 | `ferramentas/meu-chat/index.html` | `js/98-meu-chat.js` | tela | Meu Chat | manifest.json, icon-192.png, app.css, 00-base.js |
| 46 | `index.html` | `js/98-inicio.js` | tela | 🔬 Laboratório 2 — 🔬 Laboratório 2 | jszip.min.js, pako.min.js, acorn.min.js, 00-casca.js |

## 4. Montar passo a passo (cada bloco é um pedido pronto: 📋 Copiar → colar na IA)

### Passo 0 — combinar as regras com a IA

```text
Vamos recriar o app "Meu Chat" como HTML MODULAR, que abre pelo index.html, sem servidor e sem nada da Replit.
Regras: (1) index.html chama os arquivos js/ na ordem, antes do </body>; (2) js/00-core.js cria window.APP com APP.registrar(modulo), APP.guardar(chave, valor) em IndexedDB/localStorage e APP.avisar(texto); (3) cada arquivo js/NN-nome.js cuida de UM assunto, começa com (function (APP) { e termina com })(window.APP); (4) js/99-app.js vem por último e monta a tela com os módulos registrados; (5) textos em português do Brasil.
Vou pedir UM arquivo por vez. Responda só com o arquivo completo, sem cortar nada. Primeiro: crie index.html, css/app.css e js/00-core.js.
```

### Passo 1 — `js/10-base.js` (era `ferramentas/meu-chat/js/00-base.js`, 43 linhas)

```text
Crie js/10-base.js. Ele faz: Meu Chat — 00-base.js: peças comuns (MC).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 2 — `js/15-banco.js` (era `ferramentas/meu-chat/js/10-banco.js`, 26 linhas)

```text
Crie js/15-banco.js. Ele faz: Meu Chat — 10-banco.js: onde tudo fica guardado (IndexedDB do aparelho — não some ao fechar).
No app original ele tinha estas funções/partes: abrir, req, loja.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 3 — `js/20-provedores.js` (era `ferramentas/meu-chat/js/20-provedores.js`, 225 linhas)

```text
Crie js/20-provedores.js. Ele faz: Meu Chat — 20-provedores.js: conversar com as IAs (Gemini, Groq, OpenRouter, OpenAI, DeepSeek, Claude). - Várias chaves; quando uma acaba (limite/cota), passa sozinho para a próxima ("revezar"). - Busca a lista de modelos de verdade na hora de testar a chave (nada de nome velho chumbado). - As chaves ficam SÓ neste aparelho.
No app original ele tinha estas funções/partes: detectar, procurarOllama, chaves, salvarChaves, pontoGemini, listarModelos, modeloDe, testarChave, erroLegivel, corsAviso, ehLimite, cabAnthropic, lerSSE, pedir, parcial, conversar.
Ele chamava estes endereços: http://127.0.0.1:11434/api/tags. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 4 — `js/25-memoria.js` (era `ferramentas/meu-chat/js/30-memoria.js`, 59 linhas)

```text
Crie js/25-memoria.js. Ele faz: Meu Chat — 30-memoria.js: 🧠 a memória que vai junto em TODA conversa. A IA guarda sozinha o que for importante escrevendo [[lembrar: …]] no fim da resposta (o app tira isso do texto, guarda e mostra "🧠 guardei"). [[esquecer: …]] apaga.
No app original ele tinha estas funções/partes: texto, salvar, lembrar, esquecer, aplicarMarcas, sistema, abrir.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 5 — `js/30-contextos.js` (era `ferramentas/meu-chat/js/33-contextos.js`, 178 linhas)

```text
Crie js/30-contextos.js. Ele faz: Meu Chat — 33-contextos.js: 📌 CONTEXTOS — "cartões" de assunto que você LIGA e DESLIGA. Diferente da 🧠 memória (que vale para sempre e vai em tudo): um contexto é o resumo de um assunto ou de uma conversa (por exemplo, o que você vinha fazendo com o Claude), para a IA não começar do zero. Ligado = vai junto em toda conversa. Desligado = fica guardado, sem gastar.
No app original ele tinha estas funções/partes: lista, gravar, semear, esconder, tokens, ligados, texto, pintarChip, pintar, novo, clique.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 6 — `js/35-jeito.js` (era `ferramentas/meu-chat/js/35-jeito.js`, 56 linhas)

```text
Crie js/35-jeito.js. Ele faz: Meu Chat — 35-jeito.js: 🎭 O JEITO DE CADA IA. Para não ter "mudança drástica" quando troca de IA: um jeito de conversar que vale para TODAS (parceiro, calmo, honesto) e, se quiser, um jeito só de uma (ex.: o Perplexity como pesquisador jurídico que sempre traz as fontes). Tudo editável em ⚙️ → 🎭 Jeito de cada IA.
No app original ele tinha estas funções/partes: geral, deUma, texto, pintar.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 7 — `js/40-voz.js` (era `ferramentas/meu-chat/js/40-voz.js`, 219 linhas)

```text
Crie js/40-voz.js. Ele faz: Meu Chat — 40-voz.js: 🎤 falar (ditado) e 🔊 ouvir a resposta. 🔊 DOIS "motores" de voz (⚙️ → Voz): - 📱 "Voz do aparelho" (o padrão): funciona com QUALQUER IA (Gemini, Groq, Claude, Ollama…), grátis e sem limite. Você escolhe a voz (as ⭐ são as naturais), a velocidade e o tom.
No app original ele tinha estas funções/partes: podeOuvir, ouvir, parar, marcar, paraFala, pedacos, noPC, motor, temAndroid, temNavegador, natural, vozesAparelho, cfgVoz, falarFrase, enfileirar, verificarFim, pararAparelho, fluxo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 8 — `js/45-internet.js` (era `ferramentas/meu-chat/js/50-internet.js`, 58 linhas)

```text
Crie js/45-internet.js. Ele faz: Meu Chat — 50-internet.js: 🌐 pesquisar e 🔗 ler links. - Gemini e Claude pesquisam sozinhos (a busca vem embutida neles). - As outras IAs: usa a SUA chave de busca (Serper, Tavily ou Brave), se tiver, e manda os resultados junto. - Link na mensagem: o app lê a página (pelo leitor r.jina.ai, grátis) e manda o texto para a IA.
No app original ele tinha estas funções/partes: buscar, lerLink, preparar.
Ele chamava estes endereços: https://google.serper.dev/search, https://api.tavily.com/search, https://api.search.brave.com/res/v1/web/search?count=8&country=BR&search_lang=pt-br&q=, https://r.jina.ai/. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 9 — `js/50-previa.js` (era `ferramentas/meu-chat/js/60-previa.js`, 72 linhas)

```text
Crie js/50-previa.js. Ele faz: Meu Chat — 60-previa.js: 👁 ver o código funcionando, na hora. - HTML: abre a página como ela é. - TSX / JSX (React): monta com React + Babel + Tailwind (pela internet) e mostra o componente. Os erros aparecem embaixo, em vermelho.
No app original ele tinha estas funções/partes: paginaHTML, paginaReact, falha, req, App, tipoDe, abrir.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 10 — `js/55-texto.js` (era `ferramentas/meu-chat/js/70-texto.js`, 45 linhas)

```text
Crie js/55-texto.js. Ele faz: Meu Chat — 70-texto.js: mostra a resposta da IA bonitinha (negrito, listas, links, blocos de código com 📋 copiar, ⤓ baixar e 👁 ver funcionando).
No app original ele tinha estas funções/partes: inline, render, ligar.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 11 — `js/60-chat.js` (era `ferramentas/meu-chat/js/80-chat.js`, 250 linhas)

```text
Crie js/60-chat.js. Ele faz: Meu Chat — 80-chat.js: a conversa (mensagens, fotos, mandar, parar, lista de conversas). Cada conversa fica guardada no aparelho. Vai para a IA: a memória + as últimas mensagens.
No app original ele tinha estas funções/partes: nova, abrirConversa, guardar, reduzir, anexar, pintarAnexos, htmlMsg, dedup, hora, pintar, mandar, responder, depois, comparar, juntar, tela, escolherComparar, resumirSePrecisar.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 12 — `js/65-config.js` (era `ferramentas/meu-chat/js/85-config.js`, 106 linhas)

```text
Crie js/65-config.js. Ele faz: Meu Chat — 85-config.js: ⚙️ chaves das IAs, modelo, busca, voz, instruções, tema.
No app original ele tinha estas funções/partes: opcoesVoz, pintar, clique, mudou, aplicarTema, abrir.
Ele chamava estes endereços: voz-francisco.py. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 13 — `js/70-cofre.js` (era `ferramentas/meu-chat/js/87-cofre.js`, 89 linhas)

```text
Crie js/70-cofre.js. Ele faz: Meu Chat — 87-cofre.js: 🔐 Cofre de chaves. Mostra cada chave guardada (👁 ver, 📋 copiar) e leva SÓ as chaves para outro app/aparelho num arquivo trancado com senha — o mesmo arquivo do Mini SK (js/lib/cofre-arquivo.js).
No app original ele tinha estas funções/partes: todas, pintar, status, conteudo, baixar, trazer.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 14 — `js/75-backup.js` (era `ferramentas/meu-chat/js/90-backup.js`, 44 linhas)

```text
Crie js/75-backup.js. Ele faz: Meu Chat — 90-backup.js: 💾 backup de tudo (conversas + memória + ajustes) e restaurar SEM APAGAR NADA.
No app original ele tinha estas funções/partes: gerar, baixar, restaurar.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 15 — `js/80-ponte-lab.js` (era `ferramentas/meu-chat/js/95-ponte-lab.js`, 20 linhas)

```text
Crie js/80-ponte-lab.js. Ele faz: 🔬 Ponte com o Laboratório: quando o Meu Chat está DENTRO do Laboratório (aba 🤖 IA), o Laboratório pode mandar texto para a caixa de escrever (o plano do projeto, a memória, a comparação A × B). Só aceita mensagens da própria página (mesmo endereço).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 16 — `js/85-cofre-arquivo.js` (era `ferramentas/meu-chat/js/lib/cofre-arquivo.js`, 61 linhas)

```text
Crie js/85-cofre-arquivo.js. Ele faz: 🔐 Arquivo de chaves do Maikon — o MESMO formato no Mini SK, no Meu Chat e no que vier depois. Guarda SÓ as chaves (IA, GitHub, Expo, pesquisa e "Minhas chaves"), trancadas com uma senha sua (AES-GCM 256 + PBKDF2 com 250 mil voltas — sem a senha, o arquivo não abre). Assim dá para levar as chaves de um app/aparelho para outro sem passar pelo WhatsApp.
No app original ele tinha estas funções/partes: b64, deB64, chaveDaSenha, normal, selar, abrir, contar, mascara.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 17 — `js/90-guia-maikon.js` (era `ferramentas/meu-chat/js/lib/guia-maikon.js`, 117 linhas)

```text
Crie js/90-guia-maikon.js. Ele faz: 🧭 Guia das ferramentas do Maikon — o MESMO texto em todos os apps (Mini SK, Meu Chat…). A IA de cada app lê isto sozinha: assim ela já sabe o que ele tem, para que serve cada coisa, e quando é melhor mandar para outra ferramenta ou "levar para o Claude". Para atualizar: troque este arquivo nos apps (o Claude manda a versão nova junto).
No app original ele tinha estas funções/partes: resumoParaClaude, esconder.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 18 — `js/91-voz-francisco.js` (era `ferramentas/meu-chat/voz-francisco.py`, 134 linhas)

```text
Crie js/91-voz-francisco.js. Ele faz: !/usr/bin/env python3 -*- coding: utf-8 -*-.
No app original ele tinha estas funções/partes: _listar, _falar, Voz, _cabecalhos, do_OPTIONS, _json, _pedido, do_GET, do_POST, _tratar, log_message.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 19 — `js/92-casca.js` (era `js/00-casca.js`, 328 linhas)

```text
Crie js/92-casca.js. Ele faz: js/00-casca.js.
No app original ele tinha estas funções/partes: Shell, triggerAutoSave, restoreSession, navigate, openTab, activateTab, closeTab, renderTabs, toast, openModal, closeModal, updateStatusBar, updateBadges, updateSidebarInfo, startClock, tick, checkPreviousSession, setState.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 20 — `js/93-importar.js` (era `js/02-importar.js`, 746 linhas)

```text
Crie js/93-importar.js. Ele faz: js/02-importar.js.
No app original ele tinha estas funções/partes: loadLibs, Importer, getIcon, isTextFile, formatSize, showProgress, logProgress, hideProgress, initDropZone, openFolderPicker, openFilePicker, processFolderFiles, processFiles, processZip, processTar, parseTar, readTarString, processGz.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 21 — `js/94-dependencias.js` (era `js/03-dependencias.js`, 733 linhas)

```text
Crie js/94-dependencias.js. Ele faz: js/03-dependencias.js.
No app original ele tinha estas funções/partes: DepsAnalyzer, translateDesc, classifyDep, getCDNTag, hasCDN, analyze, addDep, renderSummary, setText, renderPkgTabs, setPkg, setFilter, filterDeps, renderDeps, renderDepCard, labelRelevance, showToolbar, showMonorepoBanner.
Ele chamava estes endereços: https://registry.npmjs.org/${dep.name}/latest, https://registry.npmjs.org/${name}/latest. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 22 — `js/95-analisar.js` (era `js/04-analisar.js`, 816 linhas)

```text
Crie js/95-analisar.js. Ele faz: js/04-analisar.js.
No app original ele tinha estas funções/partes: CodeAnalyzer, analyze, detectFrameworks, detectBugs, detectConsoleLogs, detectRoutes, buildStructureMap, renderSummary, setText, renderFrameworks, renderBugs, labelBugType, setBugFilter, renderConsoleLogs, renderRoutes, renderRoutesPanel, routeCardHTML, setRouteFilter.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 23 — `js/96-plano.js` (era `js/05-plano.js`, 717 linhas)

```text
Crie js/96-plano.js. Ele faz: js/05-plano.js.
No app original ele tinha estas funções/partes: Planner, setPlanType, toggleSection, setProgress, hideProgress, tick, generate, genOverview, genTech, genStructure, genDeps, row, genRoutes, genBugs, genModules, renderModulesMD, genSteps, genSetupScripts.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 24 — `js/97-05a-markdown.js` (era `js/05a-markdown.js`, 70 linhas)

```text
Crie js/97-05a-markdown.js. Ele faz: js/05a-markdown.js.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 25 — `js/98-scripts.js` (era `js/06-scripts.js`, 752 linhas)

```text
Crie js/98-scripts.js. Ele faz: js/06-scripts.js.
No app original ele tinha estas funções/partes: ScriptGen, toggleOpt, setTab, generate, collectDirs, collectKeyFiles, genBAT, genSH, genPS1, genMakefile, dirs_for_make, buildPackageJSON, buildGitignore, buildEnvExample, renderScript, highlightScript.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 26 — `js/98-06b-scripts-fim.js` (era `js/06b-scripts-fim.js`, 188 linhas)

```text
Crie js/98-06b-scripts-fim.js. Ele faz: js/06b-scripts-fim.js.
No app original ele tinha estas funções/partes: patchScriptGen, highlightScript, copyScript, downloadBAT, downloadSH, downloadPS1, downloadMakefile, downloadAll, _dl.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 27 — `js/98-terminal.js` (era `js/07-terminal.js`, 784 linhas)

```text
Crie js/98-terminal.js. Ele faz: js/07-terminal.js.
No app original ele tinha estas funções/partes: Terminal, initEnv, handleKey, runInput, runCmd, cmdHelp, cmdClear, cmdLs, cmdPwd, cmdCd, cmdCat, cmdEcho, cmdNode, cmdNpm, cmdNpx, cmdGit, cmdEnv, cmdWhoami.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 28 — `js/98-07a-busca-npm.js` (era `js/07a-busca-npm.js`, 168 linhas)

```text
Crie js/98-07a-busca-npm.js. Ele faz: js/07a-busca-npm.js.
No app original ele tinha estas funções/partes: NpmSearch, search, renderResults, translateDesc, install, setupLiveSearch.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 29 — `js/98-exportar.js` (era `js/08-exportar.js`, 774 linhas)

```text
Crie js/98-exportar.js. Ele faz: js/08-exportar.js.
No app original ele tinha estas funções/partes: Exporter, updateSummary, setProgress, hideProgress, tick, addHistory, renderHistory, exportPlan, copyPlan, exportBugs, copyBugs, exportDeps, exportDepsJSON, copyDeps, exportRoutes, exportRoutesJSON, copyRoutes, exportStructure.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 30 — `js/98-integracao.js` (era `js/09-integracao.js`, 653 linhas)

```text
Crie js/98-integracao.js. Ele faz: js/09-integracao.js.
No app original ele tinha estas funções/partes: Integration, init, updateClock, updateStatusBar, setupKeyboardShortcuts, setupGlobalDrop, showDropOverlay, hideDropOverlay, setupStateWatcher, onStateChange, markFlowDone, updateWelcomeFlow, updateBugBadge, patchShellToast, showToast, closeToast, patchShellBadges, patchShellNavigate.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 31 — `js/98-celular.js` (era `js/10-celular.js`, 20 linhas)

```text
Crie js/98-celular.js. Ele faz: js/10-celular.js.
No app original ele tinha estas funções/partes: celular, alternar.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 32 — `js/98-lab-base.js` (era `js/11-lab-base.js`, 149 linhas)

```text
Crie js/98-lab-base.js. Ele faz: js/11-lab-base.js.
No app original ele tinha estas funções/partes: ehBinario, arquivos, binarios, lista, tipo, pasta, normalizar, raizComum, resolver, raizDoArquivo, resolverApelido, achar, tem, nomePacote, referencias, add, refsJS, mapa.
O original usava as bibliotecas x: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 33 — `js/98-lab-mapa.js` (era `js/12-lab-mapa.js`, 148 linhas)

```text
Crie js/98-lab-mapa.js. Ele faz: js/12-lab-mapa.js.
No app original ele tinha estas funções/partes: tela, listar, detalhe, link, arvore, extrair, mermaid, relatorio, verCodigo, desmontar, previa, pesquisar, ver.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 34 — `js/98-lab-previa.js` (era `js/13-lab-previa.js`, 288 linhas)

```text
Crie js/98-lab-previa.js. Ele faz: js/13-lab-previa.js.
No app original ele tinha estas funções/partes: pegarConversor, temJSX, urlPacote, blobURL, urlBinario, urlDe, prepararJS, reescreverImports, ehTailwindCSS, prepararCSS, montarPagina, candidatos, tela, listarExtras, mostrarLog, mostrarConsole, rodar, rodarColado.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 35 — `js/98-lab-pesquisa.js` (era `js/14-lab-pesquisa.js`, 160 linhas)

```text
Crie js/98-lab-pesquisa.js. Ele faz: js/14-lab-pesquisa.js.
No app original ele tinha estas funções/partes: mil, json, enc, semInternet, dados, pesquisar, info, cdn, comparar, col, linha, alternativas, substitutos, ajuda.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 36 — `js/98-lab-comparar.js` (era `js/15-lab-comparar.js`, 208 linhas)

```text
Crie js/98-lab-comparar.js. Ele faz: js/15-lab-comparar.js.
No app original ele tinha estas funções/partes: diff, norm, trechos, htmlDiff, mdDiff, tela, opcoes, entrada, mostrar, arquivos, colados, semTopo, projetos, textoMD, baixarMD, copiarMD.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 37 — `js/98-15a-tar.js` (era `js/15a-tar.js`, 45 linhas)

```text
Crie js/98-15a-tar.js. Ele faz: js/15a-tar.js.
No app original ele tinha estas funções/partes: ehTar, descompactar, texto, octal, abrir.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 38 — `js/98-lab-ferramentas.js` (era `js/16-lab-ferramentas.js`, 83 linhas)

```text
Crie js/98-lab-ferramentas.js. Ele faz: js/16-lab-ferramentas.js.
No app original ele tinha estas funções/partes: bytes, tela, cartao, achar, abrirAqui, telaPropria, kit.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 39 — `js/98-lab-termux.js` (era `js/17-lab-termux.js`, 379 linhas)

```text
Crie js/98-lab-termux.js. Ele faz: LABORATÓRIO 2 — 17-lab-termux.js · 💻 TERMINAL DE VERDADE (16/11) Trocado pelo terminal ATUAL do Laboratório (o que não cai): ▶ Ligar tudo · 🚀 Rodar · ⏹ Parar · 🦙 Ollama · 🗣 Voz Francisco · 🧰 Verificar e instalar · 🩺 Terminal parado? - No celular: Termux (ttyd ws://127.0.0.1:7681/ws + ponte de arquivos 7683).
No app original ele tinha estas funções/partes: espera, status, pst, carregarScript, carregarCss, prepararTela, escreverTela, enviar, tamanho, ligado, conectar, desconectar, copiar, nome, dentro, responder, corpo, andar.
O original usava as bibliotecas http, fs, path, os: em HTML puro, use a versão de CDN (ou faça sem ela, se for simples).
Ele chamava estes endereços: ferramentas/meu-chat/voz-francisco.py. Em HTML, ligue cada um à função equivalente do módulo certo.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 40 — `js/98-lab-desmontar.js` (era `js/18-lab-desmontar.js`, 462 linhas)

```text
Crie js/98-lab-desmontar.js. Ele faz: js/18-lab-desmontar.js.
No app original ele tinha estas funções/partes: comPonte, explicar, lerJS, ehBiblioteca, nomesDoTopo, analisar, linhaDe, slug, picar, pad, nomeDoPedaco, dividirScript, secaoDe, pedaco, agrupar, rodarEm, ouvir, plano.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 41 — `js/98-embutido.js` (era `js/19-embutido.js`, 2 linhas)

```text
Crie js/98-embutido.js. Ele é uma parte de logica do app.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 42 — `js/98-colador.js` (era `ferramentas/colador.html`, 797 linhas)

```text
Crie js/98-colador.js. Ele faz: Colador de Links — 🔗 Colador de Links.
No app original ele tinha estas funções/partes: uid, ler, gravar, nomeLista, nomeDe, pintar, fixar, tirar, mover, recarregar, pintarJanela, iniciar, montar, salvar, daLista, contar, pintarListas, caixaDe.
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 43 — `js/98-meu-chat.js` (era `ferramentas/meu-chat/index.html`, 102 linhas)

```text
Crie js/98-meu-chat.js. Ele faz: Meu Chat.
Ele usa o que já foi criado em: js/10-base.js, js/15-banco.js, js/20-provedores.js, js/25-memoria.js, js/30-contextos.js, js/35-jeito.js, js/40-voz.js, js/45-internet.js, js/50-previa.js, js/55-texto.js, js/60-chat.js, js/85-cofre-arquivo.js, js/90-guia-maikon.js, js/65-config.js, js/70-cofre.js, js/75-backup.js, js/80-ponte-lab.js (pelo APP).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 44 — `js/98-inicio.js` (era `index.html`, 4113 linhas)

```text
Crie js/98-inicio.js. Ele faz: 🔬 Laboratório 2 — 🔬 Laboratório 2.
Ele usa o que já foi criado em: js/92-casca.js, js/93-importar.js, js/94-dependencias.js, js/95-analisar.js, js/97-05a-markdown.js, js/96-plano.js, js/98-scripts.js, js/98-06b-scripts-fim.js, js/98-07a-busca-npm.js, js/98-terminal.js, js/98-exportar.js, js/98-integracao.js, js/98-celular.js, js/98-lab-base.js, js/98-lab-mapa.js, js/98-lab-previa.js, js/98-lab-pesquisa.js, js/98-15a-tar.js, js/98-lab-comparar.js, js/98-lab-ferramentas.js, js/98-lab-termux.js, js/98-lab-desmontar.js, js/98-embutido.js (pelo APP).
Registre com APP.registrar({ nome, icone, abrir }). Devolva só o arquivo completo.
```

### Passo 45 — `js/99-app.js` e conferir

```text
Crie js/99-app.js: ele olha APP.modulos e monta o menu/abas com um botão para cada módulo. Depois, me mande o index.html atualizado com todos os <script src="js/…"> na ordem certa: js/00-core.js, js/10-base.js, js/15-banco.js, js/20-provedores.js, js/25-memoria.js, js/30-contextos.js, js/35-jeito.js, js/40-voz.js, js/45-internet.js, js/50-previa.js, js/55-texto.js, js/60-chat.js, js/65-config.js, js/70-cofre.js, js/75-backup.js, js/80-ponte-lab.js, js/85-cofre-arquivo.js, js/90-guia-maikon.js, js/91-voz-francisco.js, js/92-casca.js, js/93-importar.js, js/94-dependencias.js, js/95-analisar.js, js/96-plano.js, js/97-05a-markdown.js, js/98-scripts.js, js/98-06b-scripts-fim.js, js/98-terminal.js, js/98-07a-busca-npm.js, js/98-exportar.js, js/98-integracao.js, js/98-celular.js, js/98-lab-base.js, js/98-lab-mapa.js, js/98-lab-previa.js, js/98-lab-pesquisa.js, js/98-lab-comparar.js, js/98-15a-tar.js, js/98-lab-ferramentas.js, js/98-lab-termux.js, js/98-lab-desmontar.js, js/98-embutido.js, js/98-colador.js, js/98-meu-chat.js, js/98-inicio.js, js/99-app.js.
```

## 5. Conferir no final

- [ ] Abrir o index.html na prévia: aparece a tela sem erro (▤ console vazio)?
- [ ] Cada botão abre a sua parte?
- [ ] Fechar e abrir de novo: os dados continuam?
- [ ] Nada com "replit", "REPL_", "@workspace" no código (🏗️ Preparar confere).
- [ ] 📱 PWA → deixar instalável; 📦 APK ou 🖥️ .exe.
