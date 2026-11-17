# 🐜 Formigas de Langton — Painel de LED

Simulação da **Formiga de Langton** rodando direto no navegador, representada como um painel de LEDs que acendem e apagam.

Regras simplíssimas, comportamento surpreendentemente complexo.

> 🔗 **Demo:** `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`

---

## O que é

A Formiga de Langton é um **autômato celular**: um sistema em que regras locais muito simples, aplicadas repetidamente, geram padrões globais complexos.

Ela foi criada por **Christopher G. Langton** em **1986**, um dos fundadores da área de *Vida Artificial*.

## As regras

A cada passo, cada formiga:

1. Se está sobre um LED **apagado**, vira 90° à **direita** e o **acende**.
2. Se está sobre um LED **aceso**, vira 90° à **esquerda** e o **apaga**.
3. Avança uma casa na direção atual.

O mapa é **toroidal**: ao sair por uma borda, a formiga reaparece na borda oposta.

## O que observar

Com uma única formiga partindo do centro, o comportamento passa por três fases:

| Fase | Passos | Comportamento |
|------|--------|---------------|
| Simetria | primeiras centenas | Padrões simples e muitas vezes simétricos |
| Caos | até ~10 mil | O desenho parece totalmente aleatório |
| Estrada | a partir de ~10 mil | Ciclo periódico de 104 passos que constrói uma "estrada" diagonal infinita |

Curiosidade: nunca se provou que **toda** configuração inicial leva à estrada. É um problema em aberto.

## Funcionalidades

- 🟢 Painel de **300 × 200 LEDs**
- 🐜 **Várias formigas** simultâneas (padrão: 1)
- 🎨 **Cores únicas** por formiga: cada LED aceso mostra quem o acendeu, o que facilita estudar as interações quando elas se encontram
- 📍 **Posição inicial configurável**:
  - **Centro**: todas no meio, apontando para cima (comportamento clássico)
  - **Distribuída**: espalhadas uniformemente pelo painel, com direção sorteada
  - **Aleatória**: posição e direção sorteadas
- ⏯️ Pausar, continuar e reiniciar
- ⚡ Controle de velocidade (de 1 a 500 passos por quadro)
- 🚀 **Desenho incremental**: só os LEDs que mudam são redesenhados, para a animação continuar leve

## Como usar

Não precisa instalar nada.

**Localmente:** baixe o `index.html` e abra no navegador.

**Online:** ative o GitHub Pages em *Settings → Pages*, escolhendo a branch `main` e a pasta raiz.

Na interface:

1. Escolha a quantidade de formigas e o modo de posicionamento.
2. Clique em **Aplicar / Reiniciar**.
3. Ajuste a velocidade no controle deslizante.

## Configuração

No início do script, em `index.html`:

```js
const CELL = 4;    // tamanho de cada LED em pixels
const COLS = 300;  // LEDs na horizontal
const ROWS = 200;  // LEDs na vertical
```

## Como as cores são geradas

As cores não são sorteadas de forma independente, para que nunca se repitam. O primeiro matiz é aleatório, e cada formiga seguinte avança **137,5°** (o *ângulo de ouro*) no círculo cromático. Isso espalha as cores ao máximo. O brilho também alterna entre três níveis, para diferenciar ainda mais quando há muitas formigas.

## Estrutura

```
.
├── index.html   # simulação completa (HTML + CSS + JavaScript)
└── README.md
```

## Créditos

- Conceito original: **Christopher G. Langton** (1986)
- Mais informações: [Formiga de Langton — Wikipédia](https://pt.wikipedia.org/wiki/Formiga_de_Langton)

## Licença

Distribuído sob a licença MIT. Veja o arquivo `LICENSE`.