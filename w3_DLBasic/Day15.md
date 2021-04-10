GAN



강아지 이미지가 주어졌을 때,

1. generation : 강아지 사진을 찍어낼 수 있다.
2. density estimation : 어떤 이미지가 들어왔을 때, 확률값 하나가 튀어나온다. 이 이미지가 강아지와 같은지 아닌지 구분할 때 활용한다. anomaly detection
3. unsupervised representation learning : 이것은 좀 애매하고 함? feature learning



입력이 주어졌을 때 어떤 확률값이 나오는게 explicit model

단순히 만들어내는 것만은 implicit model



![image-20210205100639398](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205100639398.png)

베르누이를 표현하기 위한 모수가 1개면 된다.

카테고리컬 분포에서는 m-1개의 모수가 필요하다.





1개의 RGB 픽셀이 가질 수 있는 경우의 수가 256x256x256

이를 표현하는데 필요한 파라미터는 255x255x255

1개의 RGB 픽셀을 fully descript하기 위한 파라미터 개수가 엄청 많다.



RGB의 경우의 수 너무 많으니 binary image로 예시. (0또는 1을 갖는 픽셀) 

![image-20210205101455323](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205101455323.png)



![image-20210205101614025](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205101614025.png)

이 이미지를 표현하기 위해서 파라미터 숫자를 줄이기 위해 n개의 픽셀들이 모두 독립적이라고 가정해보자.

n개의 픽셀을 표현하는데 필요한 파라미터 숫자가 n개면 된다.

각각의 픽셀을 표현하는데 파라미터 1개만 있으면 되고, 모두 독립적으로 있으니 그냥 더하면 된다.



?왜 독립적이면 n개고 아니면 2^n??





fully dependent하면 너무 많은 파라미터 필요하고 (2^n) fully independent하자면 파라미터는 적은데 표현할 수 있는 이미지가 너무 적다. 또한 모두 독립적이라는게 말이 안되고..



Conditional Independence







conditional independence

z가 주어졌을 때, x와 y가 indenepdent하다. 

z라는 랜덤변수가 주어졌을 때 x와y가 independent하니까 x라는 랜덤변수를 표현하는데 z가 주어지면 y는 상관이 없다.



![image-20210205102214092](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205102214092.png)

이 chain rule과 conditional independence를 잘 활용하여 fully dependent, fully independent 모델 사이에 있는 좋은 모델을 만들 것이다 auto rgress model



![image-20210205102740659](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205102740659.png)



P(X_3 | x_1,x_2) : P(x_2 | x_1=0) 일때 x_3가 0또는 1이고, P(x_2 | x_1=1) 일때 x_3가 0또는 1이니까 총 4개가 나온다.



X_i+1 픽셀은 X_i에만 dependent하고, X_1 ~ X_i-1에는 independent하다고 가정하면.

> 이를 마르코프 가정





![image-20210205103638542](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205103638542.png)



x2가 주어졌을 때, x1은 x3와 independent하니까 x1을 날릴 수 있다.

> z라는 랜덤변수가 주어졌을 때 x와y가 independent하니까 x라는 랜덤변수를 표현하는데 z가 주어지면 y는 상관이 없다. 이 가정? (conditional independence)





## Auto-regressive Model



![image-20210205103904427](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205103904427.png)

joint distribution을 chain rule을 가지고 conditional distribution으로 쪼개 활용해 보겠다.

autoregressive model은 어떤 하나의 정보가 이전 정보들에 dependent 한것.

> X_i에 X_i-1만 dependent 한것도, X_i에 X_1~X_i-1에 모두 dependent한 것도 모두 autogregressive model 

임의의 이미지에 autogregreesive model을 적용하려면 픽셀에 순서를 매겨야한다.

2차원 이미지를 가로방향으로 순서 매길지, 지그재그로 매길지 등과 같은 방법에 따라 성능이 달라지기도 함. 

또한 이전 1개가 아닌 3개 5개 등을 고려할 수도 있따.(이렇게 어떤식으로 conditional independence를 주는지에 따라서 전체적인 structure가 달라진다.)



## NADE





i번째 픽셀을 1번쨰부터 i-1까지 픽셀에 dependent하게 한다.

2번째 픽셀은 1번째 픽셀을 입력으로 받는 NN을 만들어 스칼라값을 만들고 이를 시그모이드로 통과하여 값으로 바꾸고,

5번째 픽셀을 만들때는 1번째 픽셀 ~ 4번째 픽셀 값을 모두 받아서 NN을 만들어 스칼라만들고 시그모이드 통과시키고..



![image-20210205104740652](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205104740652.png)

X_i 픽셀은 i-1개의 픽셀에 depdent하게 된다.

NN입장에서는 입력의 크기가 계속해서 달라진다. 입력의 개수가 달라지니까



![image-20210205105018475](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205105018475.png)

NADE는 explicit 모델이다. == 확률을 계산할 수 있다.

 각각의 픽셀값에 대한 확률 분포를 알고 있으니 나온 값을 모두 곱하면 하나의 확률값이 나온다.



## Pixel RNN

![image-20210205105242406](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205105242406.png)

NADE는 FC layer를 사용했는데 여기선 RNN을 사용해서..







## Variational Auto encoder



Variational Inference

Posterior distribuiton을 찾는것이다.

PD는 나의 observation이 주어졌을 때 관심있어 하는 랜덤변수의 확률분포이다



VAE는 prior fitting term이 KL Divergence를 활용하기에

priori distribution이 가우시안이 아닌 경우에 활용하기 힘들다.



AAA는 VAE의 prior fitting term을 GAN Object로 바꿔버린 것에 불과하다.







## GAN





![image-20210205111141215](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205111141215.png)

GAN은 Generator를 좋게 학습시키는게 궁극적인 목적이다.

그러나 descrimator가 점점 학습하며 분류 성능이 좋아지기에 Generator도 같이 성능이 좋아진다.



VAE는 이미지가 들어오면 encoder를 통해 latent vector Z로 갔다가 decoder를 통해 원본 이미지의 차원으로 가고

generation 단계에서는 p(z) 즉, latent distribution에서 z를 샘플링한 걸 디코더를 태워 나오는 x가 제너레이션 결과가 된다.

![image-20210205111552217](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210205111552217.png)

GAN은 Z라는 latent distribution에서 출발해서 G 네트워크를 통해 Fake 이미지가 나오고, D 네트워크에서는 Real과 Fake를 구분하는 분류기를 학습한다.

G 모델은 만든 Fake 이미지가 D모델에서 True로 나오도록 학습하고, D 모델은 real과 fake를 잘 분류하도록 학습하고.



