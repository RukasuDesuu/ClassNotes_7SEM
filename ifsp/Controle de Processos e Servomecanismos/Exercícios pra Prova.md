---
date: 08-05-2025
professor: Anderson Hirata
---

# Instituto Federal de São Paulo  
## Controle de Processos Industriais e Servomecanismos  

### Lista de Exercícios 1  
**Prof. Anderson Hirata**

---

**Aluno (NOME LEGÍVEL):**  
**Prontuário:**  
**Nota:**  
**Período:**  
**Data:**  

> **Obs:** Esta lista de exercícios tem por finalidade orientar seus estudos sobre pontos principais que foram discutidos em sala de aula. As questões e exercícios podem ser respondidas e resolvidas utilizando o material fornecido pelo professor, através de bibliografia indicada, ou pesquisa própria realizada por você. Não será necessário realizar entrega sobre a lista; ao invés disso, você deverá resolvê-la e tirar as dúvidas com o professor.

---

## 1) Diferenças entre Controle de Processos e Controle de Servomecanismos

Indique:

**a)** Típicas variáveis controladas em cada tipo de controle  
**b)** Diferença entre modo regulatório e modo servo  
**c)** Exemplo de aplicação de cada um  

---

## 2) Representação da Malha de Controle Realimentada

**Diagrama:**

```tikz
\begin{document}
\begin{tikzpicture}[auto, node distance=2cm, >=latex']
  \node [input, name=R] {};
  \node [sum, right of=R] (sum) {};
  \node [block, right of=sum] (G) {$G(s)$};
  \node [block, right of=G, node distance=2.5cm] (H) {$H(s)$};
  \node [output, right of=H] (C) {};
  \node [input, below of=G, node distance=2cm] (L) {};

  \draw [->] (R) -- node {$R(s)$} (sum);
  \draw [->] (sum) -- (G);
  \draw [->] (G) -- (H);
  \draw [->] (H) -- node[name=y] {$C(s)$} (C);
  \draw [->] (y) |- ++(0,-1.5) -| node[pos=0.9, right] {$-$} (sum);
  \draw [->] (L) -| node[pos=0.75, above] {$L(s)$} (sum);
\end{tikzpicture}
\end{document}
```

**a)** Identifique cada bloco, função/sinal ou variável.  
**b)** Obtenha a função de transferência:

- $\frac{C(s)}{R(s)}$
- $\frac{C(s)}{L(s)}$

---

## 3) Modelos Matemáticos de Processos Industriais

Descreva os seguintes elementos com os parâmetros envolvidos e exemplifique com gráfico da resposta a um degrau unitário:

**a)** Elemento ganho  
**b)** Elemento integrador  
**c)** Atraso de transferência (1ª ordem)  
**d)** Atraso de transporte ou tempo morto (deadtime)  
**e)** Elemento oscilador amortecido

> Use gráficos via TikZ ou pacote `pgfplots`.

---

## 4) Sistema de Reservatório

**Figura:**

```tikz
\begin{document}
\begin{tikzpicture}[node distance=1.5cm, >=latex']
  \draw[thick] (0,0) rectangle (2,4);
  \fill[blue!20] (0,0) rectangle (2,2.5);
  \draw[dashed] (0,2.5) -- (2,2.5);
  \node at (2.3,2.5) {$h(t)$};

  \draw[->, thick] (-2,3) -- (0,3);
  \node at (-2.3,3) {$Q_e(t)$};

  \draw[->, thick] (1,-0.2) -- (1,-1.2);
  \node at (1.5,-1.2) {Saída};

  \node at (1,4.3) {Reservatório};
\end{tikzpicture}
\end{document}
```

Equação diferencial:

$$
\frac{dh}{dt} = \frac{Q_e - C_v \sqrt{\rho g} \left( \sqrt{\bar{h}} + \frac{h - \bar{h}}{2\sqrt{\bar{h}}} \right)}{A}
$$

Comparação com modelo de 1ª ordem:

$$
\tau \frac{dy}{dt} + y = Ku + \text{constante}
$$

---

## 5) Sistema de Trocador de Calor

**Figura:**

```tikz
\begin{document}
\begin{tikzpicture}[node distance=2cm, >=latex']
  \draw[thick] (0,0) rectangle (5,2);
  \node at (2.5,2.3) {Trocador de Calor};

  \draw[->, thick] (-1,1.5) -- (0,1.5);
  \node at (-1.5,1.5) {Vapor $W_v$};

  \draw[->, thick] (2.5,3) -- (2.5,2);
  \node at (2.5,3.4) {Água fria};

  \draw[->, thick] (2.5,0) -- (2.5,-1);
  \node at (2.5,-1.3) {Água quente};

  \node at (3.5,-0.5) {$T_s$};
\end{tikzpicture}
\end{document}
```

---

## 6) Sistema Superamortecido com Aproximação

### Dados do experimento:

| t (min) | Ts,m (mA) |
|---------|-----------|
| 0       | 12.0      |
| 1       | 12.0      |
| 2       | 12.5      |
| 3       | 13.1      |
| 4       | 14.0      |
| 5       | 14.8      |
| 6       | 16.4      |
| 7       | 16.1      |
| 8       | 16.4      |
| 9       | 16.8      |
| 10      | 16.9      |
| 11      | 17.0      |
| 12      | 16.9      |

### Tarefa:

1. Gerar gráfico no **MATLAB**
2. Aplicar métodos:
   - Ziegler e Nichols
   - Miller
   - Smith
   - Sundaresan e Krishnaswamy
3. Criar **script em MATLAB**
4. Comparar graficamente as aproximações



<img width=275 align="right" src="./imgs/screenshot.png">

# Obsidian TikZJax

A plugin for Obsidian that lets you render LaTeX and TikZ diagrams in your notes.

You can render graphs, figures, circuits, chemical diagrams, commutative diagrams, and more.

The following packages are available in `\usepackage{}`:
- chemfig
- tikz-cd
- circuitikz
- pgfplots
- array
- amsmath
  - amstext
- amsfonts
- amssymb
- tikz-3dplot

## Usage
Content inside of `tikz` code blocks will be rendered by TikZJax.

- Remember to load any packages you need with `\usepackage{}`, and include `\begin{document}` and `\end{document}`.

- The standalone document class is used (`\documentclass{standalone}`).


### Examples


```tikz
\begin{document}
  \begin{tikzpicture}[domain=0:4]
    \draw[very thin,color=gray] (-0.1,-1.1) grid (3.9,3.9);
    \draw[->] (-0.2,0) -- (4.2,0) node[right] {$x$};
    \draw[->] (0,-1.2) -- (0,4.2) node[above] {$f(x)$};
    \draw[color=red]    plot (\x,\x)             node[right] {$f(x) =x$};
    \draw[color=blue]   plot (\x,{sin(\x r)})    node[right] {$f(x) = \sin x$};
    \draw[color=orange] plot (\x,{0.05*exp(\x)}) node[right] {$f(x) = \frac{1}{20} \mathrm e^x$};
  \end{tikzpicture}
\end{document}
```



```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[american, voltage shift=0.5]
\draw (0,0)
to[isource, l=$I_0$, v=$V_0$] (0,3)
to[short, -*, i=$I_0$] (2,3)
to[R=$R_1$, i>_=$i_1$] (2,0) -- (0,0);
\draw (2,3) -- (4,3)
to[R=$R_2$, i>_=$i_2$]
(4,0) to[short, -*] (2,0);
\end{circuitikz}

\end{document}
```





```tikz
\usepackage{pgfplots}
\pgfplotsset{compat=1.16}

\begin{document}

\begin{tikzpicture}
\begin{axis}[colormap/viridis]
\addplot3[
	surf,
	samples=18,
	domain=-3:3
]
{exp(-x^2-y^2)*x};
\end{axis}
\end{tikzpicture}

\end{document}
```





```tikz
\usepackage{tikz-cd}

\begin{document}
\begin{tikzcd}

    T
    \arrow[drr, bend left, "x"]
    \arrow[ddr, bend right, "y"]
    \arrow[dr, dotted, "{(x,y)}" description] & & \\
    K & X \times_Z Y \arrow[r, "p"] \arrow[d, "q"]
    & X \arrow[d, "f"] \\
    & Y \arrow[r, "g"]
    & Z

\end{tikzcd}

\quad \quad

\begin{tikzcd}[row sep=2.5em]

A' \arrow[rr,"f'"] \arrow[dr,swap,"a"] \arrow[dd,swap,"g'"] &&
  B' \arrow[dd,swap,"h'" near start] \arrow[dr,"b"] \\
& A \arrow[rr,crossing over,"f" near start] &&
  B \arrow[dd,"h"] \\
C' \arrow[rr,"k'" near end] \arrow[dr,swap,"c"] && D' \arrow[dr,swap,"d"] \\
& C \arrow[rr,"k"] \arrow[uu,<-,crossing over,"g" near end]&& D

\end{tikzcd}

\end{document}
```



```tikz
\usepackage{chemfig}
\begin{document}

\chemfig{[:-90]HN(-[::-45](-[::-45]R)=[::+45]O)>[::+45]*4(-(=O)-N*5(-(<:(=[::-60]O)-[::+60]OH)-(<[::+0])(<:[::-108])-S>)--)}

\end{document}
```





```tikz
\usepackage{chemfig}
\begin{document}

\definesubmol\fragment1{

    (-[:#1,0.85,,,draw=none]
    -[::126]-[::-54](=_#(2pt,2pt)[::180])
    -[::-70](-[::-56.2,1.07]=^#(2pt,2pt)[::180,1.07])
    -[::110,0.6](-[::-148,0.60](=^[::180,0.35])-[::-18,1.1])
    -[::50,1.1](-[::18,0.60]=_[::180,0.35])
    -[::50,0.6]
    -[::110])
    }

\chemfig{
!\fragment{18}
!\fragment{90}
!\fragment{162}
!\fragment{234}
!\fragment{306}
}

\end{document}
```


## Contributing
Contributions are welcome! For information on building Tikzjax, have a look at the [contributing guide](https://github.com/artisticat1/obsidian-tikzjax/issues/68), courtesy of [@thecodechemist99](https://github.com/thecodechemist99).

## Acknowledgements
This plugin would not be possible without [TikZJax](https://github.com/kisonecat/tikzjax) by [@kisonecat](https://github.com/kisonecat)! In particular, it uses
[@drgrice1's fork](https://github.com/drgrice1/tikzjax/tree/ww-modifications) that adds some additional features.