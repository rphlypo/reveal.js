## La transformée de Fourier

<img src="./images/whalespectrum.jpg" alt="spectre d'une baleine" height="400px">

---

### L'hypothèse principale

$$\frac{\partial}{\partial t}T(x,t)=D\frac{\partial^2}{\partial x^2}T(x,t)$$

admet une solution de la forme

$$T(x,t) = \chi(x) \times \tau(t)$$

---

* Beaucoup d'équations à dérivées partielles concernées

* équations différentielles ordinaires couplées

$$
\begin{cases}
\frac{\partial^2}{\partial x^2}\chi(x) &= -K\chi(x)\\\\
\frac{\partial}{\partial t}\tau(t) &= -DK\tau(t)
\end{cases}
$$

---

Prenons $K>0$ &hellip; :

$$\begin{cases}
\frac{\partial^2}{\partial x^2}\chi(x) &= -K\chi(x)\\\\
\frac{\partial}{\partial t}\tau(t) &= -DK\tau(t)
\end{cases}
$$

$$
\implies\begin{cases}
\chi(x) &= A\sin(\sqrt{K}x) + B\cos(\sqrt{K}x)\\\\
\tau(t) & =C\exp(-DK t)
\end{cases}
$$

Note:
intégrabilité de la fonction, périodicité, ...

---

Et pour $K=0$ ?

$\chi(x) = B$ et $\tau(t)=C$

---

### La paire de Fourier

<img src="./images/spectre.png" alt="spectre d'un signal" height="400px">

dualité signal $f(x)$ &leftrightarrow; spectre $\mathcal{F}\[f\](\nu)=\int_{-\infty}^{+\infty}\mathrm e^{-\imath 2\pi \nu x}f(x)\mathrm d x$