# Day 6 - numpy



* numpy는 자체로도 많이 쓰이지만 이후에 사용되는 SciPy나 Pandas의 base 객체로도 활용.

* list에 비해 빠르고, 메모리 효율적

  > 메모리 효율적인 이유는 list는 python object를 가리키는 포인터들의 배열로 구성되기에

* 반복문 없이 데이터 배열에 대한 처리를 지원함 

  >  for while 같은거 안쓰기에 빠름. 
  >
  > for loop < list comprehension < numpy
  >
  > 약 1억번 loop를 돌 때, 약 4배의 차이를 보임

* 선형대수와 관련된 다양한 기능을 제공

* numpy는 c로 구현되어 있어 성능을 확보하는 대신 파이썬의 큰 특징인 dynamic typing 포기.

* concatenate 처럼 계산이 아닌 할당에서는 속도의 이점은 없다..

* C언어의 data type과 거의 유사하다.



### numpy array 

* 하나의 데이터 타입만 넣을 수 있다. dynamic typing not supported  <-- list와 가장 큰 차이점

* C의 Array를 사용하여 배열을 생성함.
* 데이터 타입이 정해져있고 개수를 정해놓기에? 메모리 공간을 잡기도 효율적?



### numpy shape

(3,4) - 3행 4열의 매트릭스

(2,3,4) - 3x4 매트릭스가 2개 있다.     

(5,2,3,4) - (2,3,4) 가 5개 있다.

> 3d-array 부터 앞으로 계속 쌓인다.



### numpy와 list의 메모리 차이

numpy array는 값이 붙어 있다.

list는 값을 직접 저장하는게 아니라 값의 주소값을 넣는다.

![image-20210126154220399](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210126154220399.png)

### Handling shape



#### reshape 

* array의 shape의 크기를 변경한다. element의 개수는 동일하다.

* reshape에서 -1의 의미는  element의 개수에 맞춰서 알아서 값을 넣으라는 뜻

  > (2,4) array가 있는데 reshape(-1,2) 를 한다면,  행의 크기는 4일 수 밖에 없으니
  >
  > (-1,2,2) 하면 -1 위치에는 2밖에 못들어오지



##### rank2 -> rank1 reshape

![image-20210126160054894](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210126160054894.png)



#### flatten 

다차원 array를 1차원 array로 변환

> reshape의 기능 중 하나를 따로 빼서 가져온 것.



#### slicing

* list와 달리 행과 열 부분을 나눠서 slicing이 가능함.

* matrix의 부분 집합을 추출할 때 유용함.

```python
a[:,2:] # 전체 행의 2열 이상의 값

a[1,1:3] # 1행의 1열 ~ 2열

a[1:3] # 1 행 ~ 2행 전체

a[:,::2] # 전체 행의 전체 열 중 2칸씩 뛰면서  
```



### creation function



#### np.zeros(shape, dtype, order)

```
np.zeros(shape=(10,), dtype=np.int8)
```



#### np.ones(shape, dtype, order)

```
np.ones(shape=(10,), dtype=np.int8)
```



#### np.emtpy(shape, dtype)

shape만 주어지고 비어있는 ndarray가 생성 (메모리 초기화 하지 않는다)

메모리를 초기화하지 않기에 이전에 어떤 값으로 할당되었거나, 프로그램의 일부였던 값들이 그대로 가져와진다.



#### something_like

기존 ndarray의 shape 크기 만큼 1,0 또는 empty array를 반환

>  np.ones_like(matrix) # matrix 와 같은 shape에 1값을 채워서 반환 



#### np.identity 

단위 행렬을 생성함

```
np.identity(n=3, dtype=np.int8)
```



#### np.eye

대각선이 1인 행렬, k값으로 시작 index를 변경할 수 있다.

```python
np.eye(3) # np.identity(3)과 같다.

np.eye(3,5,k=2) # 3 by 5 행렬이 만들어지는데 (0,2)이 단위행렬 시작 지점. 

[0,0,1,0,0]
[0,0,0,1,0]
[0,0,0,0,1]
```



#### np.diag

생성되어 있는 행렬에서 대각 행렬의 값만 추출함 

```
np.diag(matrix) # matrix의 대각행렬 값을 추출 
nnp.diag(matrix, k=1) # 0,1부터 시작해서 대각행렬 값을 추출.
```



#### random sampling

데이터 분포에 따른 sampling으로 array를 생성 (uniform, normal distribution 등등)

```
np.random.normal(0,1,10) # 모수값이 0과 1인 정규 분포에서 10개 추출
```



### operation function

sum, std, var, mean 등등



#### axis

operation fuction을 실행할 때 기준이 되는 dimension 축.

이 축방향으로 연산을 한다고 생각하면 될듯. sum하면 이 축방향에 있는 값을 모두 더함.

> 연산을 어떻게 지원하는지 알려면 이 개념을 알아야 함



2차원에서는 행이 axis=0, 열이 axis=1, 3차원에서는 행렬 개수가 axis=0, 행이 axis=1, 열이 axis=2



sum(axis=1) 하면 axis=1인 열 방향으로 값을 모두 더함. 즉 같은 행에 있는 값을 모두 더한 array



(2,3,4) - (axis=0, axis=1, axis=2)

sum(axis=0) 하면 (3,4)의 결과가 나오는거지.

sum(axis=2) 하면 (3,3)의 결과가 나오고.



axis 방향으로 값을 합친다.



```
qw = np.random.randint(5, size=(10,5))
array([[0, 1, 0, 1, 3],
       [0, 0, 4, 2, 0],
       [0, 0, 4, 4, 2],
       [3, 0, 1, 1, 4],
       [0, 3, 2, 2, 3],
       [1, 3, 2, 4, 1],
       [3, 0, 2, 1, 0],
       [3, 2, 2, 3, 4],
       [3, 0, 4, 2, 1],
       [3, 4, 4, 2, 0]])

np.max(qw,axis=1)
array([3, 4, 4, 4, 3, 4, 3, 4, 4, 4])
```

axis 방향으로 나머지 값들을 합쳐준다.

그래서 axis=1이면 열방향으로 이동하면서 







### concatenate



![image-20210126165256015](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210126165256015.png)





#### vstack (vertical stack)

여러 row를 붙히는

```
a = np.array([1,2,3])
b = np.array([4,5,6])
np.vstack((a,b)) 
# 하면 [[1,2,3],[4,5,6]])
```

이 작업은 np.concatenate((a,b), axis=0)과 같다



#### hstack (horizontal stack)

```
a = np.array([1,2,3])
b = np.array([4,5,6])
np.hstack((a,b)) 
# 하면 [[1,2],
       [3,4],
       [5,6]]
```

이 작업은 np.concatenate((a,b), axis=1)과 같다



#### 축을 하나 늘리는 방법

b.reshape(-1,.2) == b[np.newaxis:2]



#### broadcasting

shape이 다른 배열 간 연산을 지원하는 기능

서로의 shape이 같지 않을 경우 앞이나 뒤에 있는 row나 col에 크기를 늘려 맞춰줌.

![image-20210126170541917](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210126170541917.png)



기본적으로 numpy는 shape가 같으면 element-wise 연산을 한다.

같은 위치에 있는 element 끼리 계산



### comparison

```
a = np.arange(6)
a < 4 # [T,T,T,T,F,F], 여기서도 broadcasting

np.any(a < 4) # T
np.all(a < 4) # F
```



#### np.where

```
a = np.array([-1,0,1])
np.where(a>0, 3, 2) # a의 원소들 중 0보다 크면 3을, 작으면 2를 넣는다.
# => [2,2,3]

np.where(a>0) # 5보다 큰 원소들의 index 값을 반환
# => [2]
```

 

#### argmax & argmin

array 내에서 가장 큰 or 작은 값의 index를 반환

```
np.argmax(a, axis=1)
# 축방향으로 가면서 max 값의 index 반환
```



#### argsort

array 내에 있는 값이 작은 순서대로 index를 반환.

```
a = np.array([[1,2,4,5,8,78,23,3]])
a.argsort()
# => [0,1,7,2,3,4,6,5]
```



#### boolean inedx

boolean 값이 있는 ndarray를 인덱스에 넣으면 true에 해당하는 값만 뽑아냄

```
a = np.array([1,4,0,8])
a[a>3]
# => [4,8]
```



#### fancy index

numpy는 array를 index value로 사용해서 값 추출

```
a = np.array([5,6,7,8,9])
b = np.array([0,0,1,3])
a[b] # == a.take(b)
# => [5,5,6,8]
```



### numpy data i/o



#### txt 파일

```
np.loadtxt("./test.txt")
np.save("./test.csv", a, delimiter=",")
```



#### npy 파일

```
np.save("test.npy", arr=a)
np.load(file="test.npy")
```



