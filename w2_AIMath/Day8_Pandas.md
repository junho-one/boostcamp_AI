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