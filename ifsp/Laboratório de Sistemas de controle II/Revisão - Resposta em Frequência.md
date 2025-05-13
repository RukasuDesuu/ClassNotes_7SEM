---
date: 06-05-2025
professor: Anderson Hirata
---
**Nome:** Lucas Ekroth
# Lista 1 - Resposta em Frequência
**1.** $G(s) = \frac{1}{(s+2)(s+4)}$, substituindo $s = j\omega$
$$G(j\omega) = \frac{1}{(j\omega+2)(j\omega+4)}$$Expandindo o denominador e multiplicando pelo conjugado. $$G(j\omega) = \frac{1}{-\omega² +6j\omega + 8} \cdot \frac{-\omega² -6j\omega + 8}{-\omega² -6j\omega + 8} = \frac{-\omega^2-6j\omega+8}{\omega^4+20\omega^2 +64}$$
**Magnitude:** $$M_G(\omega)=\sqrt{(\frac{-\omega^2+8}{\omega^4+20\omega +64})^2 - (\frac{6j\omega}{\omega^4+20\omega^2 +64})^2}=\sqrt{\frac{\omega^4-16\omega^2+64}{(\omega^4 + 20 \omega^2 +64)^2}+\frac{36\omega}{(\omega^4 + 20 \omega^2 +64)^2}}$$
$$M_G(\omega)=\sqrt{\frac{\omega^4+20\omega + 64}{(\omega^4+20\omega+64)^2}}=\frac{1}{\sqrt{\omega^4+20\omega+64}}$$
**Fase:**
$$\phi_G=\tan^{-1}\Big(\frac{6\omega}{-\omega^2+8}\Big)$$