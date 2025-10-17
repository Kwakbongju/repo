# P3.1
$$M·\ddot{y}(t) = F(t)-b\dot{y}(t)-ky(t)$$

(a)

$$y(t)=x_{1}(t),  \dot{y}=x_{2}(t)$$

(b)

$$\dot{x_{1}}(t)=\dot{y}(t)=x_{2}(t)$$

$$\dot{x_{2}}(t)=\ddot{y}(t)=-\frac{k}{M}x_{1}(t)-\frac{b}{M}x_{2}(t)+\frac{1}{M}F(t)$$

(c)

$$
x(t) =
\begin{pmatrix}
x_1(t) \\
x_2(t)
\end{pmatrix}
$$



$$
\dot{x}(t) =
\begin{bmatrix}
0 & 1 \\
-\frac{k}{M} & -\frac{b}{M}
\end{bmatrix}
x(t)
+
\begin{bmatrix}
0 \\
\frac{1}{M}
\end{bmatrix}
F(t)
$$


$$
y(t) =\begin{bmatrix}0 & 1\end{bmatrix}x(t)
$$

# P3.3

$$
x_1=i_L(t)\quad x_2=v_C(t)
$$

$$
\text{KVL: } -v_1(t)+L\frac{di_L(t)}{dt}-v_C(t)+v_2(t)=0 

-v_1(t)+L\dot{x}_1(t)-x_2(t)+v_2(t)=0 \\

\dot{x}_1=\frac{v_1(t)+x_2(t)-v_2(t)}{L} \\

\dot{x}_1=\frac{1}{L}x_2(t)+\frac{1}{L}v_1(t)-\frac{1}{L}v_2(t)
$$







