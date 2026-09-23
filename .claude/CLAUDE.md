# CLAUDE.md — Repositório `pages` (GitHub Pages público)

## Contexto
- Este repositório é **PÚBLICO** e serve GitHub Pages em https://developergustavor.github.io/pages/
- A raiz (`index.html`) é a **página índice**, com navegação (cards) para cada subpágina.
- Cada subpasta que contém um `index.html` é uma **subpágina roteável** (ex.: `andre-chaveiro-24h-recife/`, `lc-chaveiro-24h-recife/`).

## Regra obrigatória de roteamento
Sempre que houver **qualquer modificação nas subpastas** — adicionar uma nova subpasta com `index.html`, remover uma existente, renomear, ou mudar o título/descrição de uma subpágina — o `index.html` da raiz **DEVE ser atualizado** para refletir o roteamento **correto e completo**:

1. Todo `index.html` em subpasta de 1º nível deve ter **exatamente um card** correspondente na grade de navegação da raiz.
2. Não pode haver card apontando para subpasta que não existe mais (link quebrado), nem subpasta sem card (rota faltando).
3. O `href` do card aponta para a subpasta com barra final (ex.: `andre-chaveiro-24h-recife/`).
4. Título e descrição do card devem refletir o `<title>` e o `<meta name="description">` reais da subpágina.
5. O thumbnail do card deve usar uma imagem existente da subpasta (padrão atual: `assets/capa-rede-social.png`); se não existir, escolher outra imagem presente ou omitir a `<img>`.

### Como verificar (fonte da verdade)
Liste as subpáginas roteáveis e compare com os cards da raiz:
```
find . -mindepth 2 -maxdepth 2 -name index.html -not -path "./.git/*" | sort
```
Cada caminho listado precisa ter card correspondente no `index.html` da raiz, e vice-versa.

## Regra de privacidade (NÃO violar)
- **Propostas comerciais em PDF NUNCA entram neste repositório** (é público). Elas vivem no repositório **privado** `pages-purposes`.
- O `.gitignore` bloqueia `pages-purposes/`, `*proposta-comercial*` e `*proposta*.pdf`. Não remover essas regras.
- Antes de qualquer `git add`/commit/push, confirmar que nenhum arquivo de proposta/PDF sensível está sendo versionado:
  ```
  git diff --cached --name-only | grep -iE "proposta|pages-purposes|\.pdf" && echo ALERTA || echo OK
  ```
