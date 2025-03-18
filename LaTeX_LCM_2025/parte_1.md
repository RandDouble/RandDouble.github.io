<!-- <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.2/css/bootstrap.min.css">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.4/styles/monokai_sublime.min.css">
<script src="https://code.jquery.com/jquery-2.1.3.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.4/highlight.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.4/languages/javascript.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.4/languages/php.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.4/languages/sql.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.4/languages/xml.min.js"></script>

<style>body { padding: 20px } pre { padding: 0 }</style>

<script>
$(function() {
    $("pre > code").each(function(i, block) {
        var codeClass = $(this).parent().attr("class");
        if (codeClass == null || codeClass === "") {
            $(this).addClass("hljs");
        } else {
            var map = {
                js: "javascript"
            };
            if (map[codeClass]) {
                codeClass = map[codeClass];
            }
            $(this).addClass(codeClass);
            hljs.highlightBlock(this);
        }
    });
});
</script> -->


<link rel="stylesheet" href="dependencies/highlightjs/styles/monokai-sublime.css">
<script src="dependencies/highlightjs//highlight.min.js"></script>

<script>hljs.highlightAll();</script>


 <!-- KaTeX -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.21/dist/katex.min.css" integrity="sha384-zh0CIslj+VczCZtlzBcjt5ppRcsAmDnRem7ESsYwWwg3m/OaJ2l4x7YBZl9Kxxib" crossorigin="anonymous">

<!-- The loading of KaTeX is deferred to speed up page rendering -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.21/dist/katex.min.js" integrity="sha384-Rma6DA2IPUwhNxmrB/7S3Tno0YY7sFu9WSYMCuulLhIqYSGZ2gKCJWIqhBWqMQfh" crossorigin="anonymous"></script>

<!-- To automatically render math in text elements, include the auto-render extension: -->
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.21/dist/contrib/auto-render.min.js" integrity="sha384-hCXGrW6PitJEwbkoStFjeJxv+fSOOQKOPbJxSfM6G5sWZjAyWhXiTIIAmQqnlLlh" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>


---
author: '`Stefano Pilosio`'
title: '`\begin{easy}`'
subtitle: Corso LaTeX LCM
date: 17 Marzo 2025
width: 1500
---

# Storia

## In principio era TeX,

::: {.container}
:::: {.col}
- 1977, Knuth inizia a scrivere la sua opera magna _The Art of Computer Programming_.
- 1982, Nasce Tex, rivisto l'ultima volta nel 2014, con la versione 3.14159264.
::::
:::: {.col}
![D.E. Knuth](images/Donald_Ervin_Knuth_(cropped).jpg){height=450px}
::::
:::



## E poi LaTeX

::: {.container}
:::: {.col}
Leslie Lamport inizia a creare delle macro per TeX nel 1978:

**LaTeX = La(mport)TeX**

Oltre a questo scrive anche il primo manuale per LaTeX:

_LaTeX: A Document Preparation System_

::::
:::: {.col}
![Leslie Lamport](images/Leslie_Lamport.jpg){height=450px}
::::
:::

## Ma alla fine cosa è LaTeX?

Un linguaggio *compilato specializzato* per la tipografia e la scrittura di documenti secondo il paradigma  WYSIWYM (_What You See Is What You Mean_).

In breve è un linguaggio di MarkUp.

## Pro e Contro

::: {.container}
:::: {.col}

#### PRO {-}

- Testo lungo e strutturato;
- Serve coerenza interna al testo;
- Molta matematica;
- Molte tabelle, immagini e reference;

::::
:::: {.col}

#### CONTRO {-}

- Non è adatto se il testo da preparare è piccolo;
- Non è adatto se è più importante l'aspetto visivo del contenuto;
- Non si è a proprio agio a scrivere codice.

::::
:::

# Tools


## Compilatore

Esistono tre varianti principali di compilatore latex:

- PdfLaTeX (Più comune, nato con supporto diretto a PDF)
- XeLaTeX (Riscrittura completa del motore, nato per gestire i caratteri Unicode)
- LuaHBLaTeX (Si ispira a PdfLaTeX, aggiunge unicode e LUA)

## Distribuzioni

Ne esistono varie, le più comuni sono:

- TeX Live ( Windows e Linux )
- MikTeX ( Windows )
- MacTeX (Mac Os X )

## Editor di testo

- [Visual Studio Code](https://code.visualstudio.com/) + [Latex Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
- [Overleaf](https://it.overleaf.com/)
- LyX
- TeXStudio
- TeXworks
- Emacs

## Come è strutturato il testo

```latex
% Preambolo
\documentclass[a4paper]{article}
\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[italian]{babel}

% Corpo del testo
\begin{document}
Ecco il mio primo documento con \LaTeX.
% Amo scrivere avendo una tazza di caffè a lato.
\end{document}
```

# Classi di Documento

---

Ne esistono di vari tipi:

- `article` per gli articoli 
- `report` per i report
- `book` per i libri
- `letter` per le lettere
- `beamer` per presentazioni

---

Supportano varie opzioni:

- `10pt, 11pt, 12pt` (Default: `10pt`)
- `a4paper, letterpaper`
- `oneside, twoside` (Nr. di facciate)
- `draft, final` Influenzano comportamento
- `twocolumn`

## Sezionamento del documento

Il sistema è basato sul sistema inglese:

0. `part` (Non influenza la numerazione del capitolo)
0. `chapter` (capitolo)
0. `section` (Paragrafo)
0. `subsection`
0. `subsubsection`

Sotto non vale la pena scendere.

## Titolo

La parte più importante di un lavoro:

```latex
\title{Come produrre un buon caffè}
\author{ LCM Admin \and Nirvana}
\date{\today}

\begin{document}
\maketitle
\end{document}
```

> Il risultato dipende dalla `documentclass` scelta

# Contenuto del testo

---

Adesso arriva la parte clue, stiamo scrivendo il nostro testo, ci accorgiamo che vogliamo fare qualche cosa di particolare, ci servono degli "ambienti".

---

### SINTASSI {-}

```latex
\begin{ambiente}
Contenuto
\end{ambiente}
```
---

## Ambienti di base

---

Con gli elenchi possiamo fare:

- Elenchi Puntati
- Elenchi Numerati
- Centrare il testo
- *Scrivere formule matematiche*
- Scrivere Teoremi

---

##### Elenchi Puntati {-}

::: {.container}
:::: {.col}
```latex
\begin{itemize}
\item Caffè Moka
\item Caffè Espresso
\item Caffè Macchiato
\end{itemize}
```
::::
:::: {.col}

- Caffè Moka
- Caffè Espresso
- Caffè Macchiato

::::
:::

##### Elenchi Numerati {-}

::: {.container}
:::: {.col}
```latex
\begin{enumerate}
\item Caffè Moka
\item Caffè Espresso
\item Caffè Macchiato
\end{enumerate}
```
::::
:::: {.col}

1. Caffè Moka
1. Caffè Espresso
1. Caffè Macchiato

::::
:::

---

##### Descrizioni {-}

::: {.container}
:::: {.col}
```latex
\begin{description}
\item[itemize] Per gli
elenchi puntati.
\item[enumerate] Per gli
elenchi numerati.
\item[description] Per g.li elenchi
in cui ogni elemento comincia
con un testo a piacere.
\end{description}
```
::::
:::: {.col}

*itemize* 
: Per gli elenchi puntati.

*enumerate*
:  Per gli elenchi numerati.

*description*
:  Per gli elenchi in cui ogni elemento cominchia con un testo a piacere.


::::
:::

---

##### Citazioni {-}

Intendiamo citazioni riportate, non è il tipico genere di citazione trovata nei testi scientifici.
Se ne possono fare di due tipi:

- In linea.
- In Display.

---

###### IN LINEA {-}

::: {.container}

:::: {.col}
```latex
Che bella che era la pubblicità: <<Il buongiorno si vede dal caffè>>
```
::::

:::: {.col}
Che bella che era la pubblicità: "Il buongiorno si vede dal caffè"
::::

:::

---

###### IN DISPLAY {-}

Tre possibili ambienti: `quote`, `quotation` e *`quoting`*

::: {.container}
:::: {.col}
```latex
% Preambolo
\usepackage{quoting}
\quotingsetup{font=small}

% Corpo

Una citazione è un testo che compone linee a sè:

\begin{quoting}
Il mattino si vede dal caffè.
\end{quoting}


```
::::
:::: {.col}

Una citazione è un testo che compone linee a sè:

> Il mattino si vede dal caffè.

::::
:::

---

## Ambienti scientifici

---

A un fisico generalmente serve avere a disposizione la possibilità di scrivere in maniera semplice tre cose:

1. Matematica
1. Enunciati di Teoremi con dimostrazioni
1. Codice

Oltre a questo in generale si aggiungono la possibilità di aggiungere:

1. Grafici e immagini
1. Tabelle
1. Schemi (Avanzato)

# Scrivere Matematica

---

È forse la feature più nota di Latex, tant'è che viene replicata anche in altri editor e linguaggi di markup tramite engines
(e.g. MathJax, KaTeX)

---

#### In Linea {-}

::: {.container}

:::: {.col}

```latex
L'energia associata alla massa a riposo secondo Einstein è $E=mc^2$ 
```

::::

:::: {.col}

L'energia associata alla massa a riposo secondo Einstein è $E=mc^2$

::::

:::

---

#### In  Display {-}

::: {.container}
:::: {.column}
```latex
\begin{equation}
\lim_{n\to\infty} \sum_{k=1}^{n} \frac{1}{k^2} = \frac{\pi^2}{6}
\end{equation}
```
::::


:::: {.column}
$$
\begin{equation}
\lim_{n\to\infty} \sum_{k=1}^{n} \frac{1}{k^2} = \frac{\pi^2}{6}
\end{equation}
$$
::::
:::

::: {.container}
:::: {.column}
```latex
\begin{equation*}
\lim_{n\to\infty} \sum_{k=1}^{n} \frac{1}{k^2} = \frac{\pi^2}{6}
\end{equation*}
```
::::


:::: {.column}
$$
\lim_{n\to\infty} \sum_{k=1}^{n} \frac{1}{k^2} = \frac{\pi^2}{6}
$$
::::
:::

---

#### Greek Letters {-}

| Greek Letter | Lowercase | Greek Letter | Lowercase |
|--------------|-------------|--------------|--------------|
| $\alpha$        | `$\alpha$`   | $\theta$        | `$\theta$`  |
| $\beta$         | `$\beta$`    | $\iota$         | `$\iota$`   |
| $\gamma$        | `$\gamma$`   | $\kappa$        | `$\kappa$`  |
| $\delta$        | `$\delta$`   | $\lambda$       | `$\lambda$` |
| $\epsilon$      | `$\epsilon$` | $\mu$           | `$\mu$`     |
| $\zeta$         | `$\zeta$`    | $\nu$           | `$\nu$`     |

---

| Greek Letter | Lowercase | Greek Letter | Lowercase |
|--------------|-------------|--------------|--------------|
| $\eta$          | `$\eta$`     | $\xi$           | `$\xi$`     |
| omicron      | `o` | $\upsilon$      | `$\upsilon$` |
| $\pi$           | `$\pi$`      | $\phi$          | `$\phi$`    |
| $\rho$          | `$\rho$`     | $\chi$          | `$\chi$`    |
| $\sigma$        | `$\sigma$`   | $\psi$          | `$\psi$`    |
| $\tau$          | `$\tau$`     | $\omega$        | `$\omega$`  |

---

## Se dovessi avere più equazioni?

Si hanno a disposizione una serie di ambienti:

- `gather` Più equazioni centrate una sopra l'altra.
- `aligned` Più formule allineate in un punto specificato.
- `multiline` Spezza Formule facendole andare su più righe.
- `split` Spezza Formula allineandola in un punto definito.

---

### Dimostrazione Pratica

---

# Immagini e tabelle

---

## Immagini

| Tipologia | Formati | Vantaggi|
|-----------|---------|---------|
| Vettoriale | `.svg`, `.pdf`, `.ps` | Ottimo per grafi, non ho limite di risoluzione |
| BitMap | `.png`, `.jpeg`| Ottimo per Immagini, a certi livelli di zoom ottengo difetti di quantizzazione | 

---

Latex supporta nativamente `pdf`, `jpeg`, `png` ed `eps`

Tutti i formati più o meno sono supportati mediante pacchetti aggiuntivi, in base alla complessità del formato questo ha un costo in tempo di compilazione.

---

## Come includere

- `\includegraphics[opzioni]{immagine}` Sconsigliato, aggiunge immagine inline
- Ambiente `figure`, necessario anche per referenze, permette di avere più figure e didascalie.

---

### Esempio

```latex
 \begin{figure}
    \centering
    \subfloat[][\emph{Mano con sfera riflettente}]
    {\includegraphics[width=.45\textwidth]{Sfera}} \quad
    \subfloat[][\emph{Belvedere}]
    {\includegraphics[width=.45\textwidth]{Belvedere}} \\
    \subfloat[][\emph{Cascata}]
    {\includegraphics[width=.45\textwidth]{Cascata}} \quad
    \subfloat[][\emph{Salita e discesa}]
    {\includegraphics[width=.45\textwidth]{SalitaDiscesa}}
    \caption{Esempio di figura composta da più sottofigure}
    \label{fig:subfig}
\end{figure}
```