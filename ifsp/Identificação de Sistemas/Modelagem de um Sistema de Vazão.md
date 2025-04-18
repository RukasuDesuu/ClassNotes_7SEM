---
date: 02-04-2025
professor: Clécio Fischer
---
# Conteúdo da Aula
Para encontrarmos a equação da planta, usaremos:
## Balanço de Massa
$$\frac{dm}{dt}=w_1-w_2$$
	 w é diferente de q, w é a vazão mássica
$m = kg$
$w = kg/s$
$m = V\cdot \rho$
$V = A\cdot h$
$m = A\cdot h \cdot \rho$
$q = \frac{q}{\rho}$
$$A \cdot \frac{dh}{dt} = q_i - q_o \to \frac{dh}{dt} = \frac{q_i-q_o}{A}$$
$q = K\sqrt{\Delta P}$
$q_o = K_o \sqrt{P-P_{atm}}$
$q_i=K_i\sqrt{P_b-P}$
$P = \gamma \cdot h + P_{atm}$
$$\dot{h} = \frac{K_i \sqrt{P_b - \gamma \cdot h - P_{atm}}-K_o\sqrt{\gamma \cdot h}}{A}$$
Por regressão podemos encontrar a função que representa nossa motobomba:
$$P_b = 3554,9 +682,8u(t)$$
Mantendo a bomba ligada por tempo suficiente temos um h constante que deve levar a gente a possibilidade de traçarmos $K_i$ e assim encontrar seu valor:
$$K_i = 5,6 \cdot 10^{-4} m⁴/s(kgf)^{1/2}$$
Analogamente, podemos encontrar $K_o$
$$K_o=3,06\cdot 10^{-5}+1,25\cdot10^{-5}\sqrt{\gamma\cdot h} \space m⁴/s(kgf)^{1/2}$$
Devido a diferença de nível entre $q_i$ e $q_o$ devemos considerar isso para modelagem:
$$\frac{K_i\sqrt{P_b^* - P_{atm}}}{A}+K = 0$$
$$K = \frac{-K_i \sqrt{P_b^*-P_{atm}}}{A}$$
$P_b^*$ - Pressão da bomba na condição específica $h= 0$
Foi considerado/retirado as seguintes medições:
$P_B^* = 14213,4 Kgf/m²$
$A = 2,5m²$
$P_{atm}=10300Kgf/m²$
$\gamma = 1000Kgf/m³$
$K=1,40\cdot 10^{-2} m/s$
$$\dot{h} = \frac{5,6\cdot 10^{-4}\sqrt{3554,9+682,8u(t)-1000\cdot h - 10300}}{2,5} - \frac{(3,06\cdot 10^{-5}+1,25\cdot 10^{-5}\sqrt{1000h})}{2,5}\cdot \sqrt{1000h} - 0,014$$