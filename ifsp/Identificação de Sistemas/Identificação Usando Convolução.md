---
date: 30-04-2025
professor: Clécio Fischer
---
# Conteúdo da Aula

Pegamos um range de amostras da saída do sistemas e montamos uma matriz com o vetor y(s), a matriz da entrada u(s) que possuirá a matriz n x n onde n é o numero de amostras e o resultado que é o vetor h(s)

## Identificação da Resposta em Frequência
$$y(t) = h(t) * u(t)$$
$$Y(j\omega) = H(j\omega) U(j\omega)$$
$$H(j\omega) = \frac{Y(j\omega)}{U(j\omega)}$$
$$Y = fft(y+e); U= fft(u) $$$$H = Y ./ U$$

