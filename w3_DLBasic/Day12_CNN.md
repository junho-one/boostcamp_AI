# Day12 CNN



FC Layer에서는 학습해야할 파라미터 개수가 크다.





입력의 크기를 (I_H, I_W), 커널의 크기를 (K_H, K_W), 출력의 크기를 (O_H,O_W)라면

출력의 크기는 (I_H -K_H +1, I_W - K_W + 1)

> 28x28  + 3x3 => 26x26



![image-20210202114519246](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202114519246.png)



채널이 여러개면 커널의 채널수와 입력의 채널 수가 같아야 한다.

각각의 채널마다 커널이 만들어짐.

결과로는 채널이 1인 결과가 만들어진다.

![image-20210202114615512](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202114615512.png)

보통은 이렇게 커널을 O_c개 만들어 결과값이 O_c의 채널을 갖도록 한다.





## Convolution 연산의 역전파



![image-20210202115028809](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202115028809.png)

x에 미분을 하게 되면 미분 기호가 안에 들어가면 시그널에 해당하는 부ㅜㅂㄴ에 미분이 적용되니까 

g의 도함수와 f가 컨볼루션 연산을 수행한다.

**컨볼루션 연산을 미분해도 똑같이 컨볼루션 연산이 나온다.**



![image-20210202115302509](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202115302509.png)

이렇게 계산해주고 

BP 단계에서 손실함수에서 값을 계산한 후에 chain rule을 통해 미분되면서 layer들을 지나게 되고,

이 convolution layer의 출력벡터의 텀에서는 delta1, delta2, delta3 라는 미분값이 출력벡터의 위치에 전달이 된다.

이 delta들이 입력과 커널에 전달되는지 살펴보자



위 사진의 화살표를 보면 입력 X3에 대해  o1에는 x3\*w3, o2에는 x3\*w2, o3에는 x3\*w1이 적용됐다.

![image-20210202115838815](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202115838815.png)

즉, x3에 대한 입력이 o1, o2, o3에 영향을 줄 때 적용된 가중치에 따라서 그레디언트 벡터에도 사용

forwrad propagation에서 x3가 w3와 곱해져서 o1에 더해졋으니, 그레디언트에서도 똑같이 d1과 w3가 곱해져서 x3에 전달된다.





![image-20210202120348949](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202120348949.png)

결과적으로 o3에 전달할 떄 x3가 w1을 톻애 전달했기 때문에, w1의 그레디언트는 delta3*x3가 된다.

커널에는 delta에다 입력값이 곱해져서 전달된다.

각각의 커널들은 입력 x3에 대해서만 적용된게 아니라 다른 데이터에 대해서도 적용됐다.

![image-20210202120500144](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202120500144.png)

w1이 적용된 입력데이터가 x1,x2,x3이니 이 값들만 delta와 연산하여 w1의 그레디언트로 만든다.

이 또한 컨볼루션 연산



