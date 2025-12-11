
---
author: '`Stefano Pilosio`'
title: '`\end{advanced}`'
subtitle: Corso LaTeX LCM
date: 11 Dicembre 2025
width: 1500
header-includes: |
    <link rel="stylesheet" href="dependencies/highlightjs/styles/monokai-sublime.css">
    <script src="dependencies/highlightjs//highlight.min.js"></script>
    <script>hljs.highlightAll();</script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.21/dist/katex.min.css" integrity="sha384-zh0CIslj+VczCZtlzBcjt5ppRcsAmDnRem7ESsYwWwg3m/OaJ2l4x7YBZl9Kxxib" crossorigin="anonymous">
    <!-- The loading of KaTeX is deferred to speed up page rendering -->
    <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.21/dist/katex.min.js" integrity="sha384-Rma6DA2IPUwhNxmrB/7S3Tno0YY7sFu9WSYMCuulLhIqYSGZ2gKCJWIqhBWqMQfh" crossorigin="anonymous"></script>
    <!-- To automatically render math in text elements, include the auto-render extension: -->
    <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.21/dist/contrib/auto-render.min.js" integrity="sha384-hCXGrW6PitJEwbkoStFjeJxv+fSOOQKOPbJxSfM6G5sWZjAyWhXiTIIAmQqnlLlh" crossorigin="anonymous"
        onload="renderMathInElement(document.body);"></script>
 
---

# Ricapitolando

## Perchè conviene usare LaTeX

- Abbiamo documenti da scrivere di una certa importanza
- Abbiamo tanta matematica in suddetti documenti
- Le alternative potrebbero essere peggiori

## Criticità

Gli argomenti di oggi vorrebbero risolvere le seguenti criticità:

- Inserire figure non è un'operazione scontata;
- Compilare LaTeX potrebbe non essere ovvio;
- Scrivere documenti a più mani certamente non è ovvio.

## Altre cose

- Ma i teoremi tanto promessi?
- Ma le bibliografie?
- Come possiamo strutturare il nostro progetto per una tesi.

---

Direi di risolvere una cosa alla volta.

# Immagini e Tabelle

## Cosa abbiamo già detto

- Il comando per includere le immagini è 
```latex
\includegraphics[option]{percorso/verso/immagine}
```
- Questo comando è sconsigliato usarlo da solo in quanto inserisce l'immagine inline
- Latex supporta nativamente `pdf`, `jpeg`, `png` ed `eps`
- Bisogna usare degli ambienti accessori

> Ce ne sono tanti, sta a noi scegliere il più adeguato ai nostri scopi.

## Cose che ci siamo dimenticati

Rivedendo le slides della scorsa volta ci siamo resi conto che non abbiamo detto che per inserire le immagini servono due pacchetti:

```latex
\usepackage{graphicx}
\usepackage{tabularx}
```

OPS

## Ambiente `figure`

È l'ambiente di base, ne esistono molte varianti. Esempio di base:

::: {.container}

:::: {.col}

```latex
\begin{figure}
\centering

\includegraphics [width=0.7\textwidth]{images/caffe.png}
\caption{Immagine di una tazza di caffè}
\label{fig:immagine_caffe}
\end{figure}
```
::::

:::: {.col}
![**Figura 1**:Immagine di una tazza di caffè](images/caffe.jpg)
::::

:::

---

### Come è posizionata l'immagine

All'ambiente figure possono essere date delle opzioni quali quanto spazio può occupare oppure il posizionamento all'interno della pagina preferito.

`h` : here

`b` : bottom

`t` : top

`p` : Pagina a se stante

`h!` : **Sconsigliato**, obbliga latex a inserire l'immagine nella posizione in cui si trova nel codice.

## Ma se volessi più immagini?

Semplice, aggiungi il pacchetto `subcaption`

```latex
\usepackage{caption}
\usepackage{subcaption}
```

> Nota a margine, esistono molti metodi, questo è il più recente introdotto e pare dalle mie ricerche che sia il migliore.

---

Questo pacchetto sostituisce un pacchetto precedente, quindi contiene anche delle macro _legacy_ per la compatibilità.

---

```latex
\begin{figure}
    \centering
    \subcaptionbox{A cat \label{cat}} {\includegraphics{images/cat}}
    \subcaptionbox{An elephant\label{elephant}}{\includegraphics{images/elephant}}
    \caption{Two animals}\label{animals}
\end{figure}
```

---

![](images/gatto_elefante_1.png){width=60%}

---

```latex
\begin{figure}
    \centering
    \subcaptionbox{A cat \label{cat}}[.4\textwidth] {\includegraphics{images/cat}}%
    \subcaptionbox{An elephant\label{elephant}}[.4\textwidth]{\includegraphics{images/elephant}}%
    \caption{Two animals}\label{animals}
\end{figure}
```

---

![](images/gatto_elefante_2.png){width=80%}

---

In alternativa per fare cose più complicate vengono messi a disposizione l'ambiente `subcaptionblock` e `subcaptiongroup`, da usare anche in questo caso dentro `figure`.

---

La scorsa volta abbiamo introdotto il comando `\ref` per creare le referenze alle labels, (Se si aggiunge l'ambiente `hyperref` si ottiene anche `ref*`)

Se vogliamo riferirci solo a una delle sottofigure viene messo a disposizione `\subref`.

---

### Comandi Legacy

Siccome questo pacchetto sostituisce `subfigure` e `subfig`, mette a disposizione il comando `\subfloat` con la medesima interfaccia proposta dal pacchetto sostituito:

```latex
    \subfloat[opzioni][sotto didascalia]{ Percorso all'immagine}
```


## Immagini di tipo non supportato nativamente

La scorsa volta ho consigliato `svg`, due strade:

- Lo converti in PDF (Consigliato se hai un tempo di compilazione limitato)
- pacchetto `svg` (richiede installato inkscape, cosa che comunque ti consiglio)

In generale queste regole valgono per tutti i formati non supportati nativamente.

---

```latex
\usepackage{svg}

\begin{figure}
    \includesvg[width=\textwidth]{percorso.svg}
\end{figure}
```


## Tabelle

Esistono 3 pacchetti:

1. `array` per tabelle contenenti prevalentemente matematica;
1. `tabular` per tabelle contenenti prevalentemente testo;
1. `tabularx`che permette rispetto al precedente maggiori possibilit1a di configurazione.

---

### `array`

::: {.container}

:::: {.col}
```latex
\[
\begin{center}
    \begin{array}{ll}
    \toprule
    f(x)  & f'(x) \\
    \midrule
    x^n  & nx^{n-1}\\
    e^x & e^x\\
    \sin x & \cos x \\
    \bottomrule
    \end{array}
\end{center}
\]
```

::::

:::: {.col}

<!-- |---|---| -->
| $f(x)$ | $f'(x)$ |
|:---|:---|
| $x^n$ | $nx^{n-1}$ |
| $e^x$ | $e^x$ |
<!-- |---|---| -->

::::
:::

---

### `tabular`

::: {.container}

:::: {.col}
```latex
\begin{center}
    \begin{tabular}{ll}
    \toprule
    Tipologie di caffè  & Caratteristiche \\
    \midrule
    Arabica  & Gusto delicato con profilo aromatico complesso. \\
    Robusta & Intenso, forte e fornisce crema. \\
    Excelsa & Profumato e delicato, ma più intenso e corposo rispetto all'arabica. \\
    Liberica & Meno diffuso, contiene note e aromi differenti, nasce in Liberia e Costa d'avorio.
    \bottomrule
    \end{tabular}
\end{center}
```

::::

:::: {.col}


| Tipologie di caffè  | Caratteristiche|
|:---|:---|
| Arabica  | Gusto delicato con profilo aromatico complesso.|
| Robusta | Intenso, forte e fornisce crema.|
| Excelsa | Profumato e delicato, ma più intenso e corposo rispetto all'arabica.|
| Liberica | Meno diffuso, contiene note e aromi differenti, nasce in Liberia e Costa d'avorio.|


::::
:::

---

Quelle descritte fino ad'ora sono tabelle definite nel testo, ci forniscono l'idea di base, ma noi solitamente vogliamo una didascalia nella tabella, e la vogliamo in modalità display, detta anche _floating_.

In pratica fanno quello che farebbe un `\includegraphics` solitario.

Come al solito ci serve un ambiente:

> `table`

---

```latex
\begin{table}[<preferenze di collocazione>]
\caption{didascalia}
\label{tab:esempio}
\centering
\begin{tabular}{}
\dots
\end{tabular}
\end{table}
```

---

Piccola nota, in Italia la didascalia nelle tabelle si deve trovare prima della tabella, mente nelle figure deve trovarsi dopo la tabella.
Bisogna spiegarlo a LaTeX perchè è di tradizione americana...

```latex
\usepackage{caption}
\captionsetup{tableposition=top, figureposition=bottom, font=small}
```

---

### Descrittori dell'allineamento

- `l`, `c` e `r`;
- `p{larghezza}` Permette di stabilire a priori la larghezza di una sola colonna;
- `tabularx` permette di stabvilire a priori la larghezza dell'intera tabella.

### `tabularx`

```latex
\begin{tabularx}{width}{lXX}
A & B & C \\
Voglio & del & Caffè \\
\end{tabularx}
```

---

Ho detto un sacco di cose, direi che è giunto il tempo delle domande anche per farvi riposare un po'.

# I TEOREMI

---

## Necessario

- Pacchetto `amsthm`

## Preparazione alla scrittura

Ebbene il precedente pacchetto fornisce i seguenti tipi di enunciato:

`plain`
: Per teoremi, lemmi, corollari, proposizioni, congetture, criteri, leggi e algoritmi

`definition`
: Per definizioni, condizioni, problemi ed esempi

`remark` 
: Per osservazioni e annotazioni

---

Chiaramente usano la notazione inglese, non proprio adatto per l'italiano.

---

Si possono aggiungere nel *preambolo* degli stili.

```latex
\theoremstyle{definition}
\newtheorem{definizione}{Definizione}

\theoremstyle{plain}
\newtheorem{teorema}{Teorema}
```

---

Che poi si possono usare come ambienti nel testo:

```latex
\begin{definizione}[di Gauss]
Si dice \emph{matematico} colui
per il quale è ovvio che
$\int_{-\infty}^{+\infty}
e^{-x^2}\,dx=\sqrt{\pi}$.
\end{definizione}
\begin{teorema}
I matematici, se ce ne sono,
sono molto r ari.
\end{teorema}
```


---

**Definizione 1** (di Gauss). Si dice _matematico_ colui per il quale è ovvio che $\int_{-\infty}^{+\infty} e^{-x^2}\,dx=\pi^{1/2}$ 


**Teorema 1.** _I matematici, se ce ne sono, sono molto rari._

---

### Osservazioni

- Etichetta e numero automatico dell'enunciato ben evidenziati;
- separa enunciato dal resto del testo senza rientro;
- Definizioni con il testo normale, mentre i  teoremi in corsivo.

## Dimostrazioni

Si usa l'ambiente `proof`, questo per qualche motivo usa babel e quindi riconosce la lingua

---

Per qualunque cosa di più avanzato sui teoremi:

1. Non dovevate chiedere a uno sperimentale di tenere il corso latex;
1. Si rimanda la dimostrazione e la ricerca di [informazioni](#fonti) al lettore.

# Bibliografia

---

Altra cosa rispetto a cui LaTeX dà grandi soddisfazioni.

Si può fare manualmente. &#x1F480;

Si può fare in automatico. &#x1F60A;

## Ci vogliamo male

Se si volesse fare a mano, si usi il pacchetto `thebibliography`

Si lascia al lettore la dimostrazione che questa è una pessima idea.

## Siamo più avanzati delle scimmie

In particolare sappiamo dell'esistenza di `biblatex`.

Questo pacchetto usa come backend `bibtex` o `biber`. Il secondo è da preferirsi.

---

Bisogna costruirsi un database personale di bibliografie.

A tal proposito direi che è il caso di vedere direttamente come è fatto un sorgente latex da tesi,
anche perchè se siamo arrivati a questo punto vuol dire che la tesi la vogliamo scrivere.

---

Piccole note prima di procedere.

- Il mio database bibliografico l'ho scritto a mano.. Adesso so dell'esistenza di tools come [Zotero](https://www.zotero.org) o [jabref](https://www.jabref.org/)
- Per gestire i file multipli ho usato come pacchetto `subfiles`, non è l'unica opzione.
- Quelle che presenterò sono le mie opinioni.

# Scrivere collaborativamente e altri dettagli

---

Tutto dipende dal tool che stiamo usando per scrivere.

---

### OverLeaf

- Se premium siamo a posto. (Per la tesi, i professori almeno fino al 2024 avevano premium pagato dalla statale);

- Alternativamente un collaboratore;

- Caveat, overleaf è open source, potete fare self-hosting del servizio.. Non è per deboli di cuore, e vi servono oltre al vostro portatile, un computer aggiuntivo che faccia da server, saper impostare una VPN, sapere come funzioni docker e avere un posto con una connessione stabile. Siete convinti?

--- 

### Repository Git

Vantaggi:

- Potete usare l'editor che vi piace di più;
- Gratis fintanto che esistono gitub, gitlab e altri repository host;
- Collaboratori quanti se ne vogliono;
- Si possono fare cose interessanti con github actions o equivalenti;
- Puoi fare modifiche offline, poichè è un sistema asincrono.

Contro:

- Devi conoscere Git
- A priori è asincrono

---

Vieni al prossimo openLab di LCM dedicato a Git.

Oppure vieni a prenderti un caffè in LCM (solo 0.50 eurini) e chiedi a un admin o 150ore di spiegarti come funzioni git.

---

### Ma se volessi scrivere in contemporanea con un collega?

I vari editor possono permettere sistemi di scrittura simultanea con i colleghi. 

E.G. Vscode ha il plugin [LiveShare](https://learn.microsoft.com/it-it/visualstudio/liveshare/use/install-live-share-visual-studio-code)

---

### OK, uso git.. voglio compilare in locale... È tedioso

Soluzione: `latexmk`

---

Hai presente i makefiles? Ecco esiste un sistema automatico e migliore per latex, che gestisce lui i cicli di compilazione per te. Basta creare un file detto `latexmkrc`, e poi gli editors  faranno il resto per te.

---

```perl
# Always create PDFs and set default engine to LuaLaTeX.
$pdf_mode = 4;
# Set the lualatex variable.
$lualatex = 'lualatex -synctex=1 -interaction=nonstopmode -shell-escape -file-line-error %O %S';

@default_files = ('main.tex');

$outdir=".";
```
---

Con questo direi che abbiamo finito: Caffè? 

---

# Fonti

---

- [L'arte di scrivere LaTeX](http://www.lorenzopantieri.net/LaTeX_files/ArteLaTeX.pdf)
- [LaTeXPedia](http://www.lorenzopantieri.net/LaTeX_files/LaTeXpedia.pdf)
- [OverLeaf](https://www.overleaf.com/learn)
- [Latex compendium](https://github.com/JamesMenetrey/LatexCompendium)
- [Wikibooks](https://en.wikibooks.org/wiki/LaTeX)
- [Lista comprensiva di tutti i simboli presenti in latex](https://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf)