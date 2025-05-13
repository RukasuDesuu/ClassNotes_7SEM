---
date: 10-05-2025
professor: Clécio Fischer
---
## **1. Método de Identificação de Sundaresan**

O **método de Sundaresan** é uma técnica gráfica usada para identificar modelos de sistemas dinâmicos de **primeira ou segunda ordem com atraso**, a partir da resposta ao degrau. A principal vantagem desse método é a simplicidade de sua aplicação prática.

### **Para sistemas sobreamortecidos**

* A resposta ao degrau **não possui oscilações**, é **monótona** e atinge o regime permanente de forma exponencial.
* O procedimento consiste em determinar dois instantes de tempo:
  * $t_1$ → quando a resposta atinge **35,3%** do valor final.
  * $t_2$ → quando a resposta atinge **85,3%** do valor final.
* A partir desses dois pontos, calculam-se:
  * A **constante de tempo** $\tau$: $$\tau = \frac{t_2 - t_1}{1.3}$$
  * O **tempo de atraso** $\tau_d$: $$\tau_d = t_1 - 0.29 \cdot \tau$$
### **Para sistemas subamortecidos**
* A resposta ao degrau é **oscilatória amortecida**, com picos que decaem ao longo do tempo.
* O método busca estimar os parâmetros de um sistema de **segunda ordem com atraso**:$$G(s) = \frac{K e^{-\tau_d s}}{\tau^2 s^2 + 2\xi\tau s + 1}$$
* Os passos principais:
  * Determinar os tempos dos dois primeiros picos $t_1$ e $t_2$.
  * Calcular o **período de oscilação** $T = t_2 - t_1$.
  * Determinar o **fator de amortecimento $\xi$** por meio do logaritmo do decremento: $$\delta = \ln\left(\frac{y_1}{y_2}\right),\quad \xi = \frac{\delta}{\sqrt{4\pi^2 + \delta^2}} $$
  * Obter a **frequência natural**: $$\omega_n = \frac{2\pi}{T \sqrt{1 - \xi^2}},\quad
\tau = \frac{1}{\omega_n}$$
  * O atraso $\tau_d$ é estimado por extrapolação linear ou análise da curva.

---

## **2. Aplicação do Método de Sundaresan**

### **Modelo Matemático Proposto**
Para sistemas com atraso e comportamento de primeira ou segunda ordem:
* **Primeira ordem com atraso**:$$
  G(s) = \frac{K e^{-\tau_d s}}{\tau s + 1} $$
* **Segunda ordem com atraso**:$$
  G(s) = \frac{K e^{-\tau_d s}}{\tau^2 s^2 + 2\xi\tau s + 1} $$
### **Aplicação a dois sistemas distintos**
#### **a) Sistema sobreamortecido (sem oscilações)**
Suponha os tempos identificados da resposta ao degrau:
* $t_1 = 2.0\ \text{s}$ (35,3%)
* $t_2 = 5.0\ \text{s}$ (85,3%)
Aplicando:
* $\tau = \frac{5.0 - 2.0}{1.3} = 2.31\ \text{s}$
* $\tau_d = 2.0 - 0.29 \cdot 2.31 \approx 1.33\ \text{s}$

Modelo identificado:$$
G(s) = \frac{K e^{-1.33s}}{2.31s + 1}$$
#### **b) Sistema subamortecido (com oscilações)**
Suponha:
* Pico 1: $y_1 = 1.2$ em $t_1 = 1.5\ \text{s}$
* Pico 2: $y_2 = 0.8$ em $t_2 = 4.5\ \text{s}$
Cálculos:
* $\delta = \ln(1.2/0.8) \approx 0.405$
* $\xi = \frac{0.405}{\sqrt{4\pi^2 + 0.405^2}} \approx 0.064$
* $T = 3.0\ \text{s}$
* $\omega_n = \frac{2\pi}{3 \cdot \sqrt{1 - 0.064^2}} \approx 2.10$
* $\tau = \frac{1}{\omega_n} \approx 0.476$
* Estimativa de atraso: $\tau_d \approx 0.5\ \text{s}$
Modelo identificado:

$$
G(s) = \frac{K e^{-0.5s}}{(0.476)^2 s^2 + 2 \cdot 0.064 \cdot 0.476 s + 1}
$$

---

## **3. Identificação em Malha Aberta a partir de Malha Fechada**

O sistema está em **malha fechada com controle proporcional**:
* $K_c = 3$
* Modelo do sistema fechado:

  $$
  H_{mf}(s) = \frac{K_p e^{-\tau_d s}}{\tau s + 1 + K_c K_p e^{-\tau_d s}}
  $$

### **Procedimento**
1. Obter a resposta ao degrau da **malha fechada**.
2. Estimar os tempos $t_1$ e $t_2$ como no método de Sundaresan.
3. Obter $\tau_{mf}$ e $\tau_{d_{mf}}$.
4. Calcular a **ganho da planta em malha aberta**:
   A partir da relação:$$   K_{mf} = \frac{K_p K_c}{1 + K_p K_c} \Rightarrow K_p = \frac{K_{mf}}{K_c (1 - K_{mf})}$$
5. Com $K_p$, $\tau$ e $\tau_d$, escrever:$$   G(s) = \frac{K_p e^{-\tau_d s}}{\tau s + 1}   $$
---
## **4. Identificação via Convolução e Domínio da Frequência (MATLAB)**
### **Código explicado passo a passo**
```matlab
u = prbs(40,8,2);        % Geração de sinal PRBS com 40 amostras (Sinal de Entrada)
u = u - 0.9;             % Ajusta nível DC do sinal
lu = length(u);          % Comprimento do vetor de entrada
y = dlsim([2 0.9],[1 -1.6 0.8],u);   % Saída simulada de sistema com entrada u
e = randn(40,1);         % Geração de ruído branco gaussiano
e = 0.003*(e - mean(e)); % Normalização e escalamento do ruído
yi = dimpulse([2 0.9],[1 -1.6 0.8],lu); % Resposta ao impulso
```
#### **Identificação por convolução**
1. A resposta ao impulso `yi` representa o **modelo de convolução**.
2. A saída esperada pode ser reconstituída como:$$   y(t) = \sum_{k=0}^{N} h(k) \cdot u(t - k)   $$
   onde $h(k)$ é `yi(k)`.
3. Assim, basta convolver `u` com `yi` para reconstruir o sistema.
#### **Identificação no domínio da frequência**
1. Aplicar a Transformada Discreta de Fourier (DFT) em `u` e `y`.
2. Calcular a função de transferência:$$   G(e^{j\omega}) = \frac{Y(e^{j\omega})}{U(e^{j\omega})}$$
3. Ajustar um modelo racional via identificação espectral (`tfest`, `arx`, etc.)

