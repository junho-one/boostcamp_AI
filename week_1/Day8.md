# Day 8 - Pandas

* 구조화된 데이터의 처리를 지원하는 Python 라이브러리

* 엑셀 시트 처럼 테이블 형태로 정리되어 있는 데이터를 다루는데 최적화된 도구



column : attribute, feild, feature

row : instance, tuple



seperation으로 \s를 쓰면 띄어쓰기. 

\s+는 띄어쓰기가 여러개 있을 수 있다.



### Series

series는 numpy에 있는 array의 래퍼이다. 판다스에서 쓰기 위해 series로 변환한 것. (Subclass of np.ndarray)

한가지 np array와 다른점은 인덱스 값이 있다. 숫자로 할 수도 있고, 문자로도 할 수 있고.

series_data.values 하면 나오는게 np.ndarray가 나온다.



list와 dictionary 모두 Series 형태로 바꿀 수 있다.



series와 dataframe은 항상 인덱스가 기준이 된다. data가 7개 들어오고 index_list가 10개가 들어오면 길이 10의 series를 만들고, 없는 값은 nan으로 처리한다.



### DataFrame

Series를 모아서 DataFrame이 된다.



#### indexing



##### loc - index location 

인덱스가 문자일 때, 해당 문자 인덱스에 접근하는 방식



##### iloc - index position 

인덱스를 숫자로 생각하고 숫자로 접근하는 방식



인덱스 번호가 [9,8,7,6,5,4,3,2,1] 이라면 

df.loc[:3]은 [9,8,7,6,5,4,3]

df.iloc[:3]은 [9,8,7]



#### handling

df.age > 40 하면 boolean 타입의 series가 만들어지지. (numpy 마냥)



##### del df["debt"] 

컬럼의 삭제보단 아예 메모리 주소를 삭제하는 방식



##### df.drop("debt", axis=1) 

axis=1이니까 컬럼 방향으로 삭제한다. debt 라는 feature가 삭제됨

```
df.drop(6) # 6번째 행 삭제
df.drop("account", axis=1) # account feature를 삭제
```



del 은 아예 debt가 df에서 사라지고, drop은 debt가 사라진 새로운 dataframe?이 반환

del은 바로 메모리가 해제 되지만, drop은 흠.. datafram도 list처럼 데이터 저장 위치를 가리키는 포인터들의 집합이라면 지정하는 포인터들의 변화. inplace 느낌?

 

#### df["account"] 과 df[["account"]] 

df["account"] 하면 feature vector가 Series 형태로 뽑히지만, df[["account"]] 하면 DataFrame 형태로 뽑힌다.

df[[0,1,2]] 하면 index가 0, 1, 2인 row 3개가 뽑힌다.

> 일관성이 없어 보이는 부분. 같은 형식인데 어떨 땐 col을 기준으로 뽑고 row를 기준으로 뽑고





##### 여러가지 데이터 접근 방식.

![image-20210127121625318](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210127121625318.png)



#### inplace

dataframe에 사용하는 여러가지 함수들은 dataframe 자체가 변하는 경우는 잘 없다.

데이터 분석단계에서 dataframe 값은 웬만하면 유지하려고 노력한다.

**하지만 값을 변경해야 하는 경우에는 inplace=True를 하면 변경된 값이 들어간다.**



#### operation

dataframe 간의 연산(+,-...)은 index를 기준으로 한다.

한 dataframe에만 있는 index 값은 nan 값이 들어간다. 이때 fill_value를 지정해주면 nan 위치에 원하는 값을 넣는다.



series와 dataframe를 계산할 때 axis를 지정해 broadcast를 할 수 있다.

df.add(series, axis=0) 하면 axis=0 즉, 행 방향으로 브로드캐스트가 일어난다.





#### map



#### replace

map 함수의 기능중 데이터 변환 기능만 담당

```
df.sex.replace({"male" : 0, "female" : 1})
df.sex.replace(["male","female"],[0,1], inplace=True)
```



#### apply

map과 달리, series 전체에 해당 함수를 적용

> map은 series 한개에 적용하는 것이고, apply는 전체 series에 적용하는 것이고.



```
df.apply(lambda x : x*5) # df에 있는 모든 column에 x*5 적용
df.apply(sum) # (=df.sum()) , df의 모든 컬럼 별 합
```

 

#### applymap

series 단위가 아닌 element 단위로 모든 series에 함수를 적용함.

series 단위에 apply를 적용시킬 때와 같은 효과.

series에 applymap 하는건 map과 같은 효과



```
df["Name"].map(lambda x : x+"G") # Name series에만 적용
df.apply(lambda x : x+"G") # 모든 series에 적용
df.apply(sum) # 모든 series에 적용하면서 sum 
df['Name'].map(sum) # 이건 안된다. 
```



apply는 series 단위이기에 sum이 되지만, map은 element 단위기 때문에 그런듯??







df.isnull().sum() : nan 값 개수



통상 index는 숫자로 지정하고, feature는 문자열로 지정해서 혼란 방지.

account_series[account_series < 30000]





# 학습



![image-20210127131837889](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210127131837889.png)

위 식의 의미는 n개의 d차원을 갖는 데이터를 p차원의 데이터로 선형변환



위에서 화살표에 해당하는 것이 가중치 행렬 W이다.

X라는 행벡터를 O라는 행벡터로 연결하게 될 때, p개의 모델을 만들어야 한다.

x1 에서 o1 ~ op까지 연결되는 화살표 p개가 d개 있으니 p * d 만큼의 화살표가 필요하다.

이게 바로 가중치 행렬 W (d*p)





## softmax

* 모델의 출력을 확률로 해석할 수 있게 변환해주는 연산

* 분류 문제를 풀 때 선형모델과 소프트맥스 함수를 결합하여 예측한다.



출력할 때는 확률 값으로 만들 필요 없이 최대값만이 예측 클래스가 되는 one-hot encoding를 해주면 된다.

>  예측 : one_hot_encoding(o)
>
>  학습 : softmax(o)



softmax를 취함으로써 선형모델의 결과물을 마치 원하는 의도로 바꿔서 출력할 수 있다.



활성화 함수는 비선형 함수로써 선형 모델로 나온 출력물의 각각 원소에 적용됨

softmax는 출력물의 모든 값을 고려해서 출력하지만, 활성화함수는 해당 값만을 고려.

> 인풋이 벡터냐, 실수값이냐?



## 활성화함수

* 실수값을 입력받아 실수값을 뱉는 비선형 함수

* 활성화함수를 쓰지 않으면 딥러닝은 선형모형과 차이가 없다.

* 오늘 날엔 ReLU를 많이 사용 



### 선형함수의 의미

선형성을 갖는 함수.

선형성이란 아래 식을 만족하는 것
$$
f(ax+b) = af(x) + bf(y)
$$

$$
ex)\,\,f(x) =x\,일때\;\;f(ax+by)=ax+by\;를\,성립한다.\;\; 그렇기에\,f(x)=x는\, 선형함수
$$



이 선형모델과 활성화 함수의 조합을 여러층으로 구성하는게 딥러닝 모델.



### 층을 여러개 쌓는 이유

더 적은 뉴런(파라미터)를 가지고 더 복잡한 패턴을 표현할 수 있기에.



이론적으로는 2층 신경망으로도 임의의 연속함수를 근사할 수 있다.

> 이를 universal approximation theorem

이론적으론 보장해 주지만 실제로는 무리가 있다.



층이 깊을수록 목적함수를 근사하는데 필요한 뉴런의 숫자가 훨씬 빨리 줄어들어 좀 더 효율적으로 학습이 가능하다.

층은 적게하고, 매 층을 넓게 만들어 (한 층을 이루는 뉴런들의 개수가 많게) 뉴럴넷을 만들 수 있지만 효율적이지 않은 거지. 층이 깊어지면 더욱 적은 뉴런(파라미터)로 가능하니까



층이 깊으면 복잡한 함수 함수를 근사 할 수 있지만, 최적화가 더 쉽지는 않다. 층이 깊어지면 깊어질수록 딥러닝 모델의 학습이 힘들어진다.



### 역전파

경사하강법을 사용하려면 각각의 가중치에 대한 그레디언트 벡터를 계산해야 경사하강법을 사용할 수 있다.

>  앞에서 선형회귀에서 B에 해당하는 그레디언트 벡터를 계산해서 업데이트 한거처럼 



딥러닝에서 각 층에 존재하는 파라미터들에 대한 미분을 계산해서, 그 값들을 가지고 파라미터 업데이트



이 가중치 행렬의 모든 원소와 y절편 개수 만큼 경사하강법이 적용된다. (많다..)



선형모델에서 경사하강법을 적용할 때, 한 층에 대해서만 적용하는 원리이기 때문에 그레디언트 벡터를 동시에 계산할 수 있었지만, 층별로 순차적으로 계산하기 때문에 모든 층에 그레디언트 벡터를 한번에 계산할 수 없고, 순차적으로 해야함.



각 층 파라미터의 그레디언트 벡터를 계산한 후에 위층부터 아래층까지 역순으로 그레디언트 벡터를 전달하면서 계산하는 원리



![image-20210127135210860](C:\Users\JH\Desktop\aiboost\image-20210127135210860.png)



역전파 알고리즘은 합성함수 미분법인 연쇄법칙 기반 **자동미분**을 사용한다.



딥러닝에서 각 뉴런에 해당하는 값을 텐서라고 표현하는데, 이 각각의 텐서 값이 컴퓨터의 메모리에 저장해놔야 역전파가 작동한다. 그래서 순전파 보다 역전파가 더 많은 메모리를 사용한다. (이게 미분하기에)



![image-20210127135733211](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210127135733211.png)



근데 결국 각 파라미터의 미분값인  그레디언트 벡터는 결과값에 이 파라미터가 손실함수에 미치는 영향??

L = 손실 함수

손실함수를 o로 미분하고, 이를 hr로 미분하고 해서 최종적으로 구하고 싶은 dL/dW_ij

미분값을 구해야 함수값이 작아지는 방향을 알고, 이동시키니까





### L2와 L1의 미분값의 차이

L1 norm으로 loss fuction을 잡고 미분하게 되면 결국 수렴하는 방향은 한정적이다.

L2 norm은 여러 각도에 대해 수렴하는 방향이 다르다.

> 원을 그렸을 때, 마름모가 생기는 L1과 원이 생기는 L2를 생각하면 된다.
>
> 원에서는 다양한 미분값이 생기지만 마름모에서는 4개의 미분값



L1와 L2 자체가 normal distribution과의 관계와도 영향이 있고....??

