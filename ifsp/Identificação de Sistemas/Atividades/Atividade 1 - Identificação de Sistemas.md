---
date: 13-04-2025
professor: Clécio Fischer
---
**Nome:** Lucas Ekroth

## Exercício 1
Simulação para uma entrada degrau com função de transferência:
$$H(s) = \frac{1}{s²+0,4s+1}$$
### Script no Matlab
```matlab
% EXERCÍCIO 1 - Sistema Contínuo
clc; clear; close all;

% Sistema H(s)
num = [1];
den = [1, 0.4, 1];
sys = tf(num, den);
  
% Tempo simulado
t = -1:0.01:20;
  
% Entrada degrau explícita
u = double(t >= 0);
  
% Geração da resposta ao degrau com step
[y, t_step] = step(sys, t(t >= 0)); % MATLAB só permite t >= 0 para step
  
% Ajuste do tempo para entrada com parte negativa
t_full = t; % -1 até 20
u_full = u;
  
% Plotagem
figure;
plot(t_full, u_full, 'k--', 'LineWidth', 1.5); hold on; % Entrada
plot(t_step, y, 'b', 'LineWidth', 2); % Saída com step
title('Exercício 1: Entrada e Saída - Sistema Contínuo');
xlabel('Tempo (s)');
ylabel('Amplitude');
legend('Entrada (Degrau)', 'Saída do Sistema');
grid on;
```
### Figuras
Plot da entrada e saída
![[exercicio1-step.png]]
## Exercício 2
Simulação para um degrau da função de transferência:
$$H(z) = \frac{0,1075z^2+0,2151 z + 0,1075}{z^2-1,6129z+0,8280}$$
Utilizando $\Delta t = 0.01s$
### Script Matlab
```matlab
% EXERCÍCIO 2 - Sistema Discreto
clc; clear; close all;

% Sistema H(z)
Ts = 0.01;
num_z = [0.1075, 0.2151, 0.1075];
den_z = [1, -1.6129, 0.8280];
sys_d = tf(num_z, den_z, Ts);

% Tempo simulado
t = -1:Ts:2;
u = double(t >= 0);

% Tempo positivo apenas para a função step
t_pos = t(t >= 0);

% Saída com step (discreta)
[y, t_step] = step(sys_d, t_pos);

% Plotagem
figure;
stairs(t, u, 'k--', 'LineWidth', 1.5); hold on;             % Entrada
stairs(t_step, y, 'r', 'LineWidth', 2);                     % Saída
title('Exercício 2: Entrada e Saída - Sistema Discreto');
xlabel('Tempo (s)');
ylabel('Amplitude');
legend('Entrada (Degrau)', 'Saída do Sistema');
grid on;
```

### Figura
Plot da entrada e saída
![[exercicio2-step.png]]