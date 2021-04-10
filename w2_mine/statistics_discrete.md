## **1. 확률변수, 확률함수**

확률변수 : 표본공간에 있는 모든 원소를 실수로 대응하는 함수 (확률변수는 변수가 아니라 함수다. 이름 잘못지어짐)

표본공간 : 설힘으로부터 나온 모든 결과를 담고 있는 집합

​	

확률변수가 무엇이냐? 

-> 함수다. 표본공간에 있는 모든 원소들을 실수로 대응시키는 

![img](https://lh5.googleusercontent.com/bxoUGPQFmZZ3Mx4elvzWFY0_A484UwUuztFbYKuM5Pt_OwWZdKhqbu72eGD9s8kVKUAKxIDp1uE6ovc4apAS5VoId-LIjHdG16saDTHAdUoe4D11MV0SS2pPlaAOSfxzrR4-k3w)

여기서 확률 변수가 앞면의 개수.표본공간의 원소 [ (HHH), (HHT) … ]가 확률변수 Y(앞면 개수)를 만나면 실수[3,2…]로 바뀐다.





![img](https://lh6.googleusercontent.com/2kiOGOxW43aYl0he6gF02_IIr-g-R38PVU6bEOJffSw_yMAQmlj612HD2HAqaipUqZNsB7cQZox3L9ZTY0sTYGjs9q7ZGUNa3UmlsJVJ7DS6y9MYccE4xOZCabHKucy3jYQA5Eg)


샘플 스페이스에 5개 있고, 주행거리가 확률변수데이터라는 것들이 다 이런 형태로 담겨져있는 것이다.실세계?에 있는 데이터(샘플들)를 확률변수를 통해 실수로 바꿔줘야 통계적인 처리, 분석이 가능하기에





![img](https://lh3.googleusercontent.com/EoQEC-pE3TPkKCVwGZQyu2C5s-WJkYmZopucFVL7AHjivZeD9riIcK_2dN07b2oBwbjwjHuZad8SegcWMKSSbU5SinlrNswrA4wGEAaCMTQN6IovbzuZvpYRDZLLKRt7XRPPL9A)확률변수 X1을 만나야 x11, xi1, 변수라고 부르는 것들이 사실은 확률변수

확률변수는 함수인데 표본공간의 모든 요소들을 실수로 대응시킨다.

확률변수에는 이산형과 연속형이 있다.

실수에는 이산형과 연속형이 있다. 

> 유한한 셀 수 있는 숫자 : 이산형.  ex) 동전을 던졌을 때 앞면의 개수, 코로나 확진자 수
>
> 실수가 연속형인 것 : 연속형. ex) 시간, 돈



확률변수에서 나오는 실수가 어떤 확률로 나오는지 알고 싶었다. 

그래서 나온 실수에 확률함수를 취해줘서 확률로 바꿔준다. 





![img](https://lh5.googleusercontent.com/1Q2SfnLhu4QOgtyRsrCMdKIG0JTL8Z3eeX4IiUHB-mLlycc6_KhC32reLenvZZjB_ZehJONQUUnvX5gjYBBpgYKzcKbY_3bCxwJN492czXwiLd0TbuILLO-7itkujZ1SeUn_Slc)



확률변수에서 나오는 값이 이산형과 실수형이니 이 실수를 확률로 바꾸는 함수에 각기 다른 이름을 붙힘.

확률함수에서 나온값은 0~1 사이이고 그 합이 1이되어야 한다.

**요소(실세계의 데이터?) → [확률변수] → 실수 → [확률함수] → 확률**



![img](https://lh3.googleusercontent.com/UMVHpHqAH2anl-yOHHuyTBPJzDHN-mU7_lpjOJfLaSEC_oVyEvtmOqA22FCf2IEWH0LvXiAvwhQNDUzQ7UZ-HBTpfZ8TdrMf5lJJ_FyqCD0Pm71TaMDlkNLnk-KeoPDde8txvLY)

P(x) = P[X = a] = 확률변수 X가 특정한 값 a을 가질 확률 x축은 확률변수에서 나온 실수, y축은 확률





## **2. 기대값**

![img](https://lh6.googleusercontent.com/VskOxKq7R0GVnnWFdBt7zqNQEpr2DqcVe97F7Y8wLy48NzWu3k8Sthk17ld_ilGlM0SXgXjFrd6pgA9Zp_Pppp6Vr6564WiLw6ETBbUTDpGcxYXr2ZDcYxcvFfnQdKz_SUSzGp0)

xi는 확률변수에서 나온 실수, 

fx(xi)는 실수가 나올 확률  

xi * f(xi)의 합은 기대값 

> 1,2,3,4,5 의 평균은 3이다.  

(1+2+3+4+5)/5 이긴 하지만 이 수식은 사실 1/5 + 2/5 + 3/5 + 4/5+ 5/5로 산술평균이란 기댓값에 특별한 경우이다.

모든 값이 동일하게 나온다는 가정이 있는 것이다.

기대값을 확률변수로부터 나올 수 있는 여러 값들에 가중평균이다라고 생각하면된다.

>  ex) 0.99로 이기고 이기면 100달러 주고, 0.01로 지는데 지면 100000달러를 낸다.
>
> 이 게임의 기대값은 100x0.99 – 0.01x100000 = -901이 된다.
>
> 기댓값을 구하려면 확률변수가 필요하다. 들어가는 실수와 확률변수에서 나오는 확률값을 곱한뒤 더하면 기댓값?





위 처럼 확률변수의 함수 꼴로 표현됐을 때도 기대값의 정의를 똑같이 적용시킬 수 있다.

![img](https://lh6.googleusercontent.com/-vfieWZ6zOZlhzNnmrR07otitEDbwzJ4J2GzHKi7AF5TKUHAhvtsKoxTdt8Y4mySNtqlCssUgWELg1IsBwo6MAcr_5xVgnTrcb2SYAp7IVFovynMUCToJWb4OoatgzSBKUmAoWU)



## 분산



![img](https://lh4.googleusercontent.com/865U4qQaBlbM2mpbQz8p1ku7doeA33vrh0qHUkx2NQOPu6mhiNVTbQwVX80CSmG4e0lZOF3wRWIA8p9Xedu8J41HlJwOFMhLxH_vmYdYmXXJyPVd5aQ5YJ4n829CwTsr6rprUNk)

확률변수 X에 기대값을 뺀후 제곱에 기대값을 취한다.

**기대값(평균)을 기점으로 얼마나 떨어져있는지를 제곱의 스케일로 표현한 측도**



![img](https://lh3.googleusercontent.com/qfHnB92ZVErhuOQwP9xN_kLQY3BuZa_v6uqNK7BKzDGcDdr6nEUUgyUtp-A20CB2HeiVul2rd5pWT08urXAJDeV8xdwUdbHQYTSuVUdgFQUpPRnJZLhHyWrFeS-n174NeY9-2sI)





## **3. 이산확률분포**



이산형 확률분포에는 베르누이분포, 이항분포, 포아송 등이 있다. 

확률함수의 인풋이 이산형일 때 확률질량함수.

확률분포 : 확률함수로부터 나온 확률들의 패턴

확률 함수가 다양하기에 패턴들 또한 다양하게 나옴 (확률 함수에서 나오는 값을 모두 더하면 1)

이산형 확률 분포 : 이산형 확률 질량 함수에서 나온 확률들의 패턴 (분포)



### 베르누이 분포

결과가 성공, 실패 두가지 중 하나로만 나오는 것을 베르누이 시도라고 한다.

확률 변수 X가 2개의 값만 갖는 확률변수이다. 

표본 집합의 값이 확률변수 X를 지나면 0 or 1의 실수가 된다. 

그러나 이 숫자(확률변수를 거쳐 나온 실수값)는 아직 확률이 아니다. 

확률 함수를 거쳐야 확률이 된다.



![img](https://lh5.googleusercontent.com/4NqCaOw3_vCyReRB9HtK4quUkdXP9fF1j_THOqVia8BpWL7zblY_mex3dFPxcmC-nOWbRqjGPYR8K_jngZk83k6Ii-_Kk0-9UIVoVvo9zG7eDWL4C9ePJHIJDkqUdU0Z_sBRYyQ)

그때 쓰이는 확률 함수 (정확히는 확률 질량 함수). 이를 베르니우 확률 함수라 부르는 듯 ?



![img](https://lh4.googleusercontent.com/SYEJXpzj7bvcJrdhBy99vmb2vKCjXT3Jw2OMTKjDlpV_8rLVPRbayMfygUFcPXnDc2Rov6IssZ-IID9hfbgjR3WqUxQb0O4RvbclhcrkPDxQ-fIzFvlcldcvopYC_ewisppNypo)

베르누이 분포는 베르누이 확률 함수로부터 생성되는 확률들의 패턴위 분포가 베르누이 분포이다.

**기댓값이 확률변수에서 나온 값 \* 그 값을 확률함수에 넣었을 때 나온 값 의 총 합**



### **이항분포**

베르누이분포를 한번 던지면 베르누이 시행.

베르누이 시행을 독립적으로 n번 시도해본다고 해보자.

여기서 **랜덤변수 X는 n번 던졌을 때 성공의 개수** 

여기서 확률변수는 0~n번까지 가질 수 있다. ( 표본집합 샘플이 확률변수를 거치면 0~n이 된다 )



![img](https://lh5.googleusercontent.com/c2IfC5JCeamOKA6xbbMCXMvDuF9dhOiIpFzkDPg-5DLtxAnstaHX8P_uLPVbNsR6gbEnheDBSLBdyu4Uyvf2mYY5AFZeoTJXXu_aqqSkhqF53KObI8xipPSLyVp_4NCbH9rEvZg)

이게 확률함수가 된다.  ( 그럼 p(x)가 확률 인거쥐 )

확률 함수에서 나오는 확률은 x번 성공할 확률이 나오는 거지(n중에 성공이 x번 나올 수 있는 경우의수 * 성공확률의 n승 * 실패확률의 n-x승)

그렇다면 이항분포는 확률함수에서 나온 확률들의 패턴인데, 확률함수가 이항확률함수. (binomial p.m.f)

확률 분포(이항분포)의 모양을 결정하는 중요한 값들이 parameter ‘n’과 ‘p’이다 ( 베르누이 분포는 파라미터는 p 한 개다. 베르누이 분포는 이항분포의 특수한 경우, n=1인 경우!!!)



![img](https://lh6.googleusercontent.com/1PcD4rwENc9Tm6ZY7DoczowLA4apJTv2joBGIMyTUJCNz3Mj_uTuJUaZ3cSOvWZ12RKWzBovYqmajoXBKTE_l3EmM_etDzS6slVxcLNf0w2GNYxBpEj3wvRsmwvpNDZHwa7U-10)

E[x] = npV[x] = np(1-p)

> ex) 불량의 개수 세기 , 0이면 양품, 1이면 불량품, n=10, p = P[def ective] = 0.1 일 때, 10개 중 불량품 개수가 2개일 확률을 구하시오.
> 확률변수 : 불량품의 개수 : (확률 변수가 가질 수 있는 값은 0~10)
>
> 확률함수 : 이항확률함수 P[X=2] = combination(10,2) * (0.1)^2 * (0.9)^8 = 0.1937E[x] = 10*0.1 = 1



**Q : 베르누이 분포란 무엇인가? **

p확률을 갖는 베르누이 시행을 했을 때 나오는 확률들의 분포입니다.

분포를 결정 짓는 것은 확률변수와 확률 함수입니다. 

여기서 확률 변수는 어떤 실험값이 들어왔을 때 실수값 0혹은 1로 바꿔줍니다. 

이 실수값을 확률함수에 넣으면 각 실수값이 나올 확률이 계산되고, 이 확률들의 패턴, 분포를 담고 있는 도표를 보고 베르누이 분포라 한다. 

이항분포의 특수한 경우로 파라미터 n이 1인 경우이다.



**Q : 이항 분포란 무엇인가 ?** 

p확률을 갖는 베르누이 시행을 독립시행 했을 때 성공의 개수에 대한 확률들의 분포.

여기서 확률 변수는 n번 던졌을 때 성공한 개수가 된다. 

즉 실수값 0,1,...n까지 된다. 

이 실수값을 이항 확률 질량 함수에 넣게되면 확률값으로 바뀌게 되고, 이 확률들의 분포, 패턴이 이항 분포이다.





### 이산형 확률분포 – 포아송분포



![img](https://lh6.googleusercontent.com/HI1tykijgAj8j-_atxsRbRECRVvKDQJAM6tva_WFDseC5cg3XjtW8DbdgOZ0ZT7XAMMv33mxj1O2-pY8ke-88zfbOYCyvcQ7w7Kof4kDiOpRS3gd65dqHTP5MzyHWEam6xJI0WA)

표본공간에서 나온 실험값들을 확률변수에 넣어 실수 형태로 바꾼다. 

이 실수를 확률 함수에 넣어 확률값을 뽑아낼 수 있고(실수가 나올 확률값), 이 확률들의 분포를 통해 확률분포. 

> (확률분포 : 확률함수로부터 생성되는 확률들의 패턴, 분포)



포아송 분포 (포아송 확률함수로부터 생성된 확률들의 패턴, 분포)

확률변수 0,1,2 .. 처럼 이산형 값이 있다.(확률변수에서 나온값을 보통 확률변수라고도 부르는듯)

![img](https://lh4.googleusercontent.com/j_0AZtKVTmgwam4A4H7rzM9GiF1-CfCB1ThWnrnNStQx0nPmHY8gzjcWvV_v0FzgM5eWQk_rTDqV_I9gl5HAVemLXd2do6wV6eUu1rXaJT5Nw7FvcIfyhSmrTpmb__sXsr0JnfQ)


이게 포아송 확률 함수 (시그마 i=0~무한대이고 저 함수를 넣으면 합은 1)

단위 시간(공간) 안에 특정 사건이 몇번 발생할 것인지를 표현하는 확률분포. 

> 람다가 어떤 단위시간에 평균 발생하는지 횟수

포아송 확률 함수의 파라미터는 람다 한개이다. 



**(파라미터는 확률 분포의 모양을 결정하는 값, 모든 분포에는 파라미터가 무조건 한개 이상은 있다.)**



![img](https://lh4.googleusercontent.com/GiCIzXAv5nVKHlnYQSoMC03u3k8QzDfez7Mu_QvQYv-5Q9Oq8RcGx6ZtwpMgzz0wvwHdkFUdLBU_QROR-5naMbIhQkIhAIYs8WtmFXwfLwuXcncxg0oalMMDZSFanUQdrJiOmeY)

이항분포 : 1회 시행 시 발생 확률이 p인 어떤 사건을 n번 시행할 때 k번 발생할 확률의 분포

이항분포에서 n이 굉장히 크고, p가 굉장히 작을 때 이 이항분포는 포아송분포로 근사할 수 있다.

![img](https://lh6.googleusercontent.com/RJ6zqUZ4h0AY-cb3I8wXyhM-Ap5RbUjU1Sqr67TonPoYnigsg1aMSMvUAl0neKkL_AcIXKeJ5ds_DHG62TkEi0iGAVqeATVNyCcfw-BgruYLG3BGbwsNdcE-wBmtGh6PfsMpmCg)



n이 굉장히 커지고, p가 굉장히 작아지고 np가 어느정도 값을 가질 때

이 이항분포는 포아송분포로 근사하게 되고, 포아송분포의 파라미터인 람다는 np가 된다.(np는 이항분포의 기대값인데..)



포아송분포가 쓰이는 상황은 단위 시간 내에 특정 사건이 몇번 발생하는 지 알고 싶을 때(자주 발생 보단 드물게 발생하는 사건에 잘 맞아 들어간다)

> 1. 어떤 집단에서 100세 이상까지 사는 사람의 수
>
> 2. 출판된 책에서 오타의 개수
> 3. 전화를 걸 때 전화를 잘못 걸을 횟수



![img](https://lh6.googleusercontent.com/nJjA1R741jfb_VgagtFyhKT_txW1_a4f4QV7rKpmXNu3B1LHGi3w3msva-JPC4ObQ8PpDbLWnL5trWBepIXUnH744Zm9_Nt7hFAKsV29dU2PYSOdb20DvyRUyrCTQguT_UWCCXA)

기대값 E(X) : 람다

분산 V(X) : 람다.

기대값과 분산이 같은 값을 갖는다.



![img](https://lh6.googleusercontent.com/kHq_sD4QIhLAEZbPPtbR6oIwx5tJANvCU_Yn7MuttH4Bfl76jXI2xHKg9nmxqcAMlH6Y-J848sbVRGglPyTRJVpuqnfr92s1z2ATzPe7ImjRgEfDhzXOjg3rleKAVO82vgLSfko)

확률변수 : imperfection한 glass sheet의 수. (X=0, X=1 …. X=n)

문제에서 glass sheet가 모두 perfect할 확률을 구하라 했으니 P(X=0) 즉, X가 0일 확률을 구해야한다. 

이를 위해 확률함수를 이용하는 것이다.

왜? 확률함수가 실수에 대해 확률을 생성하는 함수이니까



![img](https://lh6.googleusercontent.com/f7w6CIzS9_AQI3aRCvPDyrWM3egKEI4MFgCkdd3vi7sDGA7ysYKLv1lODtkxEqd_X3uzXU20cmm8nGNfpdg6RybcE1taXmdR4Tx0-o-wppsZ-zlEK0Sq_wSRScIdaYX7z791dQA)

1미리세컨당 파티클 4개.2.5미리세컨드에 있는 파티클의 개수가 15이 확률을 구하는게 문제.

확률변수 X : 2.5미리세컨드에 있는 파티클의 개수

P[X=15]를 구하고 싶은 것

1미리세컨마다 파티클 4개이니 2.5미리세컨마다 파티클 10개. 

그러니 람다는 10이 된다.(단위시간이 1미리세컨이 아니라 2.5미리세컨이다)



### *** 기하분포**
베르누이 시행을 할 때 첫 번째 성공까지 필요한 시행 횟수

5번 시행해서 첫 번째 성공 = (실패, 실패, 실패, 실패, 성공)

모수(파라미터)가 p 밖에 없다. (p = 성공 확률)



![img](https://lh5.googleusercontent.com/DIsPNP8xc6MqKf1wVvWsWS1u3pwRSqBHoHqPvUq8Qpq6j5NarfsKxep1ceAqoJZZoyTYnjpYR8-WXxHpppdKXeSVXxOZsWS2u0vlVyX5EaYszMcmJTC6gBwe65Wpbyklkooypqg)

항아리에 2 색깔의 공이 있다. 

복원 추출할 때, 검은색 공이 뽑힐 때까지 공을 뽑는다. 

확률변수 X : 검은색 공이 첫 번째 뽑힐 때까지 필요한 시행 횟수



![img](https://lh6.googleusercontent.com/qnKUsPujHbzdWSztSHuodNk5U6Cnb3RDBh0uvDKgAFFeaXcrXfAkHjoHPKFWn9EUxG_FO0i28hn7_gbGhUBBoJFUY2TW7kEdnNlXkQrL5MovFfA8jRXdGBda_oi8eg-8yCigmPQ)

검은공이 뽑힐 때까지 필요한 횟수가 k개 이상일 확률은 k-1번째까지 흰색공이 뽑힐 확률과 동일하다.



### **음이항분포** 

기하분포의 특성과 비슷하다. 

기하분포의 일반적인 형태라고 보면됨. 

확률 함수가 이항분포와 비슷하다.

베르누이 시행 k번째 성공을 하기 위해 몇 번 시행을 해야 하는지. 

즉, 확률변수 : k번째 성공을 하기 위해 필요한 시행의 횟수

r번째 성공을 보기 위해서 n번의 시행이 필요할 확률이 얼마인지 물어본다.

n-1번째까지 성공이 r-1번, 실패가 n-1-r+1번이 나오고, 여기에 무조건 성공이 한번 붙을 확률.ex) 5번째 시행에서 3번째 성공을 볼 확률. == 5번째에서 3번째 성공이 일어나야함 == 5번째 이전에는 2번의 성공이 이 일어나야 함


![img](https://lh4.googleusercontent.com/gw7Fzizh8sigCG3L3bbLVJEYtzP87IWpyajT01ZS5Yq5xrXiDBzxhm3I-a8Anvoh9QH4ytuouaNZBQwteQLC5RfDY2UCkqQhK1Oz7fxxf1CbJ6kJQZwr5OPV_xy-JXrFCWRpZOQ)




음이항 분포파라미터가 r과 p이다. r은 성공횟수, p는 성공할 확률( r=1인 경우가 기하분포가 된다 )

![img](https://lh6.googleusercontent.com/Om7gFyZ1dZVjckvELsb4Bf8Tkuo0lNbeZMyBXxgyRL8y7dh5rATavKbdBSEKK56ABFrE8VyzxhbQELkSfoKtV0lw20V9CA_25Y6l5hH5CmU_RoBd6O_0Ogdqf2DePmcBh6wXEvU)



![img](https://lh4.googleusercontent.com/memwagK_ZMoSynZqXbcdVtR3gn2q-T1HDAZhUE3O8lzVKuVODjfMYDujncCJn7li0pSB9hEJoCY63TB9rO77E4sH2_i6iuMqkfQF3bf51rrc-k5I8r4IUfvkB3VTsUtPllSY2DU)
모든 확률 변수의 기댓값과 분산은 해당 확률 함수의 **파라미터의 함수꼴**로 표현이 된다. (즉 파라미터 값으로 결정된다)


![img](https://lh3.googleusercontent.com/XL8rmLXw7BTygeVFVbMPaq3vfEo3fEnTq-ZCnyLskDP6dcOoejKgd0wr4wZ-cGwaU3OFMZ0CMG-pu5iRD3Ex479yZqCd8iZAWC2Bv14DX2zHiMvQWsqGjSVAZmmMqg4Jr9wky38)
확률 변수 : 6이 3번 나올때까지 던진 주사위 횟수 (X=3, 4, 5....)




![img](https://lh4.googleusercontent.com/xVIfveLOM_nklQfWMZ-Qj0yKpNRCJpf-cZJ8ctE-dQbMm2qX3njiSKmaoL3HvczOoNoTcnkXGD4FzHJLeSKmAJ_mdmZEZbjEt9eduWTgWXHt5tG4Pu_jTUYuviE_NKtKB-ET9HM)
(2) 6명까지 볼 예산이 있을 때 예산이 충분할 확률. 즉 3번,4번,5번,6번 안에 끝날 확률을 구하는 것이지



### **초기하분포**

품질에서 많이 쓰인다. (제조업체에서 품질을 검사할 때) 

> 뽑은 샘플 중에서 불량이 몇 개일 확률이 몇일까 와 같은 상황에서.

N개의 공 중에서 m개가 흰공, 나머지가 빨간공이다.

이중에서 n개를 비복원 추출한다면 n개 중에서 흰색공이 몇 개인지 확률을 구하고 싶을 때 사용

확률변수 : 샘플링한 n개 중에 흰색공의 개수 (X=0,1,2 ... n)

확률함수 : 
![img](https://lh6.googleusercontent.com/JJGCKeUSgDjXQUoJdIenR3RyC_qFMea8oyOP9Md830LaMx9qi4zqIosGFfWIs6OXYI9yQWWXN8SZoadY_bpIX5YxYZ6J5FoqTqJbfc6rt6Kjczdb1yE3O1_v3cHuNYou1Ot2dQo)

의미를 보면 N개중 n개 뽑았고, 흰공 m개 중 i개 뽑고, 빨간공 N-m개 중 n-i개 뽑고

파라미터 : 3개

총 공의 개수 : N

샘플링한 개수 : n 

관심있는 공의 개수 : m


![img](https://lh3.googleusercontent.com/RJZLU8PgUnDiD00dZWd9m8TjATLWrmIuLSRDbxSvUHxgVL4aq6xyWCimot4XjTmnipTW9676Bp-Xp7iWwxtcs6qmOiu6FcoFvnEYeyxVkekAf1D8_6hKyhWfn1odYUd9tySmRww)
기댓값과 분산
![img](https://lh3.googleusercontent.com/FRROxQUlnGj8iM-D7JU-9EHlw5IXZ4WflyPsPK9cxDaHC-1k3vA5Y80fI0YJ6xHDufcywh0qVVaytmlU5GRwDPBef2NurFbkFcK5nf8dt4jBN9KA6dBkZrngNgXzKB1MxcMl56A)
Var에 오류가 있었다. 파라미터가 아닌 p가 나올 수가 없지.



![img](https://lh3.googleusercontent.com/52yI-wUdxcuPXFkPim4qBcq5GW2db_BWd5q5pVaWzHhQbhj7WVg5BCJ55gBc7HM0wbH16IvtgsL11gOi3CeTnANGHQJfKvXk4Dg6nRdhFK7xmHCJsqifrhr_vxVIkMnXxpvJt6U)
확률변수 : 4개의 샘플 중에서 불량품의 개수

4개중 2개가 불량품일 확률

30개 중 4개를 뽑았을 때 양품 2개, 불량품 2개인 경우는 불량품 5개중 2개 뽑기 * 양품 25개중 2개 뽑기



![img](https://lh6.googleusercontent.com/H5fjROEdEfhAdPofKWlgnUJsC4ec2a7FCul9SmO5XKyKxlQhrjBtoyTlKdps8hZr9qQv_Wu-Ee3eCmbhUl7cNHJXqdZSGFwtOIBwPJ8wc7FUVuVxjxpwMrtLstJZiA-bO8SY45k)

문제 : 소비자가 10개 중 3개를 뽑았을 때 3개 전체 다 양품일 때 물건을 산다면, 물건을 살 확률은 몇인가?

확률 변수 : 샘플링한 3개중 불량품의 개수

A = 샘플링한 3개중 불량품이 없는 경우