---
date: 08-04-2025
professor: Anderson Hirata
---
# Conteúdo da Aula
Simulação de  [[Bode]] no matlab
```matlab
clear; clc; close ALL;

%% Questão 1
% Frequência
% G(jw) = 1/(jw+2)(jw+4)
w = 0.1:0.1:10;
G = 1./((1i*w+2).*(1i*w+4));

Magnitude = abs(G);
Fase = rad2deg(angle(G));

figure(1);
subplot(2,1,1);
semilogx(w, 20*log10(Magnitude))
title("Diagrama de Bode")
subplot(2,1,2);
semilogx(w,Fase);

figure(2);
Gtf = tf(1, poly([-2 -4]));
bode(Gtf)

%% Questão 2
% a) Zero real G(s) = s + a (a = 2)
a = 2;
G_zero_real = tf([1 a], 1);
figure(3);
subplot(2,1,1);
bode(G_zero_real);
title('Zero Real: G(s) = s + 2');

% b) Polo real G(s) = 1/(s + a) (a = 2)
G_polo_real = tf(1, [1 a]);
figure(4);
subplot(2,1,1);
bode(G_polo_real);
title('Polo Real: G(s) = 1/(s + 2)');

% c) Derivador puro G(s) = s
G_derivador = tf([1 0], 1);
figure(5);
subplot(2,1,1);
bode(G_derivador);
title('Derivador Puro: G(s) = s');

% d) Integrador puro G(s) = 1/s
G_integrador = tf(1, [1 0]);
figure(6);
subplot(2,1,1);
bode(G_integrador);
title('Integrador Puro: G(s) = 1/s');

%% Questão 3
% a) G(s) = 1/ s(s+2)(s+4)
Gaf = 1./ ( (1i*w).^3 + 6*(1i*w).^2 + 8*(1i*w) + 1);
MagnitudeA = abs(Gaf);
FaseA = phase(Gaf);
figure(7);
subplot(2,1,1);
semilogx(w, 20*log10(MagnitudeA))
title("Diagrama de Bode G(s) = 1/(s(s+2)(s+4))")
subplot(2,1,2);
semilogx(w,FaseA);
figure(8);
Ga = tf(1, conv([1 0], conv([1 2], [1 4])));
Gaf = feedback(Ga, 1);
bode(Gaf);


% b) G(s) = (s+5) / (s+2)(s+4)
Gb = tf([1 5], conv([1 2], [1 4]));
Gbf = feedback(Gb, 1);
MagnitudeB = abs(Gbf);
FaseB = rad2deg(angle(Gbf));
figure(9);
subplot(2,1,1);
semilogx(w, 20*log10(MagnitudeB))
title("Diagrama de Bode G(s) = (s+5)/((s+2)(s+4))")
subplot(2,1,2);
semilogx(w,FaseB);
figure(10);
bode(Gbf);


% c) G(s) = (s+3)(s+5) / s(s+2)(s+4)
Gc = tf(conv([1 3], [1 5]), conv([1 0], conv([1 2], [1 4])));
Gcf = feedback(Gc, 1);
MagnitudeC = abs(Gcf);
FaseC = rad2deg(angle(Gcf));
figure(11);
subplot(2,1,1);
semilogx(w, 20*log10(MagnitudeC))
title("Diagrama de Bode G(s) = ((s+3)(s+5))/((s)(s+2)(s+4))")
subplot(2,1,2);
semilogx(w,FaseC);
figure(12);
bode(Gcf);
```

[[Nyquist]]
