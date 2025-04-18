---
date: 09-04-2025
professor: Clécio Fischer
---
# Conteúdo da Aula
## **Sistema de Primeira Ordem**

- São sistemas onde temos apenas um elemento que armazena energia, matematicamente falando é quando a função de transferência possui um polinômio de primeiro grau no denominador $$\frac{Y(s)}{U(s)} = \frac{Ke^{-\tau_ds}}{\tau s +1}$$
	- O ganho K é definido quando $s\to 0$, portanto nada mais é a relação de Y(s) por U(s) (saída pela entrada) quando estiver em estado estacionário (tempo em infinito).
	- Já a constante de tempo $\tau$ é definida pelo tempo necessário para que o valor alcance +63,2% da diferença desde a excitação.
	- $\tau_{d}$, ou tempo morto, é o tempo que o sistema leva para começar a responder após a excitação

## **Sistema de Segunda Ordem**
- São sistemas onde temos dois elementos que armazenam energia, matematicamente falando é quando a função de transferência possui um polinôminio de segundo grau no denominador $$\frac{Y(s)}{U(s)} = \frac{K\omega_n^2 e^{-\tau_d s}}{s^2 + 2 \zeta \omega_{ns}+\omega_n^2}$$$$ou$$$$H(s) = \frac{Ke^{-\tau_d s}}{(\tau_1 s + 1)(\tau_2 s +2)}$$
- K é calculado da mesma forma que em primeiro grau
### Caso Subamortecido (onde $\zeta ^2 <<1$)
- A equação dela no domínio do tempo é definida como: $$y(t) = 1 -\frac{1}{\beta}e^{-\zeta \omega_n t}\cdot sen(\beta \omega_nt + \theta)$$
	 Onde,
	- $\beta = \sqrt{1-\zeta ^2}$
	- $\theta = tan^{-1}(\frac{\beta}{\zeta})$
	- $\omega = \omega_n \beta$
	- $\tau = \zeta \omega_n s$
	- $\zeta = \frac{4N}{2\pi} = \frac{0,6}{N}$ (approx.)
- Dessa forma conseguimos encontrar o $\zeta$
- $\omega_n$ é nossa frequência primordial, que pode ser calculado como $$\omega_n = \frac{2\pi}{T}$$
### Caso Sobreamortecido
- **Método Sundaresan**
Este método funciona de forma gráfica.
$$H(s) = \frac{\omega_n ^2 e ^{-\tau_d s}}{s² + 2\zeta \omega_n s + \omega_n ²}$$
- Primeiro vamos extrair o valor de K do gráfico, isso é feita da mesma forma que nos outros sistemas 
- Agora devemos normalizar o gráfico, pegamos os valores e dividimos eles pelo valor máximo do gráfico (dessa forma ele varia apenas entre 0 e 1)
- Agora, podemos usar essa seguinte formula: (área do gráfico) $$m_1 = \int_{0}^{\infty}(1-y(t)) dt = \tau_d + \tau_1 + \tau_2 $$$$\tau_1 = \frac{\eta^\frac{\eta}{1-\eta}}{M_i}$$$$\tau_2 = \frac{\eta^\frac{1}{1-\eta}}{M_i}$$$$\tau_d = m_1 - \tau_1 - \tau_2$$
	- $M_i$ é a derivada do ponto de inflexão
	- $\eta$ é o valor de encontro de $\lambda$ no gráfico
		- $\lambda$ é encontrado por $\lambda = (t_m - m_1) \cdot M_i)$
	