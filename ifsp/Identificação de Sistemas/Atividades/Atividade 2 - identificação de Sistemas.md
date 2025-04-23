---
date: 13-04-2025
professor: Clécio Fischer
---
**Nome:** Lucas Ekroth

## Questão 1 - Determinação Paramétrica
**Figura Obtida pelos Dados**
![[atividade-2_dataplot.jpg]]
Queremos encontrar a função de transferência da seguinte forma
$$\frac{Y(s)}{U(s)} = \frac{Ke^{-\tau_ds}}{\tau s +1}$$
1. Devemos calular o K, o ganho K é definido quando $s\to 0$, portanto nada mais é a relação de Y(s) por U(s) (saída pela entrada) quando estiver em estado estacionário (tempo em infinito). Encontrando os valores pelo plot:![[atividade-2_dataplot_w_marks.jpg]]
   $$K = \frac{(2.48-1.78)}{(3.56-3.04)}=1,34$$
2.  Já a constante de tempo $\tau$ é definida pelo tempo necessário para que o valor alcance +63,2% da diferença desde a excitação.$$63,2\% \space de\space (2.48-1.78) = 0,442$$ Logo encontramos que $\tau$ é igual à ==5==

3. $\tau_{d}$, ou tempo morto, é o tempo que o sistema leva para começar a responder após a excitação
$$\tau_d = 4.5-2.5 = 2s$$
Dessa forma nosso sistema possui a seguinte equação: $$H(s) = \frac{1,34e^{-2 s}}{5s+1}$$
## Questão 2 - Analise com Matlab
**Plot da resposta do modelo via Sunderasan:**![[atividade-2_matlabPlot2nd.jpg]]
**Gráfico da resposta do Modelo de Primeira Ordem:**
![[Atividade-2_matlabPlot.jpg]]

## Questão 3 - Analise Crítica
O sistema com o modelo de primeira ordem reagiu bem para este caso, fornecendo uma aproximação aceitável do comportamento dinâmico observado. A identificação dos parâmetros $K$, $\tau$ e $\tau_d$​ permitiu a obtenção de uma função de transferência coerente com os dados experimentais, apresentando uma resposta típica de sistemas com retardo e inércia.

Portanto, apesar da boa resposta inicial do modelo identificado, recomenda-se, para aplicações mais rigorosas, a validação com dados adicionais e, se necessário, o uso de modelos de ordem superior ou ajustes por métodos numéricos.