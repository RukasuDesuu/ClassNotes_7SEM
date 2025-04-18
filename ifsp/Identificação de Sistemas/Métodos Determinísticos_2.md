---
date: 16-04-2025
professor: Clécio Fischer
---
# Conteúdo da Aula
Continuação da aula [[Métodos Determinísticos]]

## Caso Subamortecido
Para a seguinte equação de segunda ordem:
$$H(s) = \frac{e^{-\tau_ds}\omega _n ^2}{s^2+2\zeta \omega_n s + \omega _n ^2}$$Ou então no domínio do tempo, ficaria:$$y(t) = u(t-\tau_d) \{ 1-e^{-\zeta \omega_n(t-\tau_d)} [\frac{\zeta}{\sqrt{1-\zeta ^2}}sen(\omega_n (t-\tau_d) \sqrt{1-\zeta ^2})+cos(\omega_n(t-\tau_d)\sqrt{1-\zeta^2}] \}$$
$$\lambda = (t_m - m_1) Mi = \frac{cos^{-1} \zeta}{\sqrt{1-\zeta ^2}} e^{\frac{-\zeta cos^{-1} \zeta}{\sqrt{1-\zeta ^2}}}$$
$$\omega_n = \frac{cos^{-1} \zeta}{\sqrt{1-\zeta ^2}}\frac{1}{t_m-m_1}, \space \tau_d = m_1 - \frac{2\zeta}{\omega_n}$$
 Agora devemos: 
 - Normalizar o gráfico: colocar o ponto inicial em 0 e o valor estacionário em 1 
 - Encontrar $t_m$, $M_i$ e $m_1$, igual à forma do ultimo método
 - Encontrar $\zeta$ pelo gráfico de $\lambda$, e pronto, agora temos todos valores necessários para calcular $\omega_n$ e encontrarmos a equação do sistema

## Identificação em Malha Fechada
**Requisitos para que possamos fazer a identificação**
1. Sinal tipo degrau na referência
2. Controlador apenas no ganho ==Proporcional==
3. Equação de $H(s)$ (da planta) será do primeiro grau, então será como $$H(s) = \frac{Ke^{-\tau_d s}}{\tau_s + 1}$$
4. Que em malha fechada será algo como $$\frac{Y(s)}{R(s)} = \frac{K_f e^{-\tau_ds}}{\tau_s + [K_f e ^{-\tau_ds}-1]}$$
	- Onde,
	- $K_f = K_cK$t
	- E para simularmos o tempo morto, temos que usar a [[Aproximação de Padé]]:
		- E assim, ficará: $$\frac{Y(s)}{R(s)} = \frac{\bar {K} (1-0,5\tau_ds)}{\bar{\tau}^2 s^2 + 2\zeta\bar\tau s+1}$$,onde:
		- $\bar K = \frac{K_f}{K_f+1}$
		- $\bar\tau = [\frac{\tau_d\tau}{2(K_f+1)}]^{0.5}$
		- $\zeta = \frac{\tau+0.5\tau_d (1+K_f)}{\sqrt{2\tau_d\tau(K_f+1)}}$
	- e para achar K, $K = \frac{y(\infty)}{K_c(A-y(\infty))}$, Onde $K_c$ é o ganho configurado no controlador e o A é o ganho no degrau
	- E a definição de $\tau$ que é: $$\tau = \frac{\Delta t}{\pi}[\zeta\sqrt{K_f+1}+\sqrt{\zeta^2(K_f+1)+K_f}]\sqrt{(1-\zeta ^2)(K_f+1)}$$e $\tau_d$: $$\tau_d = \frac{2\Delta t\sqrt{(1-\zeta ^2)(K_f+1)}}{\pi[\zeta\sqrt{K_f+1}+\sqrt{\zeta^2(K_f+1)+K_f}]}$$ e $\zeta$: $$\zeta= \frac{-\ln[\frac{y(\infty)-y_m}{y_{p1} -y(\infty)}]}{\sqrt{\pi ^2 + (\ln[\frac{y(\infty)-y_m}{y_{p1}-y(\infty)}])^2}}$$$$ou$$$$\zeta=\frac{-\ln[\frac{y_{p2}-y(\infty)}{y_{p1} -y(\infty)}]}{\sqrt{4\pi ^2 + (\ln[\frac{y_{p2}-y(\infty)}{y_{p1}-y(\infty)}])^2}}$$e $y(\infty)$: $$y(\infty) \approx \frac{y_{p2}y_{p1}-y²_m}{y_{p2}+y_{p1}-2y_m}$$
>$y_{p1}$ é o y no primeiro pico 
> $y_{p2}$ é o y no segundo pico
> $y_{m}$ é o y no minimo (após o overshoot)
> $\Delta t$ é a diferença do tempo do primeiro e segundo tempo (no primeiro pico quando atinge o valor estacionario)
> Para isso precisamos ==aumentar o ganho== até termos o comportamento de ==segunda ordem==

Atividade em sala,
Equação obtida foi: $$H(s) = \frac{2,3e^{-3,793s}}{10,66s+1}$$
