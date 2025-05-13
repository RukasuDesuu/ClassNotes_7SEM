---
date: 07-05-2025
professor: Clécio Fischer
---
# Conteúdo da Aula
### Da Última Aula
Usando convolução chegamos a seguinte função de h, que mostra um grande problema dessa forma de análise, é muito suscetível a ruído.
$$\vec{h} = \frac{y_i(k)}{u(0)} + \frac{e(k)}{u(k)}$$

Para tentarmos corrigir isso podemos usar as 
## Funções de Correlação
Se tirarmos, digamos, 100 amostras de uma simulação com a mesma entrada podemos observar que teremos saídas com o mesmo comportamento, apenas com diferenças devido ao ruído, 
Diante disso podemos fazer um cálculo da média conseguimos atenuar o nosso ruído. Esse valor de média é chamado de [[Esperança do Sinal]]
No entanto, fazer o cálculo da esperança num contexto real nem sempre é possível

Para prosseguirmos com o processo temos que verificar se o nosso sistema é [[Ergódico]]
Caso o sistema seja, podemos seguir com o conceito da [[Correlação Cruzada]]
O sistema amostrado diversas vezes com mesma entrada pode ser descrito como $$y(k+1) = \sum_{j=0}^\infty h(j) u(k+i-j)$$e usando o conceito da Autocorrelação teremos uma equação como$$r_{uy}(k) = \sum_{i=0}^\infty h(i) r_u(k-i) $$ (essa equação ainda pode ser escrita como uma matrix de dimensão $\infty \times \infty$), descrito por$$r_{uy} = R_u h$$, que ainda pode ser invertível, então $$h = R_u^{-1} r_{uy}$$

---
Uma propriedade importante é $$r_u(k) = 0, \space \forall\space k\neq0$$
$$r_{uy} = (r_u(0) I) h$$
**Função do Matlab** 
```matlab
myccf2()
```