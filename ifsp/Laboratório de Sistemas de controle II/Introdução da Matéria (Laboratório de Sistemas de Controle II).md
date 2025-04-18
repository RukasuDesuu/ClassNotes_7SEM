---
date: 25/03/2025
teacher: Anderson Hirata
---
Estudaremos **Resposta em Frequência**, como diagramas de [[Bode]] e [[Nyquist]]
## Conteúdo Programático
- Apresentação de ferramentas de projeto no domino de frequência
- Construção do Diagrama de Bode e do Diagrama de Nyquist-Analise
- Projeto de compensadores no domínio de frequência
- Aquisição de sinais e controle de sistemas em malha fechada
- Utilização de ferramentas integradas para projeto através do Lugar Geométrico das Raízes e do Gráfico de Bode
## Bibliografia Básica
- Nise, Engenharia de Sistemas de Controle, LTC, 7ªed.
- Ogata, Engenharia de Controle Moderno, Pearson, 5ªed.
- https://www.mathworks.com/
- https://www.ni.com/en/shop/labview.html

## Cálculo da nota final
$$0.75* \frac{Av_1 + Av_2}{2}+0,25*Pr$$
$Av_1$: [[Avaliação 1 de Sistemas de Controle II]]
$Av_2$: [[Avaliação 2 de Sistemas de Controle II]]
$Pr$: [[Projeto de Sistemas de Controle II]]

##  Diagrama de Bode no Matlab
Plot do diagrama de [[Bode]] de uma função de transferência no Matlab
 ```matlab
% Exemplo de Resposta em Frequẽncia
% LSCE7 - Aula 1

% frequẽncia omega (rad/s)
w = 0:0.1:10;

%funcao de transferencia G(s)
G = 2./(1i*w+2);

magnitude = sqrt(real(G).^2 + imag(G).^2);
magnitude_dB = 20*log10(magnitude);

fase = atan(imag(G)./real(G));
fase_deg =  rad2deg(fase);

%Plotando os Gráficos
figure(1);
subplot(2,1,1);
    semilogx(w, magnitude_dB );
    title('Diagrama de Bode');
    ylabel('Magnitude (dB)');
    xlabel('Frequência (rad/s)');
subplot(2,1,2);
    semilogx(w, fase_deg );
    ylabel('Fase (deg)');
    xlabel('Frequência (rad/s)')
    
    
%% MATLAB - Bode Plot
G2 = tf(2,[2,1]);
figure(2);
bode(G2);
 ```