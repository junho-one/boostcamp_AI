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











