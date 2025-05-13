---
date: 10-05-2025
professor: Vinicius Ecard
---
## Enunciado

Dada a forma de onda triangular periódica mostrada na figura, você deve:
- **Utilizar a série exponencial de Fourier**
- **Plotar o espectro de amplitude** $∣Fn∣$ e **fase** Fn$\angle F_n$
- **Realizar isso no MATLAB**

---

##  Análise do Sinal $x(t)$

A função é periódica com período $T_0$ e definida por partes:

$$x(t) = \begin{cases} \frac{2V_m}{T_0}t, & 0 < t < \frac{T_0}{2} \\ 0, & \frac{T_0}{2} < t < T_0 \end{cases}$$

Essa função é **repetida periodicamente** para $t \in \mathbb{R}$. O espectro de Fourier pode ser obtido pela fórmula:

$$F_n = \frac{1}{T_0} \int_{0}^{T_0} x(t) e^{-jn\omega_0 t} dt, \quad \omega_0 = \frac{2\pi}{T_0}$$

Como $x(t) = 0$ de $T_0/2$ a $T_0$, a integral simplifica para:

$$F_n = \frac{1}{T_0} \int_{0}^{T_0/2} \frac{2V_m}{T_0}t \cdot e^{-jn\omega_0 t} dt$$

---

## Código MATLAB para Espectro

```matlab
Vm = 1;
T0 = 2*pi;
w0 = 2*pi/T0;
N = 30;
n = -N:N;
w = n*w0;
Fn = zeros(size(n));
  
for k = 1:length(n)
nk = n(k);
Fn(k) = (1/T0) * integral(@(t) (2*Vm/T0).*t .* exp(-1j*nk*w0*t), 0, T0/2);
end
  
% Amplitude
subplot(2,1,1);
stem(w, abs(Fn), 'filled');
xlabel('\omega [rad/s]'); ylabel('|F_n|');
title('(a) Espectro de Amplitude');
  
% Fase
subplot(2,1,2);
stem(w, (angle(Fn)), 'filled');
xlabel('\omega [rad/s]'); ylabel('\angle F_n [rad]');
title('(b) Espectro de Fase');
```
---
## Imagens Obtidas
![[Fourier.jpg]]