---
date: 13-04-2025
professor: Clécio Fischer
---
**Nome:** Lucas Ekroth

## Questão 1 - Determinação Paramétrica com Método de Sundaresan
**Figura Obtida pelos Dados**
![[output.png]]

Este método funciona de forma gráfica.
$$H(s) = \frac{\omega_n ^2 e ^{-\tau_d s}}{s² + 2\zeta \omega_n s + \omega_n ²}$$
- Primeiro vamos extrair o valor de K do gráfico, isso é feita da mesma forma que nos outros sistemas 
  
  $K = \frac{2,5-1,8}{3,55 - 3,05} = 1,2$ 
  
- Agora devemos normalizar o gráfico, pegamos os valores e dividimos eles pelo valor máximo do gráfico (dessa forma ele varia apenas entre 0 e 1)
(utilizando python fiz o plot)
![[normalized-slope.png]]

- Agora, podemos usar essa seguinte formula: (área do gráfico) $$m_1 = \int_{0}^{\infty}(1-y(t)) dt = \tau_d + \tau_1 + \tau_2 $$$$\tau_1 = \frac{\eta^\frac{\eta}{1-\eta}}{M_i}$$$$\tau_2 = \frac{\eta^\frac{1}{1-\eta}}{M_i}$$$$\tau_d = m_1 - \tau_1 - \tau_2$$
$m_1= \frac{(10+5)\cdot 0.9}{2}= 6,75$
	- $M_i$ é a derivada do ponto de inflexão
		$M_i$ encontrado na derivada no ponto de inflexão foi: $\frac{1}{8.5} = 0,117$
	- $\eta$ é o valor de encontro de $\lambda$ no gráfico
			- $\lambda$ é encontrado por $\lambda = (t_m - m_1) \cdot M_i) = (8.5-6.5)\cdot 0,117 = 0,234$
		![[lambda-plot.png]]
		  $\eta = 0,147$ 
Agora Com os valores:
- $\eta = 0{,}147$
- $M_i = 0{,}117$
- $m_1 = 6{,}75$
Podemos calcular os tempos característicos.
##### Cálculo de $\tau_1$

$$
\tau_1 = \frac{\eta^{\frac{\eta}{1 - \eta}}}{M_i}
$$

$$
\tau_1 = \frac{0{,}147^{\frac{0{,}147}{1 - 0{,}147}}}{0{,}117}
= \frac{0{,}147^{\frac{0{,}147}{0{,}853}}}{0{,}117}
= \frac{0{,}147^{0{,}1724}}{0{,}117}
$$

$$
\tau_1 \approx \frac{0{,}676}{0{,}117} \approx 5{,}78
$$
##### Cálculo de $\tau_2$
$$
\tau_2 = \frac{\eta^{\frac{1}{1 - \eta}}}{M_i}
$$

$$
\tau_2 = \frac{0{,}147^{\frac{1}{1 - 0{,}147}}}{0{,}117}
= \frac{0{,}147^{1{,}1724}}{0{,}117}
$$

$$
\tau_2 \approx \frac{0{,}099}{0{,}117} \approx 0{,}85
$$
##### Cálculo de $\tau_d$

$$
\tau_d = m_1 - \tau_1 - \tau_2
$$

$$
\tau_d = 6{,}75 - 5{,}78 - 0{,}85 = 0{,}12
$$
Logo nosso $H(s)$ encontrado é igual a:$$H(s) = \frac{1,2\cdot e^{-0,12s}}{(5,78s+1)(0,85s+2)}$$

## Questão 2 - Analise com Matlab
Atribuindo os valores encontrados ao script podemos executar-lo e comparar com a resposta experimental ![[Pasted image 20250413182803.png]]
- O script ficou dessa forma:
```matlab
% Script de apoio aa aplicacao do metodo de Sundaresan et al (1978)
% aos dados bfg3.dat
%
% LAA 07/04/2020

clear
close all
 
% carrega dados
load bfg3.dat
t=bfg3(:,1);
U=bfg3(:,2);
Y=bfg3(:,3);
clear bfg3

figure(1)
subplot(211)
plot(t,U,'k');
set(gca,'FontSize',16)
axis([0 t(end) 3.0 3.8])
ylabel('entrada (volts)')

subplot(212)
plot(t,Y,'k');
set(gca,'FontSize',16)
axis([0 t(end) 1.6 2.6])
xlabel('t (s)')
ylabel('saida (volts)')


% print -djpeg bfg3.jpg

% ajustar os dados, consideraremos que a entrada inicia em 2,5 s
% que eh o 6o elemento de t. Alem disso, o metodo supoe que o valor
% da saida em estado estacionario eh um. Devemos encontrar o fator de 
% ajuste para corrigir isso, que serah o inverso da excursao da saida.

% variacao de saida
Delta_Y=mean(Y(end-15:end))-mean(Y(1:6));
% variacao da entrada
Delta_U=mean(U(end-15:end))-mean(U(1:6));
tt=t(6:end)-t(6);
% ganho
K=Delta_Y/Delta_U;


% fazendo todos os ajuste, lembrando de retirar o offset tem-se
u=(U(6:end)-mean(U(1:6)))/Delta_Y;
y=(Y(6:end)-mean(Y(1:6)))/Delta_Y;


figure(2)
subplot(211)
plot(tt,u,'k');
set(gca,'FontSize',16)
axis([0 tt(end) 0 1.2])
ylabel('entrada (volts)')

subplot(212)
plot(tt,y,'k');
set(gca,'FontSize',16)
axis([0 tt(end) 0 1.5])
xlabel('t (s)')
ylabel('saida (volts)')


% print -djpeg bfg3a.jpg


% para fins de calculos graficos, faremos uma nova figura da resposta ao
% degrau

figure(3)
plot(tt(1:61),y(1:61),'r',LineWidth=4);
set(gca,'FontSize',16)
axis([0 tt(61) 0 1.5])
xlabel('t (s)')
ylabel('saida (volts)')
grid

% print -djpeg bfg3a_zoom.jpg


%%
% area m1
m1=2.5+(11.5-2.5)/2 % Original
m1=6.5  %Sala de Aula
m1 = 6.75 %meu obtido
% inclinacao Mi
Mi=1/8.5  % Original
Mi=0.25  % Sala de Aula
Mi = 0.117 % meu obtido
tm=10;  % Original
tm=7; % Sala de Aula
tm = 8.5 %Meu obtido

lambda=(tm-m1)*Mi


% 
Eta=0.02:0.001:0.95;
Chi=log(Eta)./(Eta-1); % Eq. 3.17 do livro
Lambda=Chi.*exp(-Chi); % Eq. 3.16 do livro

figure(4)
plot(Lambda,Eta,'k',[lambda lambda],[0 1],'b')
set(gca,'FontSize',16)
xlabel('\lambda')
ylabel('\eta')


% print -djpeg eta_lambda.jpg

% valor de eta obtido graficamente
eta = 0.56; % Original
eta=0.044;  % Sala de Aula
eta = 0.147 %meu obtido

% Calculando os parametros usando Eqs. 3.18
tau1=(eta^(eta/(1-eta)))/Mi
tau2=(eta^(1/(1-eta)))/Mi
taud=m1-tau1-tau2

sys=tf(K,conv([tau1 1],[tau2 1]));
ym=lsim(sys,ones(length(tt),1)*Delta_U,tt)/Delta_Y;

figure(5)
plot(tt,y,'k',tt+taud,ym,LineWidth=4);
set(gca,'FontSize',16)
axis([0 tt(end) -0.05 1.2])
xlabel('t (s)')
ylabel('saida (volts)')
grid
%%

% print -djpeg modelo.jpg

% Ajuste
taud=taud*0.5
tau2=m1-tau1-taud
tau1

sys=tf(K,conv([tau1 1],[tau2 1]));
ym=lsim(sys,ones(length(tt),1)*Delta_U,tt)/Delta_Y;

figure(6)
plot(tt,y,'k',tt+taud,ym,LineWidth=4);
set(gca,'FontSize',16)
axis([0 tt(end) -0.05 1.2])
xlabel('t (s)')
ylabel('saida (volts)')
grid

% print -djpeg modelo_ajustado.jpg

```

Onde meus dados foram adicionados com o comentário "meu obtido"

### Questão 3 - Analise Crítica
A curva da nossa função de transferência se adequou bem ao sistema, o nosso tempo morto ficou um pouco adiantado, mas ficou bem proximo, além de que o tempo de inflexão parecer estar bem 'encaixado'
Ainda há certos ajustes finos que podem ser feitos, mas dessa forma já está bem próximo. 