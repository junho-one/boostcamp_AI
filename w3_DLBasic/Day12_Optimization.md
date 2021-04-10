# Day 12 Optimization



중요한 컨셉



## Generalization

많은 경우에 일반화 성능을 높이는게 우리의 목적이다.

일반적인 학습 과정에서 epoch마다 training error는 줄어든다.

그러나 test error에 대해서는 error가더 커지는 순간이 온다.

![image-20210202094010526](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202094010526.png)

generalization performance 라는건 training error와 test error 사이의 차이

좋은 gp를 갖는다는 것은 학습데이터의 성능이 실제에서도 나온다. 즉, 갭이 적다.

그러나 애초에 학습성능이 안좋으면 gp가 좋다해도 테스트에서의 성능은 안좋다.



## Underfitting vs OverFitting

![image-20210202094203227](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202094203227.png)

underfitting : 네트워크가 너무 간단하거나, 학습을 너무 조금시켜서 학습 데이터도 잘 못맞춘다.

overfitting : 너무 학습 데이터에 맞춰져 테스트 환경에서는 잘 못맞춘다.



그러나 학습데이터도 하나의 표본. 실제로 위 사진에서 파란색 선이 모집단의 그래프일 수도 있는 것. 컨셉적인 이야기.



## Cross-validation (== k-fold validation)

학습데이터와 평가데이터를 어떻게 나눌가..

![image-20210202095400711](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202095400711.png)



학습데이터를 k개로 나눠서 k-1개로 학습 시키고, 1개로 평가를 한다.

이 과정을 평가데이터가 달라지게 k번 테스트 해본다.



cross validation을 통해 최적의 하이퍼파라미터를 찾고, 실제 학습시킬 때는 모든 데이터를 다 사용하여 학습시킨다.



## Bias and Variance

![image-20210202095415619](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202095415619.png)



Variance 란 비슷한 입력들을 넣었을 때, 출력이 얼마나 일관적으로 나오는지.

> 모델이 overfitting되면 높은 variance로 비슷한 입력에도 서로다른 출력이..

Bias 란 출력값을 평균적으로 봤을 때 실제값에 접근한다면 bias가 적다.



## Bias-variance tradeoff

![image-20210202095808421](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202095808421.png)

내가 minimize하는 cost는 사실 bias, variance, noise로 이뤄져있다.

둘중 하나가 작아지면 하나는 커지게 된다.



## Bootstrapping

신발끈을 위로 들어서 하늘을 날겠다.

학습데이터를 랜덤 서브 샘플링으로 여러개 만들고, 이 것들로 여러 모델을 만들어서 

하나의 테스팅 값에 모델들이 비슷한 결과를 내나 체크?

> 학습데이터가 100개가 있으면 80개씩 랜덤으로 뽑아 각각의 데이터셋으로 여러 모델을 학습시킬 수 있다.



## Bagging vs Boosting

![image-20210202100522382](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202100522382.png)



Bagging ( Boostrapping aggregating )

여러개 모델을 랜덤 서브 샘플링으로 만들고, 각 모델에서 나온 결과를 평균내어 최종 결과값을 내겠다.

전체 데이터를 학습시켜 1개의 모델을 만드는 것보다 bagging으로 여러 모델 만들어서 평균값으로 예측하는게 더 좋은 성능을 낼 때가 많다.

> 앙상블도 배깅에 속할 때가 많다.



Boosting

학습데이터가 100개 잇으면 간단한 모델을 만들고, 학습데이터에 대해 돌려본다.

근데 간단해서 80개는 잘하는데 20개는 잘 못해.

그럼 두번쨰 모델을 만드는데 위에서 예측 잘 안된 20개의 데이터에 대해서만 잘 맞도록 모델을 만든다

이렇게 여러 모델을 만들어서 합친다.

이 여러개의 weak learner들을 sequential하게 합쳐서 하나의 strong learaner를 만든다.







## Gradient Descent Method

1. SGD : single sample을 통해서만 gradient를 계산해서 업데이트
2. Mini-batch GD : batch size만큼의 sample을 활용해 **하나의 gradient**를 구하고 업데이트
3. Batch GD : 전체 데이터를 활용해 gradient를 구하고 업데이트



Batch size.

배치 사이즈가 크다면 sharp minimizer로 도달하고, 작으면 flat minimizer로 도달한다.

실험적으로 배치사이즈가 더 적으면 학습에 더 좋다.



![image-20210202101004916](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202101004916.png)

flat minimum의 특징은 미니멈 값의 변화가 적기 때문에 조금 움직여도 테스트 function에서도 낮은 값이 나온다.

sharp minimum에서는 조금만 변화돼도 test function에서 많은 변화. 즉, gerneralization performance가 떨어진다.



실험적으로 배치사이즈가 줄이면 generalization performance가 좋아진다.



## Gradient Descent Methods



GD의 단점은 lr을 잡아주는게 힘들다.

더 빨리 학습시키기 위해 여러 테크닉이 나옴 

1. momentum : 이전에 그래디언트가 어떤 방향으로 흘렀으면, 이번에 다른 방향으로 나오더라도 이전 방향을 좀 반영하자.

   ![image-20210202101425750](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202101425750.png)

   그레디언트가 계속해서 바뀌더라도 괜찮은 성능을 내게 된다.

2. Nesterov Accelerate : momentum에서는 그래디언트 계산시 현재 주어져있는 파라미터에서 계산해서 그 그레디언트를 가지고 모멘텀을 accumation 했지만,  얘는 한번 이동한 뒤 그 간 곳에서 그레디언트를 계산한 값을 가지고 accumation한다.  모멘텀으로 한번 가본다음에 그레디언트 디센트를 구해서 이동한다. (모멘텀을 그냥 이전 스템에서의 그레디언트 정도로 생각.)

![image-20210202101718377](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202101718377.png)

> 원래 U라는 함수에서 gd를 하다보면 로컬미니멈에 도달 못하고 왼쪽 오른쪽만 왓다갓다 하는데 
>
> 얘는 왼쪽에서 한단계 가면 오른쪽으로 가서 이 오른쪽에서 gd를 계산하니까 로컬미니멈 방향을 조금 알기에 좀 반영해서 업데이트



3. Adagrad : 뉴럴넷의 모든 파라미터들에 대해  이때까지 변화량이 적은 파라미터는 많이 변화시키고 변화를 많이 했던 파라미터는 적게 변화시키고

![image-20210202102232256](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202102232256.png)

G가 이 파라미터의 그레디언트가 얼마나 만이 변햇는지를 측정한 값 (제곱해서 더한)

앱실론은 0으로 나눠주기 위한

G가 계속 커지니 점점 0으로 가게 되고, 시간이 지날수록 그레디언트 변화가 없어짐.



4. adadelta : 이전 파라미터 전체를 더하지 말고, 윈도우사이즈를 잡아서 그 개수만큼만 더해서 G로 쓰자는 아이디어. 그러나 파라미터 개수 * 윈도우 사이즈 만큼의 데이터를 갖고 있어야해서 GPT-3같은데서는 할 수가 없어. 이를 막기 위한 아이디어로 만든게 adadelta. G_t가 대략 윈도우 사이즈만큼의 데이터를 더한 값을 의미 	adadelta는 lr이 없다. 그래서 잘 활용되지 않음.

![image-20210202102601076](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202102601076.png)



5. RMSprop : Adadelta에서 없던 stepsize를 넣은게 전부다.

![image-20210202103016095](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202103016095.png)



6. Adam : 그레디언트의 크기가 변함에 따라, 그레디언트의 스퀘어의 크기에 따라 adaptive하게 바꾸고 모멘텀 정보를 잘 합친게 adam

![image-20210202103308116](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202103308116.png)

하이퍼파라미터 : B1, B2, lr, epsilon





## Regularization

generalization을 잘하게 하고 싶은 것

학습을 방해하는 것이 얘의 목적.

학습을 방해하고자 하는 의미는 학습데이터에만 잘맞게 하지 말고, 테스트데이터에도 잘맞게 하기 위해

밑의 방법들을 넣어서 잘 될 수도 있꼬 ㅇ나될수도 잇지만, 잘 되더라



### Early stopping

validation error가 어느시점부터 커진다면 그때 멈추는 것.

![image-20210202103659191](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202103659191.png)



### parameter norm penalty

네트워크 파라미터 값이 너무 커지지 않게 하자.

파라미터를 제곱한뒤 더하면 어떠한 숫자가 나올텐데 이 숫자를 cost에 추가시켜 같이 줄여나가는 것

파라미터 값이 크기가 작으면 작을 수록 좋다.

뉴럴넷이 만드는 함수의 공간에서 함수를 최대한 부드러운 함수로 만들자. 부드러운 함수일 수록 GP가 높을거다라는 가정하에..



### data augmentation

데이터는 많을 수록 좋으니 있는 데이터를 활용하여 데이터 수를 늘려보자



![image-20210202103945339](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202103945339.png)

이미지의 label이 바뀌지 않는 한도 내에서 이미지를 변화시키면서 데이터를 만들어냄.

> mnist에서 6이라는 사진을 data augmentation한다고 180도 돌려버리면 9가 되니 이런건 안되는 거고



### noise robustness

왜 이걸하면 잘되는지는 의문

데이터와 뉴럴넷의 weight(파라미터?)에 noise 값을 넣는다.

![image-20210202104157433](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202104157433.png)



### label smoothing



학습데이터를 두개를 뽑아서 섞어준다.

이미지도 섞고, 라벨도 섞는다.

![image-20210202104356337](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202104356337.png)

**교수님 경험 상 mixup이나 cutmix를 활용하면 성능이 정말 잘 올라간다.**



dropout

![image-20210202104447289](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202104447289.png)

학습중에 뉴럴넷의 weight를 0으로 바꿔줌.

각각의 뉴런들이 robust한 피쳐를 잡을 수 있다. (수학적 증명은 X)



### Batch Normalization

내가 적용하고자 하는 Layer에 statistics를 정교화 시킨다

가각ㄱ의 레이어가 천개의 파라미터로 되어있다면 천개의 파라미터



레이어가 깊게 쌓일 수록 BN을 사용하면 성능이 올라간다.







## SGD vs Adam vs momentum



![image-20210202111429625](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210202111429625.png)

sgd는 10000번을 해도 잘 못맞추는데 adam은 2500번이면 충분하게 피팅된다.

adam이 빠르게 수렴하기에 이를 먼저 써보는게 좋다.

물론 더 오랜 시간 흘렀을 때 Adam보다 SGD가 더 좋은 모델을 만들 수도 있다.



모멘텀 방법은 이전의 그레디언트를 활용해서 다음번에도 활용하겠다는 것.



이전 배치에서의 정보가 현재 배치에서도 사용한다는..

그래서 한번에 더 많은 데이터를 보는 효과가 생기는 것

\> 한 배치는 사실 전체 데이터에서 엄청나게 작은 양. 좀더 봄으로써 빠르게 수렴



거기다 adam은 adaptive learning rate을 합치기에 어느 파라미터에는 lr을 늘리고 어디엔 늘리는 방법을 쓰기에 같은 base lr을 갖고 있어도 훨씬 더 빠르게 학습된다.





데이터들이 제일 큰 피크를 위주로 피팅된다. 그 이유는 loss와 이어진다.



squared loss는 큰 로스를 제곱시켜서 증폭시킨다. 그렇기에 많이 틀리는 데(차이가 큰곳)를 잘 맞추려하고, 적게 틀리는 데는 덜 집중한다. 그렇기에 outlier가 낀 데이터에 대해서 너무 맞추려고 하다보니 네트워크가 이상해지는..