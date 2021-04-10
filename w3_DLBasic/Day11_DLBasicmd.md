# DeepLearning Basic



Key components of DL

* The **Data** that the model can learn

* The **Model** how to transform the data

* The **loss function** that quantifies the badness of the model

* The **algorithm** to adjust the parameters to minimize the loss 

  > SGD, Adam Optimizer



이 네가지 항목에 비추어서 새로운 논문이나 기술을 보게 되면 

기존 연구에 비해서 어떤 장점이 있고 변형이 있는지를 알기 쉽다!!





## loss fuction

모델이 정해지고 데이터가 정해져있을 때, 이 모델을 어떻게 학습할지

> 각 layer의 weight와 bias를 어떻게 업데이트 할지



regression task 에서는  모델의 예측값과 실제값의 차이의 제곱을 최소화 시키는 방향으로. MSE

classification task 에서는 모델의 예측값과 실제값의 cross entropy를 최소화하는 방향으로.

probabilistic task 에서는 출력값을 단순 값이 아닌 값에 대한 평균과 분산 과 같은 것으로 모델링할 때 MLE를 통해서도 가능.



항상 이 값을 사용하는게 아니고 데이터와 상황에 따라 달라진다. 왜 사용하는지를 아는 것이 중요하다.



mle는 제곱 쓰지만 절대값 쓰는 loss function도 있다. L1 norm?

어떤 아웃라이어가 있을 때 이 데이터에 맞추려다가 뉴럴넷이 망가지는 경우가 있다.

그렇기에 l2 norm이 항상 맞는 방법은 아닐 수 있다.



분류문제의 아웃풋은 대부분 원핫벡터로 표현된다.

yi^(d)는 하나만 1이고 나머지는 0 인 벡터

그래서 크로스엔트로피를 쓰는건데... 이게 최적일까?? 하는 생각도 해바야한다.



probabilistic task

모델이 아웃풋이 숫자가 아닌 확률적인 문제를 풀고 싶을 떄

사람의 사진을 보고 나이를 맞추는데, 15, 46살 이렇게 나오는게 아니라

20살이긴 한데 약간 애매해, 이사람은 확실히 30살이야 같이 신뢰도? 같은것을 같이 낼때..



## Optimizer

사람들은 그냥 Adam을 쓴다. 결과가 잘나오니까..

왜 Adam을 쓸까..





다양한 hyperparameter 서치를 하낟.

어떤 옵티마이저 쓰고, base lr, lr 스케쥴링은 어케할지 등등... 이에 따라 성능이 차이가 많이 남



구글은 컴퓨팅 파워가 짱짱하기에 여러가지를 하지만

우리들은 몇번 실험 못해. 이떄 좋은 성능을 내는게 Adam







AI를 만들기 위해 뇌를 모방할 필요는 없다.

시작은 neuron에 동작방법을 모방하며 시작했겠지만, 작금의 뉴럴넷이 잘 작동하는게 뇌를 모방해서 잘 되는게 아니라 여러 변형과 시도로 잘되는 것

> 날기위해 새를 모방하다 새와는 다른 방법으로 날고있다.





편미분을 해서 얻어내는 gradient 정보는 local한 정보이다. 그 위치에서 조금만 유효하기에

step size가 크면 학습이 안된다.

> adaptive learning rate 방법론은 step size를 자동으로 바꿔준다.



n차원 -> m 차원으로 가고 싶다면 행렬을 사용하면 되지.

100차원 입력에서 20차원 출력으로 

이러한 행렬을 곱하는 것을 affine transform이라 한다.



이러한 행렬의 곱 혹은 행렬은 두개의 벡터 공간 사이의 변환으로 해석하는게 좋다.

행렬을 찾는 다는 것은 두 차원 사이의 선형변환을 찾겠다는 것이다.



![image-20210201130235851](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210201130235851.png)

다음과 같이 linear transform으로만 layer를 쌓게 된다면 

W_2*W_1은 사실상 한개의 layer에 있는 어떠한 선형변환 W_x와 같은 것이다. 쌓는 의미가 없어



![image-20210201130327714](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210201130327714.png)

그래서 중간에 nonlinear transform을 넣어준다

x에서 y로 가는 매핑이 표현할 수 있는 **표현력을 최대한 극대화 하기 위해서**는

단순 선형결합을 반복하는 것이 아니라 중간에 activation function을 넣어 non linear transform을 거치고 선형결합하고, 비선형결합 거치고 .....

> 많은 파라미터를 쓰면 더 표현력이 좋겟지. 그래서 쌓는거고. 그런데 선형결합만 하면 파라미터 많아도 의미가 없으니!





히든 레이어가 1개 있는 뉴럴 네트워크의 표현력은 대부분의 continuous function들을 잘 표현한다.

 









reshape = view

axis = dim

squeeze : 매트릭스를 하나 줄여줌. 랭크를 하나 줄여줌





torch autograd



```
w = torch.tensor(2.0, requires_grad=True)
y = w**2
z = 2*y+5
# z = 2*w^2 + 5라는 식, 그래프를 만든것

z.backward() # 미분 연산을 한다.
w.grad # 미분 값이 출력. # == tensor(8.)
```



nn.Linear 같은 함수들이 어떻게 구현되어 잇는지 찾아보는 것이 좋다... (github)

torch는 numpy와 비슷하다. 하지만 자동미분을 해준다는 것이.. 굿.





























