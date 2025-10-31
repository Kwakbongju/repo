# State Variables
## The concept of state variables
![](https://i.ifh.cc/ZLmbAn.jpg)  

State는 vector로 확장된다. Vector로 확장된 state를 이용해서 state space equation을 만든다. 

System을 수식화 할 때, state를 정의해 system안에 의미있는 것들을 먼저 정의해 이것을 중심으로 문제 풀이 진행 이것을 state variable 모델이라고 한다.

State는 input과 다른 state에 영향을 받는다. Output은 input과 state의 조합으로 만들어진다.

state variable 모델은 문제를 푸는 과정에 의미를 부여한다. 또한 벡터이기에 컴퓨터에서 다루기도 쉽다.  



## Example 1: spring-mass-damper system
 

![](https://i.ifh.cc/yDBCnZ.png)

우선 수학적 모델을 먼저 알아야한다(아래에 있는 식은 라플라스를 이용해서 풀었다)  

$$
M \frac{d^2y(t)}{dt^2} + b \frac{dy(t)}{dt} + k y(t) = r(t)
$$

상태변수를 다음과 같이 정의한다:

$$
x_1(t) = y(t), \quad x_2(t) = \frac{dy(t)}{dt}
$$

따라서 상태방정식은 다음과 같다:

$$
\begin{cases}
\frac{dx_1(t)}{dt} = x_2(t) \\
\frac{dx_2(t)}{dt} = -\frac{b}{M}x_2(t) - \frac{k}{M}x_1(t) + \frac{1}{M}r(t)
\end{cases}
$$

출력방정식은 다음과 같다:

$$
y(t) = x_1(t)
$$

2차 미분 방적식이기에 state를 2개 정의했으며, 이때 변위와 변위의 미분을 state로 정의했다.  
state와 수학적 모델을 이용해 2차 미분 방정식은 1차 미분 방정식 2개로 바꾼다.  

ouput에 대한 식도 깔끔하게 정리돼서 나온다.

## Example 2: R-L-C circuit system  

![](https://i.ifh.cc/BOQ27k.png)  



상태변수 정의:  

$$
x_1(t) = v_C(t), \quad x_2(t) = i_L(t)
$$  


---

### 🔹 By KCL
$$
u(t) = C \frac{dx_1(t)}{dt} + x_2(t)
\quad \Rightarrow \quad
\frac{dx_1(t)}{dt} = \frac{1}{C}\big[-x_2(t) + u(t)\big]
$$

---

### 🔹 By KVL
$$
L \frac{dx_2(t)}{dt} + R x_2(t) - x_1(t) = 0
\quad \Rightarrow \quad
\frac{dx_2(t)}{dt} = \frac{1}{L}\big[x_1(t) - R x_2(t)\big]
$$

---

### 🔹 State-Space Equations
$$
\begin{cases}
\frac{dx_1(t)}{dt} = \frac{1}{C}\big[-x_2(t) + u(t)\big] \\
\frac{dx_2(t)}{dt} = \frac{1}{L}\big[x_1(t) - R x_2(t)\big]
\end{cases}
$$

출력 방정식:  

$$
y(t) = R x_2(t)
$$  

state를 정의하는 것은 일단은 그냥 넘어가도록 한다. 이후에 이에 대해 자세히 다룰 시간이 있다.  

그냥 이와 같이 세팅한다고 암기하면 된다. 다만 여기서 state를 정의함에 있어 주의해야할 것이다.  

$$x_1(t)$$와 $$x_2(t)$$가 항등식이 되지만 않으면 된다.  

이에 대한 예시로 상수배가 되는 관계는 안된다. state를 독립적으로 세팅해줘야 한다.  

State variable을 이용해 equation을 만들 때, (state)’=something 이러한 형식으로 정리하면 편하다.  


1차 미분 방정식의 기본 형태가 $$x’=ax+b$$이기 때문이다. 위에 있는 식은 $$x’_1=ax_2+bu(t)$$형식으로 정리된다.  





## 1st Order State Differential Equation

If we define **states**, the differential equation is derived as:

$$
\dot{x}(t) = a x(t) + b u(t)
$$

Laplace transform:

$$
sX(s) - x(0) = aX(s) + bU(s)
$$

$$
(s - a)X(s) = x(0) + bU(s)
$$

$$
X(s) = \frac{1}{s - a}x(0) + \frac{1}{s - a}bU(s)
$$

---

Inverse Laplace transform:

$$
x(t) = e^{at}x(0) + \int_{0}^{t} e^{a(t-\tau)}b u(\tau) d\tau
$$

---

Thus, it can be expressed compactly as:

$$
x(t) = \Phi(t) \, x(0) + \int_{0}^{t} \Phi(t - \tau) \, b \, u(\tau) \, d\tau
$$  


1차 미방이 이렇게 정리가 된다. Exp 부분을 ϕ(t)로 치환 적분 안에 있는 Exp부분도 ϕ(t)꼴로 치환 가능하다.

초기값이 ϕ(t)에 의해 바뀐다. Input이 ϕ(t)에 의해 바뀐다.  



> 🟢 Transition from initial state: $$\Phi(t) · x(0) \)$$  
> 🔵 Effect of input:  $$\displaystyle \int_{0}^{t} \Phi(t - \tau) b u(\tau) d\tau \$$

Much more** meaningful!**  

### state를 정의하고 미방으로 바꿔야하는 이유  

다차의 미분방정식 여러 개의 1차 미방으로 바뀐다 -> 컴퓨터에게 시키기 쉬워진다.  

수식에 의미부여를 할 수 있게 된다.  


결과 계산을 끝내면 1차 행렬 미분방정식이 나오게 된다.  

이때 왼쪽 항은 state 초기 상태를 $$\Phi(t)\$$에 의해 변환된 값을 전달한다.  

오른쪽 항은 input을 $$\Phi(t)\$$에 의해 변환된 값을 전달한다.  


## State vector and state space equation  

![](https://i.ifh.cc/S7TS4L.jpg)  

State는 일반적으로 vector form으로 정의한다. 그리고 그것을 State Vector라고 부른다.  

A와 B는 행렬이다.1차 미분방정식이 여러 개이기 때문이다.  

다차 미분방정식을 여래 개의 1차 미방으로 바꾼다. 그것을 1차 행렬 미분방정식으로 바꾼 것을 state differential equation이라고 한다.  

State와 input을 조합해 ouput을 만드는 equatio을 output equation이라고 한다.  

2개를 묶어서 state space equation이라고 한다.  


맨 아래에서 왼쪽 식을 오른쪽처럼 바꿀 수 있다. 결국 오른쪽 식을 유도하기 위함이다.  

ouput도 행렬 방정식으로 만든다. 하지만 이는 미분 방정식은 아니고 일반 방정식이다.  


## State transition matrix  

###  1st Order System
$$
x(t) = e^{at}x(0) + \int_{0}^{t} e^{a(t-\tau)}b\,u(\tau)\,d\tau
$$  


1차 미분 방정식을 라플라스로 풀면 이러한 형태가 나온다. 이때 a는 상수이다.  

---

###  n-th Order System
$$
x(t) = \exp(At)x(0) + \int_{0}^{t} \exp[A(t-\tau)]B\,u(\tau)\,d\tau
$$

다음으로 다차에서 보면 1차 미분 방정식에서 상수인 a가 다차 미분 방정식에서는 행렬 A가 되는 것을 볼 수 있다.
  
---

###  Laplace Domain Representation
$$
x(s) = [sI - A]^{-1}x(0) + [sI - A]^{-1}B\,U(s)
$$  

행렬을 기준으로 다시 라플라스 변환을 하면 풀이가 이와 같이 변하게 된다.  



Define the **State Transition Matrix** in the *Laplace domain* as:  

$$
\Phi(s) = [sI - A]^{-1}
$$  

아까 exp를 ϕ(t)로 치환했던 것처럼 이번에는 ϕ(s)로 치환한다.



Then, in the *time domain*:  

$$
\Phi(t) = \mathcal{L}^{-1}\{\Phi(s)\}
$$

---

### 🔹 Final Expression  

$$
x(t) = \Phi(t)\,x(0) + \int_{0}^{t} \Phi(t-\tau)\,B\,u(\tau)\,d\tau
$$

> 🟢 **Φ(t) : State Transition Matrix**  
> 🔵 Describes the transition of the state vector over time.  
>  
> $$\Phi(t)x(0) \$$ → Transition from initial state  
>  
> $$\displaystyle \int_{0}^{t}\Phi(t-\tau)B\,u(\tau)\,d\tau \$$ → Effect of input


 
핵심은 수학적 모델링을 통해 만든 미분방정식을 1차 행렬 미분방정식을 바꾸는 것에 있다. 



## Example 3.1  

![](https://i.ifh.cc/okjZQF.jpg)   

시스템 4차 미분방정식이다. 따라서  2차 미분방정식이 2개가 나온다.  

왜냐하면 M1기준으로 2차 미분방정식이 하나 나오고 M2기준으로 2차 미분방정식이 하나 나오기 때문이다.  


M2에 대한 식을 세울 때, 질량 사이에 있는 댐퍼와 스프링은 q와 p 둘의 영향을 받게 된다.  


 state space equation을 만들어서 4차 방정식을 다른 방식으로 푼다.  

 ![](https://i.ifh.cc/FghVBq.jpg)  

 이는 매트랩을 이용해서 풀이를 진행한 모습이다.




































