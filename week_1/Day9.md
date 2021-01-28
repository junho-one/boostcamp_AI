# Pandas-2



## Groupby

groupby에 의해 만들어지는 데이터는 Series 타입이다.

인덱스가 여러개 있을 뿐, 값은 하나의 컬럼에 있다.



![image-20210128095254951](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128095254951.png)



```[[
df.groupby("Team")["Points"].sum()
df.groupby(["Team","location"])["Points"].sum()
```

두개 이상의 column을 넣어줄 수도 있다.



### unstack

groupby해서 나온 결과를 테이블 형태로 변환해줌. (stack()하면 반대 연산)

reset_index와 같은 연산인 듯.



```
h_index = df.groupby(["Team","Score"])["Points"].sum()
h_idex.unstack()
```



### swaplevel

groupby을 여러개 컬럼을 통해서 수행할 때, 인덱스가 여러개가 된다. 

각 인덱스는 레벨이 있는데, 그 레벨의 순서를 바꿔주는 함수



### sort_index

index level 기준으로 정렬해준다.

```
h_index.sort_values(level=1)
```



### Groupby - grouped

* Groupby에 의해 Split된 상태만 추출이 가능하다.이 상태를 grouped라 한다.

```
grouped = df.groupby("Team")

for name, group in grouped :
	print(name, group)

grouped.get_group("Devils")
```

![image-20210128100409167](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128100409167.png)



group이라는 값 자체가 dataframe

grouped를 통해 세 가지 유형의 apply가 가능함.



#### Aggregation 

요약된 통계정보를 추출해 줌

```
grouped = df.groupby("Team")
grouped.agg([np.sum, np.mean]) # 팀 별로 컬럼에 sum, mean 함수를 적용한다.
```



#### Transformation 

Aggregation과 달리 key값 별로 요약된 정보가 아님

개별 데이터의 변환을 지원



```
grouped = df.groupby("Team")
grouped.transform(lambda x : x.max())
```

Team 별로 묶여 있을 때, 모든 값을 Team 별 max 값으로 치환

> Riders 팀에 Rank가 1,2 Points가 8,7 Yea가 14,15라면 Riders 팀의 값은 모두 2,8,15가 된다.

grouped된 상태에서 각 컬럼 별로 모든 값에 동일한 연산이 적용된다.



```
score = lambda x : (x - x.mean()) / x.std
grouped.transform(score) # 여기서 mean은 각 팀 별 mean
```

각각 컬럼 별로 실행을 시켜주되 개별 데이터에 적용 시킬 때 사용.

즉, 개별 데이터가 정규화되는 효과.



#### filtration

특정 정보를 제거 하여 보여주는 필터링 기능

특정 조건으로 데이터를 검색할 때 사용

>  굳이 이렇게 안뽑아도 되간 하는데?



```
df.groupby("Team").filter(lambda x : x["Points"].sum() > 1000)
# Rider라는 팀, Kings라는 팀 등등이 생길텐데, 그 팀의 point의 합이 1000 이상인 팀의 데이터만 나와라
```



### Pivot Table

excel에서 보던 Pivot table과 동일

Index 축은 groupby와 동일함

Column에 labeling 값을 추가하여 

value에 numeric type 값을 aggregation 하는 형태 



### Crosstab

network 형태의 데이터. a와b가 얼마 만큼의 상관이 있다 등등? -> movie_rating

> A가 B에 몇점을 줬다. A-B : 5

이런 형태의 데이터를 다룰 때 crosstab을 사용할 수 이싿.



### Merge

SQL에서의 join으로 생각하면 된다.

어떤 기준점을 통해 두개의 데이터를 합침. (기준점 데이터 값이 같다면)

```
pd.merge(df_a, df_b, on="subject_id") # a와 b에 있는 subject_id를 통해 합친다.
pd.merge(df_a, df_b, left_on="subject_id", right_on="id", how="left") 
```



### Concat

```
pd.concat([df_a, df_b]) == df_a.append(df_b)
```

밑으로 붙어지는 상황 (row 방향으로)



```
pd.concat([df_a, df_b], axis=1) 
```

옆으로 붙어지는 상황 (col 방향으로)





# 확률론



![image-20210128174318558](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128174318558.png)





**데이터에서 관찰되는 분포와 모델 예측의 분포의 차이를 최소화하는 방향으로 학습한다.**

이를 확률론 기반으로 해석하기에 확률론이 중요하다. 이를 알아야 문제에 맞는 손실함수를 적절히 사용할 수 있다.

> 예측이 틀릴 위험(risk)을 최소화하도록 데이터를 학습하는 원리는 통계적 기계학습의 기본 원리









## 확률 분포

데이터를 표현하는 초상화

데이터 공간에서 데이터를 추출하는 분포.

확률 분포를 통해 데이터를 초상화를 그릴 수 있기에  데이터를 해석하는데 중요한 도구로 사용된다.

확률변수는 확률분포 D에 따라 이산형, 연속형 확률 변수로 구분된다.



**이산형 확률변수**에서는 X가 가능한 **모든 경우의 수를 고려**한다.

그렇기에 P(X=x)  확률변수 X가 x가 될 확률을 모두 더하는 형태로 확률 분포를 모델링한다.

![image-20210128175138128](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128175138128.png)



**연속형 확률변수**는 확률변수 X가 x가 될 확률을 구하는건 불가능하다. 

데이터 공간에 정의된 확률변수의 밀도 위에서의 적분을 통해 모델링한다.

![image-20210128175244216](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128175244216.png)



밀도 함수는 확률이 아닌 누적확률분포의 변화율로 생각해야함??

P(X)는 누적확률분포의 변화율을 모델링하는 개념??



이산형, 연속형 두 확률변수에서 확률분포를 구하는 모델링 방식에 차이가 있따.

> 모든 확률변수가 이 두가지로 구분되는 것은 아니다.





확률변수에 따라 확률 분포를 다르게 모델링

전체 데이터 x와 y가 주어지면 산정할 수 있는데, 이를 결합분포 P(X,y)라고 한다.

![image-20210128175834976](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128175834976.png)



파란 점이 연속 확률 변수처럼 보이는 확률 분포 모양을 띄지만

빨간 칸막이로 나누면 이산 확률 분포처럼 생각할 수 있다.



> x가 몇번째 칸에 있을 때, y가 1인 파란 점의 갯수를 카운팅하면 
>
> 현재 주어진 데이터의 결합분포를 가지고 원래 확률분포 D를 모델링할 수 있다.



원래 확률분포 D가 연속이냐 이산이냐에 따라서 결합분포 P(x,y)를 연속이냐 이산이냐 결정하는게 아님

결합분포를 산정할 때는, 원래 확률분포에 상관 없이 모델링 할 수 있따.





## 주변확률분포

결합분포가 주어져 있는 상황에서 각각의 입력 X에 대해 y텀에 해당하는 것들을 더해주거나 (이산)

적분해주면 (연속) 입력 X에 대한 주변확률 분포가 나온다.

주변확률분포는 x에대한 정보를 주지 y에 대한 정보를 주지는 않는다.



![image-20210128215931237](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128215931237.png)



오른쪽 히스토 그램을 보면

P(x,y)로 주어진 결합확률 분포에서 y가 1이든지 2이든지 상관없이 각 칸에 해당하는 점들의 개수를 세서 빈도를 계산하여 X값에 따른 분포를 구할 수 있다. (y에 따른 값을 구한건 아니지!) 이런걸 주변확률분포라고 한다.



결합확률분포를 각각의 y에 대해서 모두 더해주거나 적분을 해주면 유도를 할 수 있다.

주변확률분포는 x에 대한 정보를 측정할 수 있기에 이를 통해 많은 통계적 분석을 할 수 있다.





## 조건부확률분포

y가 주어져있는 상황에서 x에 대한 확률분포

주변확률분포는 y가 1이냐 2이냐에 상관 없이 구했었지만 

얘는 y가 1인 경우에 해당하는  점들만 카운팀



![image-20210128181220018](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128181220018.png)

이 분포는 y가 1로 주어져있는 경우의 확률 분포이기 떄문에 y가 1인 조건부가 주어졌을 때의 확률 분포

조건부 확률 분포는 입력 x와 출력 y사이의 관계를 모델링



P(X|y)

y가 조건부로 주어졌을 때 X의 확률 분포는 특정 출력값 특정 클래스가 주어진 조건에서 데이터의 확률 분포를 보여주기때문에 두 입력과 출력 사이의 통계적 관계를 모델링할 때, 혹은 예측 모형을 세울 때 사용한다.

> 주어진 클래스에 대해 X의 분포가 어떤 식으로 형성됐는지 살펴보기 위해서는 주변 확률 분포 보단 조건부 확률 분포를 사용



*y가 주어졌을때 x들이 어떤 분포를 갖는지 알면,  x가 들어왔을 때 y가 뭔지를 알 수 잇으니?* 



조건부확률은 기계학습에서 매우 중요 'ㅇ'



P(y|X)는 입력변수 X가 들어왔을 때, 정답이 y일 확률 

> 연속확률분포에서는 P(y|X) 또한 확률이 아니고 밀도로 해석.







## 기대값 



기대값을 이용해서 분산이나 첨도, 공분산 등을 구할 수 있다.

연속확률변수냐 이산확률변수냐에 따라 적분을 취하거나 급수를 취하거나 계산 방식이 다르다.





![image-20210128183115588](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128183115588.png)



조건부 기대값이  L2 norm(y-f(x)) 을 최소화하는 함수 f(x)와 같다

회귀 문제에서 조건부 기대값을 사용하는 이유는 목적식으로 사용하는 l2 norm을 최소화하는 함수이기에



## 몬테카를로 샘플링



![image-20210128183830004](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210128183830004.png)



x에 샘플링한 데이터를 대입하고 이 f(x)를 구한 뒤 이 값들을 산술평균 해주면 

이 산술평균 값이 우리가 원하는 기대값에 근사한다.



확률 분포를 몰라도 샘플링만 가능하다면 기대값을 뽑아낼 수 있기에 기계학습 방법에서 매우 많이 쓰인다. 





X ~ P(X) P(X)에서 분포되는 X