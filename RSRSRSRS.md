추천시스템 공부 -> 관련 공부 -> 카카오 공부 





다음 뉴스를 초개인화?

주식 -> 주식관련된 뉴스들 모아서

취업 -> 취업관련 뉴스들

> 인기차트 같은게 문제가 되는 것도 집단의 주도하에 모두에게 보이는 키워드가 바뀜. 조국사건 때 실검전쟁.
>
> 정치적 수단으로 이용되기 때문.. 정치적으로 끼게 되면 반은 우리편이지만 반은 적이다.





기업을 사전조사를 한다 -> 그 기업 관련 뉴스들...



개인의 선호도 찾기.

1. 선호도 키워드를 사람에게 입력하게 한다.

2. 자주 보는 뉴스에서 관심 키워드를 뽑아낸다.
3. 다른 매체에서 데이터 가져옴
   * 카카오톡 오픈채팅방을 보고 관심이 있는게 뭔지를.





뉴스에 키워드 추출

1. 기자들에게 키워드를 박으면 추천되어 많이 보여진다는 혜택을 주고 키워드 받음.

2. 텍스트에서 정보 추출, 키워드 추출.

   * 빈도수로 
   * ner
   * Text Rank(https://lovit.github.io/nlp/2019/04/30/textrank/)
   * 다음 뉴스에서 문서 요약 쓰면 그걸로??  (추론식 요약은 좀 과한듯. 추출식 요약으로 가능할듯)

   



------------------



# 추천 시스템

유저의 선호도 및 과거 행동을 바탕으로 개인에 맞는 관심사를 제공하는 시스템

> 비디오, 쇼핑몰, 뉴스, 금융 상품



## 1. Content-based Filtering

```
source code : https://github.com/junho-one/recommendation/blob/master/Content-based%20Filtering.ipynb
```



유저가 관심있는 아이템의 속성을 분석하여 이와 유사한 아이템을 추천해주는 것.

해당 아이템의 도메인을 활용한다.

CF와는 다르게 다른 유저의 정보가 사용되지 않는다.

> 내가 산 옷과 비슷하게 생긴 옷 추천, 관련된 기사 추천
>
> 음악을 분석하여 장르, 비트, 음색 등 다양한 특징을 추출하여 이를 분석하고 유사한 곡을 추천



![img](https://images.velog.io/images/jinseock95/post/7afca98a-1379-424d-8817-d182960dd3a0/image.png)



**아이템의 feature를 잘 추출하는 것**이 중요하고 (TF-IDF, Word2Vec 같은 Feature Extraction 방법론)

추출된 feature를 통해 아이템을 비교할 **유사도를 선택하는 것**이 중요하다



### 과정

1. 컨텐츠 분석 : 비정형 데이터로부터 관련 있는 정보를 얻는 작업. feature extraction, vector representation 등의 작업을 수행한다.
2. 유저 프로필 파악 : 유저가 선호하는 아이템과 취향을 파악하는 작업. 머신러닝과 같은 알고리즘을 통해 유저 데이터를 일반화한다.
3. 유사 아이템 선택 : 가장 적절한 아이템을 선택하는 작업. Cosine Similarity 등을 사용하여 유저 프로필과 가장 관련 있는 아이템을 선택한다



### 장점 

* 추천 대상 고객의 선호도를 파악하기 위해 자신만의 과거 행동 데이터가 이용되기에 다른 사용자의 정보가 부족해도 유용하게 활용된다.

* 아이템에 대한 평가 데이터가 없더라도 아이템의 속성을 파악하여 유사도를 파악할 수 있다. 한번도 이용하지 않은 아이템도 추천 리스트에 포함될 수 있다.

  > cold start 문제가 없다.



### 단점

* 데이터 특성을 추출하는 과정이 어렵다. 

* 고객의 독립적인 정보만을 활용하기에 과거의 유저가 봤던 유형의 아이템만 추천한다는 한계. 추천 후보의 다양성이 보장되지 않는다.

  > 과도한 특수화

* 새로운 유저는 유저 프로필이 존재하지 않아 추천이 어려움



컨텐츠를 유형별로 clustering.



### Feature Extraction



#### 1.1 Count vectorization

문서집합을 입력으로 받아 들어온 모든 개별적인 단어를 각각의 index에 매핑시킨다.

문서 내에 해당 단어의 개수가 특정 index의 값이 된다.

즉, 들어온 문서집합의 개별적인 단어의 개수가 출력 벡터의 차원이 된다.

>  ["i am hadsome guy", "the guy is beautiful"] 가 들어온다면 개별적인 단어로 "I","am", "handsome","guy","the", "is","beautiful" 이 개별적인 단어로 출력 벡터 차원은 7차원이 된다.
>
> ["i am hadsome guy"] ==> [1,1,1,1,0,0,0]
>
> ["the guy is beautiful"] ==> [0,0,0,1,1,1,1] 이 된다.  
>
> guy의 idx는 3



#### 1.2 TF-IDF

TF-IDF는 모든 문서에서 자주 등장하는 단어는 중요도가 낮다고 판단하고, 특정 문서에만 등장하는 단어는 중요도가 높다고 판단한다. TF-IDF 값이 크면 중요도가 높은 것이다.

IDF를 구해 각 단어들에 중요도를 매기고, 위에서 만든 카운트 벡터의 단어 빈도수(TF)에 그 단어의 IDF를 곱해줌으로써 벡터를 만든다.



TF-IDF = Term Frequency * Inverse Document Frequency



##### 1. TF(d,t) Term Frequency : 특정 문서 d에서의 특정 단어 t의 등장 횟수

그 용어가 ducoment에 얼마나 자주 등장했나? 얼마나 그 document와 연관됐나?



##### 2. DF(t) : 특정 단어 t가 등장한 문서의 수 

특정 단어가 각 문서에서 몇번 등장했는지 관심을 가지지 않으며 오직 특정 단어 t가 등장한 문서의 수에만 관심.



##### 3. IDF(d,t) : df(t)에 반비례하는 수 

![image-20210206232713886](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210206232713886.png)

DF에 역수를 취해주면서 분모에 1을 더해주고 log를 취함.

1을 더해주는 것은 분모가 0이되는 것을 방지해준다. log를 사용하지 않으면 총 문서의 수 n이 커질수록 IDF값이 기하급수적으로 커진다.

> 자주 쓰이는 단어들은 희귀한 단어들에 비해 수십배 수백배 많이 쓰인다. 이 격차를 줄이기 위해 log. 



즉, 얼마나 적은 documents가 이 용어를 가지고 있나? 특정 용어가 다른 documents에서 많이 등장할수록 IDF value는 작아진다. 즉 어느곳에나 등장하는 용어는 관심 없고, 드물게 등장하는 용어에만 관심이 있다. IDF를 통해 흔한 용어들의 중요도를 강등시키고, 핵심 단어들의 중요도를 올린다.

> "하다", "아니다" 이런 건 별 의미가 없을테니 (모든 문장에서 많이 나와서)





TF-IDF를 통해 item을 하나의 vector로 표현하고 clustering 알고리즘을 통해 item을 몇 종류의 cluster로 나눈다.

이렇게 유저가 콜라를 좋아한다면 같은 클러스터에 있는 사이다도 추천해준다.



장점

* 간단하다.



단점 

* 문서가 커지면 차원이 너무 커진다.
* sparse하지 않을가?
* BoW 방식에 기반을 두기에 텍스트 내에서의 위치, 의미 등을 잡아내지 못한다.




#### 1.2 Word2Vec

단어를 벡터로 매핑시킨다.

NNLM(Neural Network Language Model, 이전 단어 sequence로 다음 나올 단어 예측), LSA 알고리즘에 비해 대용량 데이터를 매우 빠르게 학습할 수 있다.



##### CBOW

주변에 있는 단어들을 가지고, 중간에 있는 단어를 예측하는 방법.

##### Skip-gram

중심 단어를 통해 주변 단어를 예측하는 방법





![image-20210207002235518](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210207002235518.png)

네트워크 구조는 여러 단어들을 One-hot 형태로 입력받아 Weight를 곱해준 후 (이때 하나의 Matrix형태?)

Softmax를 취해서 특정 단어를 예측해낸다.



주변 단어의 원핫벡터가 dense vector로 변환되고 중간 단어를 예측하는 수식

![image-20210207002636384](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210207002636384.png)

![image-20210207002858661](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210207002858661.png)

이렇게 구한 아웃풋 단어와 실제 단어 간의 크로스엔트로피를 구해 백프로퍼게이션을 해준다.



skip-gram에서는 은닉층 좌우로 반전 되면 된다. 즉, 입력층이 한개, 출력층이 여러개가 나오는 네트워크



각 단어들을 word2vec에 보낸 뒤 모든 단어를 평균낸 벡터를 구한다. 이를 하나의 아이템 벡터로 이용하고

아이템 벡터간 유사도를 구해서 추천해준다.

그러나 TF-IDF가 이러한 avg word2vec 방식보다 잘 된다는 말이 있다.



### Hierarchical softmax, negative sampling

이게 없으면 H(은닉층 노드수) x V(단어 수)의 시간복잡도가 나으논데 Hxlog(V)로 개선





song2vec





#### 1.3 latent Vector









## 2. Collaborative Filtering

유저-아이템의 관계로부터 도출되는 추천 시스템

아이템에 대한 정보(feature) 없이도 사용 가능하다.

'특정 아이템에 대해 선호도가 유사한 고객들은 다른 아이템에 대해서도 비슷한 선호도를 보일 것'이라는 가정을 바탕으로 사용자 혹은 아이템간 유사도를 기반으로 선호도를 예측하는 방법

이렇게 비슷한 유저 혹은 비슷한 아이템 끼리 협력해서 필터링하기에 CF



### 장점

* 추천대상이 되는 고객과 취향이 비슷한 사용자를 선정하여 선호 아이템을 추천해주기에 아이템의 다양성이 보장될 수 있다.
* domain knowledge가 필요없다.



목표는 user-item interaction을 matrix 형태로 표현하고, 비어 있는 부분을 채우는 것

이 문제를 matrix completion이라고 함.



implicit feedback이라면 interaction이 있는 곳을 1로, 없던 곳을 0으로 채운다.

explicit data에서는 rating 안에 positive feedback, negative feeback 모두를 담고 있지만, 

implicit feedback은 오직 positive feedback 밖에 없기에 'missing data'를 모두 잠정적인 negative feedback으로 보고 0으로 채운다. 그래서 목표가 빈공간을 채우는 것이 아니라 주어진 matrix에서 사용자의 선호 패턴을 알아내는 것.



CF for implicit : https://velog.io/@vvakki_/Collaborative-Filtering-for-Implicit-Feedback-Datasets-%EB%85%BC%EB%AC%B8-%EB%A6%AC%EB%B7%B0







유사도 계산에 KNN과 pearson correlation



**Pearson - Cosine** 

Cosine similarity는 user나 item의 평균 rating을 계산하지 않아도 되기 떄문에 계산적인 측면에서 pearson correlation 보다 더 효율적이다. 하지만 특정 사용자의 점수 기준이 너무 높거나 낮거나 또는 특정 아이템이 받는 점수가 평균적으로 너무 높거나 낮거나 할 때 유사도가 계산이 잘 안된다.

>  어떠한 두 아이템의 평가가 [5,5,5,5,5] 와 [1,1,1,1,1]  이면 둘간의 유사도는 1이다. 그래서 pearson이나 보정된 코사인 유사도 사용 (보정된 코사인 유사도에서는 사용자의 평균값을 뺴주면서 어느정도 해결)





또한 문제는 두 아이템을 평가한 유저가 한명 뿐이라면 유사도가 1이 나온다.

이렇게 적은 데이터에 추천 정확도가 떨어지기에 5명 이상이 평가한 데이터에만 유사도를 구하는 방법도..



사용자 기반 vs 아이템 기반

대부분은 아이템 기반 CF를 활용한다.

유저가 아이템을 평가하는 순간, 다른 아이템을 추천할 수 있어야 하는데, 매 평가시 유사도 정보를 업데이트 하는 것은 현실적으로 어렵다. 아이템 기반에서는 일정 기간마다 업데이트 해줘도 적절하게 대처가 가능하다.



### 단점

* Cold Start : 새로운 유저나 아이템에는 과거 행동 데이터가 없기 떄문에 사용이 힘들다. 기존 데이터를 기반으로 추천을 하는 것이니 문제가 생기는 것이 당연.

* Data Sparsity : 수 많은 유저와 아이템 사이에 경험하지 못한, 구매해보지 못한 경우가 데이터의 대부분을 차지함.

  > 온라인 쇼핑몰에서 내가 구매한 목록보다 구매하지 않은 목록이 압도적으로 많음

* Scalability : 유저와 아이템의 수가 많아질 수록 데이터의 크기가 기하급수적으로 커짐

* Popularity bias(인기 편향) : 인기 있는 콘텐츠만 추천 결과에 너무 자주 노출된다.





### 2.1 Memory-based Filtering

User-Item Matrix로부터 도출되는 유사도 기반으로 아이템을 추천.

모델을 구축하지 않고, 추천이 요구될 때마다 휴리스틱 기법을 통해 결과를 도출하는 lazy learning 기법이다.

목표는 user-item interaction을 matrix 형태로 표현하고, 비어 있는 부분을 채우는 것



![img](https://images.velog.io/images/jinseock95/post/276e0190-4b7a-4791-9dba-b0a1bd5201cc/image.png)



#### 2.1.1 User-based CF

유저 간의 선호도(아이템에 대한 점수)나 구매 이력을 비교하여 추천 유저와 유사도가 높은 유저들을 골라낸 뒤, 이들이 좋아했던 아이템을 추천해주는 방법.

user-item interaction 정보를 통해 비슷한 사용자를 찾고, 내가 보지 않았지만 비슷한 사용자가 좋아했던 아이템을 추천한다.



1. item-user interaction을 matrix 형태로 만든다.

2. user간의 similarity를 계산한다. (pearson correlation이 대표적)

3. 추천 user와 similarity가 높은 Top N명의 user를 추려낸 뒤 normalize 한다. 

   > 유저 마다 점수를 잘주는 사람, 짜게 주는 사람이 있다.

4. 추천 user가 본 책을 빼고 rating을 예측하여 rating이 가장 높은 책을 추천해준다.



유형 1 : 점수를 예측

top N명의 유사한 유저들을 선택한 뒤, 그 유저들이 해당 아이템에 매긴 점수 \* 추천 유저와의 유사도의 합을 분자로 놓고, 추천 유저와의 유사도 합을 분모로 넣어 계산한다.

유형 2 : 편차를 예측

top N명의 유사한 유저들을 선택한 뒤, 그 유저들의 해당 아이템에 대한 편차 \* 추천 유저와의 유사도의 합을 분자로 놓고, 추천 유저와의 유사도 합을 분모로 넣어 계산한다. 이 값을 추천 유저의 평균 점수에 더해준다.

> 점수를 짜게 주는 사람과 후하게 주는 사람이 있으니까



*선호도가 업는 경우 즉, 0과1인 경우 타니모토 계수나 log-likelihood ratio를 사용해서 집합의 교집합 느낌으로*



#### 고민할 점

1. 나와 유사도가 1인 이웃이 있다. 공통으로 평가한 항목이 1개라면 1이 나오게 된다.
2. 나와 취향이 비슷하지만 해당 아이템에 평가를 하지 않았다면 이 이웃을 사용할 수 없다.



#### 2.1.2 Item-based CF

아이템 간의 유저 목록을 비교하여 추천

![image-20210208000458194](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210208000458194.png)

사용자 기반 필터링과 다른 점은 내가 평가하지 않은 아이템 i와 다른 아이템간의 유사도를 활용한다.

유저 u가 아이템 i에 매길 평점을 예측한다고 했을 때,

분모 항에 시그마의 의미는 유저 u가 평가했던 아이템 j들이다. 그러므로 아이템 간의 유사도 총합.

분자에 식은 유저가 평가한 아이템 j의 평점과 아이템 i와 j간의 유사도를 곱해서 낸 값이다.

> 내가 사용했떤 아이템 j들과 새로운 아이템 i간의 유사도를 구해서 얼마나 비슷한 아이템인지 찾는다. 
>
> 그러면 유사한 아이템에 매긴 점수가 높았다면 예측 점수도 높게 나올 것이다.



**논문에 따르면 경험적으로 Item-based가 더 나은 성능을 보인다.**





사용자로부터 선호가 일치할 수록 아이템 간 유사도가 높아지며 유사도가 높은 아이템을 추천한다.

아이템에 대한 유사도를 계산하여 



특정 아이템이 기준이 되어, 사용자들에 의해 평가된 점수가 유사한 아이템을 이웃 아이템으로 선정한다

이웃 아이템을 평가한 점수를 바탕으로 추천 대상 고객이 특정 아이템에 대해 갖게 될 선호도를 예측하여 추천.





어떤 사람이 a영화에 2점, b영화에 4점 주고, 다른 사람이 a영화에 1점, b영화에 2점을 줬다면 두 영화 간의 유사도는 1이다. 그래서 조정된 코사인 유사도를 사용.

![img](https://blog.kakaocdn.net/dn/dbqAQ7/btqBdTFV3ns/2bd5o5WyyME9TH1xt1eeXK/img.png)





### 2.2 Model-based Filtering 

User-Item interaction을 머신러닝이나 딥러닝 같은 모델을 통해 학습하는 과정.

User-Item matrix를 통해 model을 학습하고 예측은 이 모델을 사용해서 한다.



기존 memory based filtering의 유사도 측정이나 선호도 예측의 과정에서 기계학습 모델을 적용하여 추천하는 방식





#### 2.2.1 latent factor based CF

잠재요인 협업 필터링은 matrix factorziation을 기반하여 사용한다.

다차원 행렬을 SVD와 같은 차원 감소 기법으로 분해하여 latent factor를 찾아내어 뽑아내는 방법.

User와 Item의 Interaction을 Matrix로 표현한 다음 Factorize하여 latent vector를 얻는다.



유저-아이템 행렬을 이용해 유저-잠재요인, 아이템-잠재요인 행렬로 분해할 수 있다.

![image-20210208124437335](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210208124437335.png)

이 잠재요인이 정확히 무엇을 의미하는지 알 수없다. 영화로 치면 장르, 배우 등등이 될 수 있다.



#### SVD 

차원축소기술의 일종으로 실수나 복소수로 이루어진 m\*n 행렬 M은 다음과 같이 세개의 행렬 곱으로 분해 가능하다

![image-20210208140336932](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210208140336932.png)

![image-20210208141239735](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210208141239735.png)

* U : 역행렬이 대칭 행렬인 m by m 크기의 행렬. user와 latent factor 간의 관계를 나타냄
* Σ : 비 대각 성분이 0인 m by n 크기의 행렬. latent factor의 중요도를 나타냄
* V : 역행렬이 대칭 행렬인 n by n 크기의 행렬. item과 latent factor 간의 관계를 나타냄
* U_k : U에서 k개의 대표 특이치에 대응하는 k개의 성분만 남긴 m by k 크기의 행렬
* Σ_k : 대표값으로 쓰일 k개의 특이치 성분만을 남긴 k by k 크기의 행렬
* V_k : V에서 k개의 대표 특이치에 대응하는 k개의 성분만 남긴 n by k 크기의 행렬



U,V 는 orthogonal matrix이고, Σ는 diagonal matrix이다.

> orthogonal : 역행렬이 대칭행렬.
>
> diagonal : 대각 성분에만 값있고 나머지는 0



여기서 U는 M\*M.T, V는 M.T\*M의 고유벡터를 각각 포함하고 있다.



SVD는 데이터에 결측치가 없어야 하지만 대부분의 현업 데이터는 Sparse하다.



고유값 고유벡터 공식이 정방행렬에서만 가능한데 이를 직사각형에서도 할 수 있게 하는게 SVD





#### 고유값과 고유벡터의 의미

벡터에 행렬 연산을 취해주면 다른 모양의 벡터가 나온다. 

> 다른 차원일 수도 있고, 다른 방향일 수도 있고

그러나 어떤 벡터들은 선형변환 시 크기만 바뀌고 방향이 바뀌지 않는 경우가 있따.

![image-20210208151940200](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210208151940200.png)



x와 Ax가 평행했을 때, 출력값이 크기만 커진다.

입력벡터 x를 A로 선형변환 시킨 결과 Ax가 상수배라는 의미

![image-20210208152259054](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210208152259054.png)

임의의 n by n 행렬 A에 대하여 0이 아닌 솔루션 벡터 x가 존재한다면 숫자 람다는 행렬 A의 고유값이다.

솔루션 벡터 x는 고유값 람다에 대응하는 고유벡터이다.



Ax - λx = 0이 만족하고, (A- λ)x = 0이다.

(A- λ) 의 determinant가 0이 되어야지 x가 nontrivial solution을 갖게 된다.

즉, ad-bc가 0이 되어야 한다. 식을 풀어주면  λ를 구할 수 있음. 이 값을 통해 벡터를 구할 수 있다.

> determinant는 정방행렬에서만 정의된다. (A- λ)의 det가 0이면 (A- λ)의 역행렬이 존재하지 않는다. 
>
> (A- λ)가 역행렬이 존재한다면 x는 항상 0이다. 그러나 고유벡터는 영벡터가 아니다. 그러기에 역행렬이 존재하지 않는 경우에만 고유값, 고유벡터가 존재할 수 있다.



![image-20210208191630689](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210208191630689.png)

이런 값이 나왔다면 v1 벡터로 A 선형변환을 하면 1배 즉, 변화 없고,

v2 벡터로 A 선형변환하면 기존 v2벡터에 3배가 늘어난다.



고유값과 고유벡터가 묻는 것은

* 벡터 x에 선형변환 A를 취했을 때 크기만 변하고 원래 벡터와 평행한 벡터 x`은 무엇인가.
* 그 크기는 얼마나 변했나. -> 람다.

![image-20210208152746195](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210208152746195.png)









SVD 예제

https://bskyvision.com/251



#### SGD와 ALS

SGD를 사용하면 유저 잠재 요인 p와 아이템 잠재 요인 q를 학습시킬 때, loss function을 각각에 편미분하면 된다.

그러나 objective function에서 p와 q를 모르기 때문에 convex optimization이 아니다.

이를 convex하게 바꿔주기 위해 ALS 방법을 통해 p와 q 둘중 하나를 고정시켜 convex로 만들어준다. 따라서 p와 q를 번갈아가면서 고정하고, 업데이트하는 방식으로 학습을 진행한다.



#### 장점

* 잠재요인을 끌어냈을 때의 장점은 "저장 공간 절약"

  > 2000명의 user와 1000개의 item이라면 user-item matrix는 2000*1000이다.
  >
  > 그러나 latent vector로 100차원 뽑아내면 2000\*100 + 1000\*100 









https://lsjsj92.tistory.com/564

https://www.notion.so/Basics-4487ed5d90f94ad490879401c7801293 뒷부분.



Naive bayes

Clustering

----------

차원축소

https://velog.io/@jinseock95/%EB%85%BC%EB%AC%B8%EC%B6%94%EC%B2%9C-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EA%B8%B0%EB%B2%95-%EC%97%B0%EA%B5%AC%EB%8F%99%ED%96%A5-%EB%B6%84%EC%84%9D2015-%EC%86%90%EC%A7%80%EC%9D%80-%EC%99%B8-4%EB%AA%85





MF 혹은 CF?

결국 item embedding vector와 user embedding vector를 얻을 수 있는데

item embedding vector를 고정하고 학습을 수행하면 유사한 취향을 가진 유저들의 user embedding vector는 비슷한 값을 갖게 학습될 것이고, vice versa



CF를 학습시킬 때 training set에 많이 등장하면 그 임베딩 벡터의 norm이 커지는 경향이 있다.

그렇기에 유명함을 capture하고 싶다면 dot product를 쓰는게 좋지

> dotproduct는 norm 값에 비례해서 커지니까.
>
> 만약 크기가 1로 scale 됐다면 코사인 유사도와 dot product는 같다



또한 초기값의 norm을 크게 준다면 rare하게 등장하는 아이템들의 임베딩 벡터 값은 크게 된다. 그래서 초기화가 중요하고 정규화도!!



implicit에서 MF



objective functon

![image-20210305022110464](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210305022110464.png)

1로 interaction이 일어난 데이터에 대해서만 loss를 구해준다면 이 모델은 matrix의 모든 원소를 1로 예측하는 모델이 될 것이다.

![image-20210305022153739](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210305022153739.png)

그렇다고 모든 i,j값에 대해 (예측값-실제값)^2을 사용한다면 real world의 데이터는 sparse한 데이터이기에 matrix의 모든 원소를 0으로 예측하는 모델이 생길 것이다



![image-20210305022255690](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210305022255690.png)

그래서 대안으로 다음과 같은 loss function 사용. w0은 hyper parameter



두 embedding을 학습시키기 위해서는 ALS를 사용해야한다. (non convex해서?)

ALS는 fixing U and BP V, fixing V and BP U인듯??

이케하면 converge된는게 보장된다.



SGD와 WALS의 장단점

SGD는 어떠한 loss function에도 쓸 수 있고 병렬화가 잘됨

하지만 느리다(빠르게 converge하지 않음) 또한 네거티브 샘플링이 필요하다?

> **Harder to handle the unobserved entries (need to use negative sampling or gravity).**

WALS는 loss squares에서만 사용할 수 있다. 하지만 병렬화 되고 SGD보다 converge가 빠르고 Easier to handle unbosersevd entries



기존에 없던 아이템이 들어온다면 전체 모델을 다 재학습할 필요 없이 유저 매트릭스를 동결시키고 해당 데이터로만 아이템 매트릭스 학습시키면 됨.



CF에도 나이나 사는곳 같은 특성정보를 넣을 수 있따??

![image-20210305023455890](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210305023455890.png)



### AutoEncoder



https://paperswithcode.com/paper/autorec-autoencoders-meet-collaborative

https://www.youtube.com/watch?v=h6vePourB7E&ab_channel=%EC%82%BC%EC%84%B1SDS

https://wiserloner.tistory.com/1212



## 3. Factorization Machine

다양한 Feature들 간의 Interaction을 Polynomial Regression으로 모델링합니다.



영화를 추천한다고 생각할 때 영화의 메타데이터, 유저의 메타데이터가 유용한 정보가 될 수 있다.

MF의 방법으로는 이러한 다양한 피처들을 담아내기 쉽지 않다.

FM은 Feature가 다양한 데이터셋에서 좋은 모델. CTR 예측 대회에서 좋은 성과를 냈다.



## 4. 연관 규칙 분석

두 아이템 집합이 빈번히 발생하는가를 알려주는 일련의 규칙들을 생성하는 알고리즘

컨텐츠 기반 추천에도 사용된다.



### Support

전체 경우의 수에서 두 아이템이 같이 나오는 비율.

![img](https://blog.kakaocdn.net/dn/bWLbXX/btqw8CVCn9h/UY4ObQTdMTsYasgbdy7np0/img.jpg)

N은 전체 경우의 수, N_x^y는 x와 y가 동시에 일어난 경우의 수이다.

이 값이 높으면 높을수록 관계가 더 의미있다고 할 수 있다.

> 차와 라떼를 주문한 고객이 머핀을 주문할 support 값을 구하고 싶다면
>
> 차, 라떼, 머핀을 동시에 구매한 경우의 수를 전체 경우의 수로 나눠주면 된다.



### Confidence

X가 나온 경우 중 X와 Y가 함께 나올 비율. 조건부 확률이라고 생각하면 쉬울 듯.

![img](https://blog.kakaocdn.net/dn/0ObsV/btqxbACe59A/89Wew3zPpTAbFEVCrmKknk/img.jpg)

N_x는 x가 나온 경우의 수, N_x^y는 x와 y가 동시에 나온 경우의 수

>  차와 라떼를 주문한 고객이 머핀을 주문할 confidence를 구하고 싶다면, 
>
> 차와 라떼, 머핀을 주문한 고객의 수를 차와 라떼를 주문한 고객의 수로 나눠주면 된다.



### Lift

X와 Y가 같이 나오는 비율을 X가 나올 비율과 Y가 나올 비율의 곱으로 나눈 값

이 lift를 가지고 생성된 규칙이 실제 효용가치가 있는지를 판단한다.

![img](https://blog.kakaocdn.net/dn/b3wY5u/btqxcMJcChs/ypoO0OsCxsFMibPbLHMqhk/img.jpg)

lift 값이 1보다 높을 때 positively correlation, 1일 때 independent, 1 미만일 때 negatively correlation이라고 한다.

그렇기에 lift값이 1보다 높은 값을 가질 때 관계가 의미있다.





### Brute Force

1. 모든 조건절에 들어가고 결과절에 들어가는 아이템 집합을 만든다.

   >  ‘달걀을 구매하는 사람들은 라면도 함께 산다’를 보겠습니다. 여기에서 ‘달걀 구매’가 조건절, ‘라면 구매’가 결과절이며 각각의 아이템 집합은 ‘달걀’, ‘라면’

2. 위에서 찾은 frequent item set에 대해 만들 수 있는 모든 association rule을 만들고 min_conf를 넘는 rule을 찾는다.,



### A priori algorithm

빈번하게 발생하는 아이템 집합 만을 고려하여 연관 규칙을 생성하는 방법.



아이템 집합 {A}의 지지도가 0.1이라고 가정해보자. 

그렇다면 아이템 집합 {A,B}의 지지도는 아무리 높아도 0.1을 넘지 못한다.

이때 {A,B}를 {A}, {B}의 초월 집합이라고 한다.

즉, 임의의 아이템 집합의 지지도가 일정 기준을 넘지 못한다면 해당 아이템 집합의 초월집합의 지지도는 반드시 그 기준을 넘지 못한다.





## 5. Multi-Armed Bandit (MAB)



서로 다른 승률을 가진 여러 슬롯 머신이 있고, 정해진 횟수만큼 슬롯머신을 시도해볼 수 있을 때, 어떤 순서로 슬롯머신을 시도해야 가장 돈을 많이 벌 수 있는지를 찾는 문제이다. 

슬롯머신의 승률을 모르기에 시도해보면서 승률을 알아내야 한다.



가장 간단한 전략은 **입실론-그리디 방법**

10%의 확률로 아무 슬롯머신을 시도해보며 정보가 부족한 슬롯머신의 승률을 유추하고 (Explore), 90%의 확률로는 지금까지 관측한 슬롯머신 중 승률이 가장 좋은 것만 시도해 이익을 최대화 하는 것(Exploit)이다.

explore과 exploit은 trade-off 관계이기에 이 둘을 잘 조정하는게 MAB의 핵심



![image-20210303204434819](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210303204434819.png)

Q(a) = 이때까지 승률



UCB(Upper-Confidence-Bound)

슬롯머신이 최적이 될만한 가능성을 수치로 계산하여 선택한다.



입실론-그리디에서는 exploit을 할 때 최적의 슬롯머신을 찾기 위해 랜덤으로 탐험한다.

더 합리적인 선택은 없을까?? => UCB(Upper-Confidence-Bound)



![image-20210303204423036](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210303204423036.png)

네모 박스가 **해당 슬롯머신이 최적의 슬롯머신이 될 수도 있는 가능성**을 의미

N(a)는 해당 슬롯머신을 선택했던 횟수이고, t는 모든 슬롯머신을 선택한 횟수의 합.

즉 적게 선택됐다면 아직 승률이 수렴하지 않았을 가능성이 높으니 가능성을 높게 주고, 많이 선택됐다면 그 승률이 맞을 가능성이 크니 가능성을 적게 주고!!



여기서 슬롯머신을 우리가 제공하는 콘텐츠, 슬롯머신의 보상을 클릭, 승률을 CTR? 반응률로 바꾸면 우리가 해결하고 싶은 문제와 동일해짐.

하지만 현실에서는 승률이 같지 않고 시간, 위치에 따라 달라지고, 슬롯머신 시도도 제한되어 진다.



멀티암밴딧은 많은 인터넷 기업이 사용하고, 대부분의 최적화 문제에 있어서 잘 맞는 알고리즘.

> MAB는 A/B 테스트의 진화버전이라고 함.?



### Thomson sampling





한정된 정보로 학습을 해가며 Regret을 줄이고 최적의 Arm을 찾는다.



추천은 MAB의 여러 Application 중에 하나.

Item을 Arm으로 보고 User의 반응을 Reward로 본다면 MAB의 목적과 부합한다.

한정된 정보를 갖고 Regret을 줄여가며 최적을 찾기 때문에 Cold start 문제를 손실을 최소화 하면서 극복하기 좋다.





토로스에서는 앙상블 기법은 사용자의 반응을 고려하지 않으므로 사용자 반응이 반영되기 전 까지 사용자 반응에 둔감하다. 그렇기에 추천 결과가 정적으로 느껴질 수 있고, 반응률이 좋은 콘텐츠를 추천 결과에 더 자주 노출하는 매커니즘을 적용하기 어렵다.

그래서 MAB를 적용한다.

> explore, exploit으로 사용자 반응을 통해 CTR을 계속 바꿔주기에



사례

https://www.slideshare.net/ssuser2fe594/ss-164511610

https://netflixtechblog.com/artwork-personalization-c589f074ad76?gi=f8b539f9c5d6

https://static1.squarespace.com/static/5ae0d0b48ab7227d232c2bea/t/5ba849e3c83025fa56814f45/1537755637453/BartRecSys.pdf



https://brunch.co.kr/@chris-song/62











### 6. Deep learning

Task와 Data 구조에 맞게 적절한 DL모델을 변형, 적용

DNN, CNN, RNN, Transformer, GAN, DRN, GNN, Knwoledge Embedding 등 많은 딥러닝 구조가 시도된다.

https://arxiv.org/pdf/1707.07435.pdf



1. 다른 분야에서도 마찬가지지만 Production을 고려한다면 학습 속도, 추론 속도를 고려해야 함.

추천에서 다른 점이 있다면 주기적으로 재학습을 해야하는 상황이 많다는 점.

새로운 상품이 들어오거나, 소비 트렌드가 자주 바뀌기에..

*추가되는 데이터에 대해 Online Learning을 하든 Batch 학습을 다시 하든 해야 함.*



2. 데이터의 특징이 이미지나 자연어 처리의 성질과 다르기 때문에 layer 숫자, epochs, sequence length 등 기존 분야에서 쓰이는 값과 다를 수 있다.



3. loss와 evaluation matrix를 잘 살펴봐야 한다.

CrossEntropy나 MSE가 사용되는 경우도 많지만 *BRP* 같이 랭킹이 고려된 loss를 사용하는 경우도 있다. 

Metric의 경우도 Accuracy를 사용하는 경우보다 NDCG, map@k, recall@k, MRR 과 같이 순서가 고려된 Metric이 사용되는 경우도 많다









explicit feedback : 아이템에 대한 유저의 선호도. 보통 데이터의 크기가 작다.

> 영화 평점, 맛집 별점

implicit feedback : 서비스에서 유저가 한 행동. explicit feedback에 비해 데이터 품질은 낮으나 양이 많다.

최신 추천 시스템은 implicit feedback 데이터를 통해 추천하는 방향으로 발전 

> 뉴스를 클릭한 기록









## 7. 평가 방법



점수 예측 알고리즘

* MSE : 오차가 큰 값에 대해 가중치를 높게 부여하는 평가
* RMSE : MSE보다는 오차가 큰 값에 대해 가중치를 상대적으로 적게 평가
* MAE : 모든 오차에 동일한 가중치를 부여하는 평가







추천의 목표

추천 시스템의 요소인 아이템과 사용자들의 특징은 시간이 지남에 따라 변화하기에 시간적 역동성을 추천 시스템에 반영해야함.

추천 시스템 성능이 좋더라도 매번 비슷한 아이템을 추천한다면 만족도나 신뢰도가 떨어질 것이다. 그렇기에 일정 수준 정확도를 유지하면서 다양성을 추구해야 한다.













--------------------

출처

* https://velog.io/@vvakki_/%EC%B6%94%EC%B2%9C-%EC%8B%9C%EC%8A%A4%ED%85%9CRecommendation-System-%EA%B0%9C%EC%9A%94

* https://www.notion.so/ecc73247c9f9486d9063fca918c5917e#a10dab4409ab417f91d6b1d0015c53a7
* 







나중에 읽어볼 논문 : https://arxiv.org/pdf/1907.06902.pdf?utm_source=share&utm_medium=ios_app







## CF with Implicit feedback



사용자가 해당 상품을 싫어한다는 것에 대한 정보가 부족하다.



* We propose treating the data as indication of positive and negative preference associated with vastly varying confidence levels.

* optimization이 scales linaerly with data size



user와 item간의 액션을 의미하는 r_ui 값을 통해 preference와 confidence level을 만든다.

preference는 해당 프로를 좋아하는지 안좋아하는지에 대한 binary 값이고,

confidence는 preference를 얼마나 신뢰할 수 있는지에 대한 정보를 담고 있다.

> 예를 들면 tv show를 20번 봤다면 1번 본 사람 보다 좋아할 확률? 이 더 높다고 할 수 있다.



### implicit data 특성

1. No neagtive feedback

   item을 계속사는 경향성을 살펴보면 좋아한다는 것은 알 수 있지만, (계속 구매) 싫어한다는 것을 판단하기는 어렵다.

   특정 티비쇼를 안봤다는게 싫어하는건지 단순히 있는지 모르는건지

   > explicit data에서는 평가된 데이터 값만 보면 된다. 그리고 아직 안본거 몰라서 못본 것(missing data이라 판단할 수 있다.

   그래서 누락 데이터와 부정 데이터를 처리하는게 중요하다

   

2. Implicit feedback is inherently noisy.

   액션이 있다는게 무조건 positive를 의미하지 않는다.

   > 선물용으로 샀을 수도 있고, 사고나서 실망했을 수도 있다.



3. explicit feedback에서 숫자는 preference를 의미하지만 implicit feedback에서 숫자는 confidence를 의미

   > implicit feedback에서 숫자는 action이 몇번 일어났는지에 대한 값.

   큰 숫자가 단순히 좋아한다는 의미를 내포한다고할 수 없다. 하지만 중요하다. confidence를 얘기해주기에.

   > 한번만 수행된 액션은 어떠한 랜덤적으로 일어날 수 있다. (의도치않게)
   >
   > 그러나 반복적으로 액션이 발생한다면 사용자의 의견이 들어있다고 판단할 수 있다.



4. explicit feedback과는 다른 measure가 필요하다

   explicit feedback에서는 mean squared error가 성공적으로 작동했다.  그러나 implcit 에서는

   아이템 간의 경쟁, 반복적인 피드백의 의미, availability of item 들을 고려해야 한다.

   > 티비 시청 데이터라면 여러번 시청된 데이터는 어떻게 평가할지, 동시에 방영되는 두 프로그램은 같이 볼 수 없기에 하나만 선택해야할텐데 액션의 횟수 데이터로 어떻게 이를 판단할지.



이 논문에서 숫자의 의미는 얼마나 이 티비쇼를 끝까지 봤는지

> r_ui = 0.7 이라면 u가 티비쇼 i를 70% 봤다.
>
> 만약 두번 시청했다면 r_ui = 2 (100%로 2번 본걸 의미하는거지.)



implicit data는 frequency들이 수치화 된 것인데

다른 유저들은 다른 스케일가지고 있어서 유사도를 측정하기가 힘들다??

> 몇번을 시청해야 좋아하는건지에 대한게 다 다르니까??



neighbor 기반 보다는 latent factor model의 성능이 더 좋다.



r_ui가 0보다 크면 p_ui는 1, 0이면 p_ui는 0이다.

즉 p는 아이템에 대한 선호도를 의미하는 binary

하지만 이 선호도는 confidence level이 중요하다.,

p_ui가 0이면 신뢰도는 낮은데, 이는 어떤 항목에 대해 긍정적인 행동을 취하지 않았다는 의미인데

정말 싫어하는것을 넘어 못 접해봤거나 이미 봤거나 너무 비싸거나하는 다양한 변수들이 존재하기에 신뢰도가 낮음

![image-20210306154137272](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210306154137272.png)



또한 action이 있다는 것도 좋아한다는 것이 아닐 수 있다.

> 이전 티비쇼를 좋아해서 다 보고 틀어놔서 뒤의 티비쇼도 action이 일어날 수 있따. 또는 자신은 싫어하지만 선물용으로 구매

하지만 그래도 action이 많이 일어난다는 것은 선호할 가능성이 크다는것을 의미한다.

그래서 confidence level을 의미하는 c_ui를 설계함. p_ui에 대한 신뢰도 정도로 보면 될듯?

![image-20210306154229481](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210306154229481.png)

알파는 하이퍼파라미터인가??

논문에서는 40을 썼을 때 좋은 성능이 난다고 함.



유저벡터와 아이템벡터를 하나의 공간에 매핑시킨다고함. 둘이 직접적으로 유사도 구할 수도 있는

이는 explicit data의 MF와 유사하지만 , (1) confidence level을 고려해야하고, optimization할 때 rating된 데이터에 대해서만 수행하는게 아니라 모든 데이터에 대해 수행해야함.

![image-20210306155022925](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210306155022925.png)

그래서 다음과 같은 loss function을 사용한다.



그런데 모든 데이터 (아이템 크기 x 유저 크기)에 대해서 수행하기에 데이터가 너무 커서 explicit data에서 쓰이는 stochastic gradient 같은 방식을 사용하지 못함.



user factor나 item factor가 하나씩 고정된다면 cost function이 2차함수가 되어 global minimum으로 갈 수 있다.(ALS)



1. recomputing all user factors

   Y = nxf matrix, 모든 item factors들을 담고 있는 매트릭스

   C^u = nxn diagonal matrix, C^u_ii = c_ui를 의미한다. 즉 confidence를 담고 있다.

   p(u) = R^n 공간 상에 있음. 즉 n개의 원소 갖는 벡터. u에 대한 모든 아이템에 대한 p_ui를 담고 있다고 생각하면 됨

   ![image-20210306160954690](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210306160954690.png)

   By differentiation we find an analytic expression for x_u that minimizes the cost function

   > 위의 cost function을 미분한 것 같은데 유도가 잘 안되네..

   이 식의 시간복잡도를 다음과 같은 방법으로 줄일 수 있다.

   ![image-20210306162321059](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210306162321059.png)

   이 방법으로 10번 정도 sweep하면 된다고 함.



저자가 말하는 더 생각해봐야할 점은.

1. p_ui를 r_ui에서 다른 방식으로 뽑아낼 수 있을 것이다. (threshold)
2. c_ui를 r_ui에서 뽑아내는 방식도 다양할 것이다



이 방식은

1. r_ui를 통해 두가지 c_ui, p_ui를 만들어내고, 이는 데이터의 특성을 더 잘 반영하게 된다.

2. n\*m 크기의 데이터 연산이 linear running time에 수행된다.



0이 싫다라는 보장도 없고, 유저의 반응을 추적할 수 없기에 precision 기반 metrics는 부적절하다

왜냐하면 they require knowing which programs are undesired to a user

그렇지만 프로그램을 본다는 것은 좋아한다는 의미를 내포하고 있고, 그래서 recall 기반 metrics가 적절하다

> recall이 실제 true 중 맞춘 비율인데, 우리는 좋아한다는 것은 알고 있으니 이걸로해서 좋아하는걸 얼마나 많이 맞췄느냐로



이 모델은 다른 latent factor model들과 다르게 explainable 하다



0으로 줄때 confidence level을 모두 동일하게 0으로 줬는데,

상황이 많다. 그런 프로가 있는지 모르거나 싫어하거나 동시간대에 좋아하는 프로가 있꺼나. 이럴때 confidence level을 다 따로 줘야해.





## MF



전통적인 SVD는 matrix가 sparse한 경우에 대해서는 정의되지 않는다.

Moreover, carelessly addressing only the relatively few known entries is highly prone to overfitting

> *imputation* is the process of replacing missing data with substituted values

Earlier systems relied on imputation to fill in missing ratings and make the rating matrix dense.2 However, imputation can be very expensive as it significantly increases the amount of data. In addition, inaccurate imputation might distort the data considerably

그래서 최근엔 observed data만 모델링하도록 한다. regularization과 함께

![image-20210307013611481](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210307013611481.png)

목적식을 다음과 같이 쓰는데, k는 r_ui를 아는 경우 즉, 0이 아닌 경우만 해당한다.





### ALS

q_i와 p_u가 모두 unknown이기에 위의 목적식은 convex 하지 않다.

그러나 둘 중 하나를 고정시킨다면 목적식이 2차함수가 되고 풀수 있어진다.

> 왜일까.. 하나만 변수로 생각하고 해야 되는건가?



p_u가 고정되면 q_i에 대해 최소제곱법으로(least squares) 문제를 풀고, vice versa



일반적인 SGD가 더 빠르긴 하지만 아래와 같은 상황에서 더 유용하다.

1. 병렬화에 좋다. 각각의 q_i가 계산될 때 다른 item factor들에 대해 독립적이다. p_u도 마찬가지.
2. implicit data에서 쓰기 좋다. 이 데이터에서는 matrix가 dense하기 때문에 힘들다?



### Bias

much of the observed variation in rating values is due to effects associated with either users or items, known as biases or intercepts, independent of any interactions.

그래서 단순히 r_ui 를 p_u\*q_i로 나타내기엔 무리가 있다.

variation(bias)이 생기기 떄문에.

몇명의 유저는 점수를 잘 주는 경향이 있고, 몇몇 아이템은 더 점수를 잘받는 경향이 있다.

> 페미영화?



![image-20210307023618237](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210307023618237.png)

그래서 다음과 같이 식을 수정

mu는 global mean이고 각 아이템과 유저의 bias, user와 item의 interaction까지 4개의 term이다

![image-20210307023737883](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210307023737883.png)

전체 목적식은 다음과 같아진다.



bias를 넣어주는 부분은 잘 이해가 가지 않긴함..?



### user factor를 보강

유저의 explicit data가 없을 떄 implicit data를 활용할 수 있다.

item을 시청?한 경우 implicit preference가 남는데, action이 있는 item의 factor들을 이용하여 user의 factor를 구할 수 있는 것! (= x_i)

또는 인류학적 데이터? 성별, 나이, 사는곳 등등을 통해 유저 정보를 이용할 수도 있다.(= y_i)

![image-20210307024916396](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210307024916396.png)

> 아이템 factor도 이와같은 방법으로 강화시킬 수 있다.



### Temporal Dynamics

이때까지 모델은 static했다.

하지만 사람의 성향은 계속 바뀌고, 아이템의 유행도 변화한다.



위에서 rating을 여러개의 term으로 쪼갠 것이 각각의 term들이 시간적인 요소를 다룰 수 있게 해준다.

>  특히 item bias, user bias, user preferences들이!



#### 1. 시간에 따라 변화하는 아이템의 인기

영화는 처음 나왔을 때나 특정 이벤트에 따라 인기가 올라가고 내려가고 한다. 주연 배우가 새로운 영화 찍을 때, 이전 영화들도 같이 주목받기도 함

그래서 모델은 item bias를 시간에 따라 다르게 줘야한다.



#### 2. 사람의 average rating이 시간에 따라 바뀜

옛날에는 4점으로 많이 주다가 요즘은 대게 3점 정도로 짜게 주기도 한다.

user의 rating scale이 변화함

그래서 user bias도 time이 들어가야 한다.



#### 3. 유저의 선호도 계속 바뀜

자명

그래서 p_u 인 유저의 factor 정보는 시간에 따라 바뀔 수있다.

하지만 q_i인 아이템의 factor는 static하지.



![image-20210307030022347](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210307030022347.png)

그래서 다음과 같이 표기 가능



### 또한 confidence level을 추가할 수 있다.

implicit data인 횟수를 confidence level로 사용한다

이를 통해 cost function을 강화할 수 있음.

![image-20210307031000448](C:\Users\JH\AppData\Roaming\Typora\typora-user-images\image-20210307031000448.png)

한번만 발생한 이벤트는 정말 좋아서 한게 아니라 우연히 발생한 것일 수 있다.

그래서 적은 가중치를 주고, 반복적으로 행해지는 것은 높은 가중치!!





MF에서는 가장 주요한 factor를 축으로해서 데이터를 흩뿌림으로써 matrix decomposition에서 주요하게 사용되는 특성이 무엇인지 유추할 수 있다. (explainable)

