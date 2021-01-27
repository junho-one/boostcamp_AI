# Day 7



## 미분

* 변수의 움직임에 따른 함수값의 변화를 측정하기 위한 도구.
* 최적화에서 제일 많이 사용하는 기법



sympy.diff : 미분을 대신해주는 함수

```
sym.diff(sym.poly(x**2 + 2*x + 3), x)
```



### 경사하강법

미분으로 점 (x,f(x))에서의 접선의 기울기를 구한다.

접선의 기울기를 통해 어느 방향으로 점을 움직여야 함수값이 증가하는지, 감소하는지를 알 수 있다.

2차원에서는 그냥 그래프를 보면 되지만, **10차원 100차원 같은 고차원 공간에서는 어느방향으로 가야 함수가 증가하는 감소하는지를 알기가 쉽지 않다.** 이를 위해 미분..

미분값이 있을 때 함수값을 증가시키고 싶으면 x에 미분값을 더하면 되고, 감소시키고 싶으면 빼면 된다.

미분값을 더하면 경사상승법이라 하며 함수의 극대값 위치를 구할 때 사용한다. 빼면 경사하강법으로 극소값으로 간다.극값에 도달하면 미분값이 0이기에 움직임을 멈춘다.



```
def func(val) :
	fun = sym.poly(x**2 + 2*x + 3)
	return fun.subs(x, val), fun

def func_gradient(fun, val) :
	_, function = fun(val)
	diff = sym.diff(function, x)
	return diff.subs(x, val), diff

def gradient_descent(fun, init_point, lr = 1e-2, epsilon = 1e-5)
	val = init_point
	diff, _ = func_gradient(fun, init_point)
	while np.abs(diff) < epsilon :
		val = val + lr * diff
		diff, _ = func_gradient(fun, val)

gradient_descent(fun+func, init_point+np.random.uniform(-2,2))


grad = gradient(var) # 미분을 계산하는 함수

while abs(grad) > eps :
	var = var - lr * grad
	grad = gradient(var)
```



#### d차원에서의 경사하강법

벡터가 입력인 다변수 함수의 경우 편미분을 사용한다.

**특정 방향의 좌표축으로 움직이게 하는게 편미분**

i번째 변수에서만 변화율을 알아낼 수 있다.

> 다른변수는 상수취급하고 i번째 변수에 대해서만 미분



d차원 벡터를 입력으로 받는 함수는 편미분을 d개만큼 할 수 있다. 각 변수 d개 만큼 편미분을 계산한 값들을 하나의 벡터로 표현할 수 있는데, 이 벡터를 **그레디언트 벡터**라고 한다 

> 각 gradient 벡터의 i번째 값은 i번째 변수로 편미분한 값.



앞서 그레디언트 벡터를 이용하면 일반적인 d차원 공간에서 벡터에 적용되는 경사하강법을 똑같이 사용할 수 있다.



![image-20210126130538625](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210126130538625.png)

f(x,y) = x^2 + 2y^2   ->  그레디언트 벡터 : (2x, 4y)

이 그래디언트 벡터에 -를 하면  극소점으로 향하는 화살표들의 움직임으로 볼 수 있다.



변수가 1개일 때와 다른 점은 훈련 종료를 기준을 abs(grad) 가 아닌 norm(grad)





## 경사하강법

무어 필로즈 역행렬을 사용한 회귀분석은 선형모델인 경우에만 가능하다.

비선형 모델에서는 경사하강법을 이용해서 해야함. **일반적인 기계학습 모형에서 하는 최적화는 경사하강법.**



![image-20210126131759232](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210126131759232.png)

선형 회귀의 목적식은 L2 norm

> 실제값을 담은 벡터와 예측값을 담은 벡터가 가장 가까워지게 하는게(L2 norm 최소) 최적화



주어진 데이터에서 정답에 해당하는 y랑 선형모델의 값(XB)의 거리(차이?)인 L2 norm을 최소화하는 베타를 찾는 것이 목표.

베타를 최소화하고 싶다면 목적식을 베타로 미분을 한 다음에 주어진 베타에서 미분값(그래디언트 벡터)을 빼주게 되면 경사하강법 알고리즘으로 최소의 점을 구할 수 있다.



 ![image-20210126132615717](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210126132615717.png)

L2 norm 에서 1/n 을 해주는데 n개의 데이터를 이용하기에 평균값을 취하기 위해서 n으로 나눈다.



![image-20210126132703563](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210126132703563.png)

**L2 norm와 L2 norm의 제곱값의 그래디언트는 같다.**

왜 같은거지 ?



![image-20210126133024661](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210126133024661.png)



**B^{t+1}을 구하기 위해선 B^{t}에다 미분값 즉, 그래디언트 벡터를 빼주면 된다. 이를 반복하면 목적식을 최소화 하는 B를 구할 수 있다**



```
X = np.array([[1,1],[1,2],[2,2],[2,3]])
y = np.dot(X, np.array([1,2])) + 3

beta_gd = [10.1, 15.1, -6.5]
X_ = np.array([np.append(x,[1]) for x in X])

for t in range(T) :
	error = y - X_ @ beta
	grad = -transpose(X_) @ error
	beta = beta - lr * grad

print(beta_gd)
```



경사하강법은 **역행렬을 사용하지 않고도** 최적화할 수 있지만, 학습률과 학습횟수를 적절하게 설정하고, 볼록함수인 경우에 수렴이 보장된다.

선형회귀의 경우 **목적식  L2 norm(y-XB) 이 회귀계수 B에 대해 볼록함수이기에 수렴이 보장**된다.

하지만 비선형회귀 문제의 경우 목적식이 볼록하지 않을 수 있으므로 수렴이 항상 보장되지 않는다.



딥러닝을 사용하는 경우에는 목적식이 대부분 볼록함수가 아니고 볼록한 부분이 여러개가 나온다. 그렇기에 변형된 경사하강법 알고리즘을 사용해야한다.



### 확률적 경사하강법 (Stochastic Gradient Descent)

* 모든 데이터를 사용해서 업데이트하는 대신 데이터 한개 또는 일부 활용하여 업데이트 한다. 
* 모든 데이터를 사용해 그래디언트 벡터 계산해서를 경사하강법을 하는게 아닌 일부로 계산.



>  일부를 활용하게 되면 이 데이터를 mini batch 라고 한다. 1개만 활용하면 sgd, 데이터 일부를 활용하면 mini batch SGD. 그러나 대부분 mini batch SGD 사용하고, SGD라고 하면 mini batch SGD라고 이해하면 된다.



경사하강법과 달리 non-convex한 목적식에서도 SGD로 최적화가 가능하다.

GD에서는 Local minimum에 빠지면 나올 수 없는데 SGD는 가능.

SGD는 전체 데이터를 쓰는게 아니기에 조금씩 목적식이 달라진다. 그렇기에 빠져나올 수도 있는것



모든 데이터의 일부를 가지고 그래디언트 벡터를 계산하기에 모든 데이터를 가지고 계산한 그래디언트 벡터와는 값이 다를 수 밖에 없다. 하지만 일부를 사용해 계산한 그레디언트 벡터의 기대값이 모든 데이터를 활용해 계산한 그래디언트 벡터와 유사할 것이라는 것이 확률적으로 유사하다고 보장된다.

일부를 사용하기에 연산 자원에서 효율적이면서 GD와 유사하기에 개이득

