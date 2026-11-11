# Heroes Hub · Marvel

[![CI/CD](https://github.com/SEU-USUARIO/marvel-heroes-hub/actions/workflows/ci-cd.yml/badge.svg)](https://github.com/SEU-USUARIO/marvel-heroes-hub/actions/workflows/ci-cd.yml)
[![Licença MIT](https://img.shields.io/badge/licen%C3%A7a-MIT-ffc72c.svg)](LICENSE)
![Sem dependências](https://img.shields.io/badge/depend%C3%AAncias-0-3fb950.svg)

Catálogo, comparador e quiz de super-heróis da Marvel, feito com **HTML, CSS e JavaScript puro**. O foco é mostrar uma esteira de engenharia completa: código testado, Pull Requests com checks obrigatórios e deploy automático no GitHub Pages.

**Demo:** https://emilymayara256-web.github.io/marvel-heroes-hub/ · **Apresentação:** [slides](https://SEU-USUARIO.github.io/marvel-heroes-hub/slides/)

[![Assistir à apresentação do projeto](assets/videos/intro.jpg)](assets/videos/intro.mp4)

## O que tem aqui

| Recurso | Descrição |
| --- | --- |
| Catálogo | 12 heróis em 4 times, busca que ignora acentos, filtro por time e ficha detalhada |
| Comparador | Ranking dos 5 mais fortes e duelo de atributos entre quaisquer dois heróis |
| Quiz | 6 perguntas com feedback imediato e placar final |
| Slides | Apresentação navegável por teclado, toque e link direto (`slides/#3`) |
| Vídeos | Dois vídeos curtos gerados por código em `tools/make_videos.py` |
| CI/CD | Testes em todo push e PR, deploy no Pages a partir da `main` |

## A esteira

[![Esteira da Issue ao Release](assets/videos/pipeline.jpg)](assets/videos/pipeline.mp4)

1. Toda mudança começa em uma **Issue**.
2. Uma **branch** `feature/...` isola o trabalho.
3. **Commits** seguem Conventional Commits (`feat`, `fix`, `test`, `docs`, `ci`, `chore`).
4. O **Pull Request** dispara o job `test`; `build` e `deploy` só rodam na `main`.
5. A `main` é protegida: só recebe merge com o check `test` verde.
6. Marcos viram **Releases** com tags semânticas (`v1.0.0`).

## Como rodar

Requer Node 20+ e Python 3.

```bash
git clone https://github.com/SEU-USUARIO/marvel-heroes-hub.git
cd marvel-heroes-hub
npm test        # 12 testes com node:test
npm start       # http://localhost:8080
```

Para regenerar os vídeos (requer Pillow e ffmpeg): `python3 tools/make_videos.py`.

## Estrutura

```
.github/workflows/ci-cd.yml   test → build → deploy
index.html, quiz.html         páginas
css/                          estilos em camadas (base, catálogo, comparador, quiz, vídeos)
js/logic.js, quiz-logic.js    lógica pura, sem DOM
js/script.js, comparador.js, quiz.js   telas
js/heroes.js, questions.js    dados
slides/index.html             apresentação
tests/                        testes unitários
tools/                        build e gerador de vídeos
docs/PUBLICAR.md              passo a passo de publicação
```

## Decisões técnicas

- **Lógica separada da interface:** funções puras em `logic.js` e `quiz-logic.js` são testadas sem navegador.
- **Zero dependências:** `package.json` não tem pacotes; testes usam o runner nativo do Node.
- **Acessibilidade:** foco visível, `aria-live` nos resultados, texto com contraste calculado por cor e `prefers-reduced-motion` respeitado.
- **Atributos dos heróis** são estimativas de fã para fins didáticos, não valores oficiais.

## Roadmap

- [ ] Modo escuro/claro alternável
- [ ] Mais heróis e vilões
- [ ] Quiz com níveis de dificuldade

## Aviso

Projeto de portfólio sem fins comerciais, não afiliado à Marvel ou à Disney. Nomes e personagens pertencem aos seus respectivos donos. O código é licenciado sob a [MIT](LICENSE).
