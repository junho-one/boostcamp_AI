# 연속형 확률 변수, 연속형 확률 분포

이산형 확률 변수와의 차이점은 확률 변수에서 나온 값이 연속형이다.

그리고 이산형에선 합이지만 연속형에서는 적분을 사용한다.

> ex) 돈, 몸무게, 키 ...



## 확률밀도함수 

0~1 사이에 확률이 아웃풋으로 나오는데 인풋이 연속형 실수이다.



![img](https://lh6.googleusercontent.com/I4gugjC5BZT8Yt8vqBcThrQy9hnhTvlC2Xl3cTWvkJe_LYYFo2kc9MOlQ9BY0TlXa3xUI6RoGudOgC65dmuRicehEzmaohIWhjVbrKM8I9P4kTi56UO5a6qbkWisu0olNdgzHYw)

확률밀도함수에서 딱 a일 확률은 0이다. 

a에서 a 적분이니까 수식에 의해.. 그래서 앱실론이란 굉장히 작은 숫자를 a에 빼주고 더해줘서 약간의 공간을 만들어 적분한다.



![img](https://lh5.googleusercontent.com/MFUTmAEDFThA-jcCp1GiqyWEWcmUpep63qL76FgTGZgFJA7WmyE3Ot83ghzNqEyQWMfVOmcXenm1vkwJeOa8mj1i11b60ihooYid7XJkdmx28VFga5bq_TR5Bp8mdVpv8kn2tT8)

P(x=a) = P(x=b) = 0이기에 확률 밀도 함수를 통해 확률을 계산할 때, 부호가 있든 없든 상관이 없다.



![img](https://lh5.googleusercontent.com/nj700cExMHRd18YQNKKqcYZO8gYfIh2b1XYA0oyD8eBd6L7_9mhq4bwgo3_6R49U4V2R3K1lUKIbe3yk8xG4d6jSqHFy7kgO1syBUb4UnuuK7rqao7IiJpOVuaPCf20uP8m8KKo)

pdf가 되기 위해서는 모든 가능한 값의 적분값은 1이 되야 하기에 그 성질을 이용한다.



![img](https://lh4.googleusercontent.com/oEe_P7JPxKGeMmEKs5SbrX2F1dd2N6xKkDGUhZkWAFt8VmyYVFJAepbXxyCBZWBXXgEgL1PlOOi4xvLXFj7d46MBEcDikSyg2quof8drZgi_F9mwoGrmZ04CwULevzdqAxGvriA)





![img](https://lh3.googleusercontent.com/OCw8OpzXH7C18crxbgNgf5jMiIWD8P3yWl3qSbToxjr1DBVpNCFUqmy9iJNA00F40ZrhAlEUQasTuulxx8cj0Jswt9pPb08zDeMK_7qQSd-HKlWEP6JaKBVZHPPuT_F_G2yTacw)

cdf는 특정한 값보다 작을 확률을 표현한다. 즉, -무한대 ~ 특정값까지 적분한 값cdf를 미분하면 pdf값이 된다.



![img](https://lh4.googleusercontent.com/U9pFnGyJ8e4cJ1anvCpp9hn7CfH5PxeXR0MpLvTzwedkCOr3HEPom8ukAsRkDd-xK7p3GewhV_WXJaV8JS6FNGT6IiEGye0GPSPxFDBjvrRvhys7iqWEhCoOcW4xwG31x6tSgB8)



cdf 함수를 알고있다면 a~b 확률을 쉽게 구할 수 있다.



![img](https://lh3.googleusercontent.com/vE3jlqcWZrWqzoH8HcHp1vVlkwrMub9MtDN92etGBB2pGLQk3lGU5u1-ETk3ocWxg6wf7S2o4SZFxrA1dmjRxPx85gUljZWVMnPCxQQG-puoQ3L2KoJcAabPdqwQ3uM9e086RDE)

cdf 식을 알면 그냥 쓰면 되고, pdf 식을 알면 그냥 적분하면 되고



![img](https://lh3.googleusercontent.com/C0FLMZbdbL2S21JARBZmT1TRB-jy6fbPDZlKXcPTNUte0uWVvivHkvLbvBUBFrOwY4p1pnwcLmIlT1HIOlgIjkWXtTQri-vaTbY3s3DUC2lJBDUQFT5RCDrkuTwFEvgFfhB-Nso)



![img](https://lh3.googleusercontent.com/LvlAErv9rfPyC2hjS2e929FxlSfd80K-6ha-rImyx-xbdKe65Xg6UsEoW0_JsqUZ_NctUZud05f-UNit_nO9ZFE8PCh7WUmfVhGlXlMrqYpmYv3tFGHJOLl0urduNOIJvGL0KXw)

![img](https://lh5.googleusercontent.com/L_UkWJ_7HlC_CEGbvkjNq3eebqanPa99OmtVs9bMrSF4ygFW5JI0uoEpJ7Om9vDjE-fU8cEGRTMVLaQ9bet97jre3_dZTOqVEqQmGUxUtblFJE23WzNDZSxKffOb-TrdUQ8RMIQ)





![img](https://lh3.googleusercontent.com/YTWxbSzeM3lJ9xrTlEBoKNgWPSvMmzi5Nkc3WYnLX9gdvf0tXkxUQT9POYGztbOn8MPygLAcfGltGHSvAKwNNLmugdZumSahkjO7nOd3ntNsZ2Bw0HyTOEVzDPyBRGAs_xyOdws)



![img](https://lh5.googleusercontent.com/MK3mSE1pSVUTSqk2ri7isvxrOtybZIjvygJWWr9r3d4x9uX8daLyiCmZlxsVOkLdxNarlAoUlUBYMqCIH4oPulkISYDFyGbimFjfwTplSRNjYin7Tgl1J3GusXfcRrJ0wPmMD3M)





### 일양분포 (uniform distribution)
특정 구간 a ~ B 내에서는 특정 확률이 계속 발생한다.



![img](https://lh4.googleusercontent.com/HAppswBzPviybi4etLk_YIefw5ivkxx5OY39twAdSYxIGauMmgt45eyFoSpH_r7eg802B1gcmwD11ukJWdynUSL3FiN4Bno01IUuzaVwT1KVWfthWsrtDUdAG-I814H35vwpY0w)




![img](https://lh5.googleusercontent.com/mVx-neAVUGXMl2TU3X1gG4AeZUqakx1SDU9xGKwsfvoykINTge7P-F8lgwKatjmxSunZEzap0DgsFLQ8ikIG8FzHe30jGSP6Z_9_4NUCB3sR7KHc0CCKv092DC1Sy7qhmCkljb0)



a가 1,2,3 구간에 존재할 수 있다. 각각의 cdf를 구해야 한다.

cdf : -무한대에서 특정 지점까지의 pdf를 적분한 값으로 특정 지점까지의 확률의 누적 값에 해당한다.

이 세 구간의 cdf 식을 모두 써야 한다.

![img](https://lh6.googleusercontent.com/Ms0lk6pRRJN-Kt0tezxVpYrz-Tz0ZZx2KXLR5Cr8p1R7gaeyw-wEbErEoUUSMs_MdSeuLRtxhXeQulYyXxKveZ-4U9PDL6-e7liZpv8QqwGdIVLS1dbfQaxKwujszXldo-zHMkU)







기대값 : 확률 변수의 기대값이란 각 확률변수가 특정 값을 가질 확률들을 가중치로 확률변수의 결과값을 평균 낸 값

![img](https://lh5.googleusercontent.com/hUx4J3xwLxnXH9DdZ-IACZXtwrRTKdjuJsP45JMFG5CAAs3OgLPMtfQ8k8SgH1KPJ5sijvT7AzN52mLhoF-qGRChaMv8TFLYTfO8Nfr-imTxDpayUrsumvkxE9OD0kn4d4-5I1Y)





#### 예제 

![img](https://lh6.googleusercontent.com/flSMsW6YybGBNiVNmjdAutgMqkOJoNYu5D0GYn93i1SkHpm3mghlR19cwxpXMJph8mzIEsYGDhHi9QrUXZXCzbOCluFs9w18xg7EAVL08HzUp7-Z8SaochaTodUV4kz83PGOYD0)








### 정규분포


정규 확률 함수

![img](https://lh6.googleusercontent.com/sk7WzhX1wJL3acL7hg5S7Ux1z1hVUbo4MqkWBfFf1g3labLHdAV5ZNAYLVIN28EyKfvRG-IPlIvxbsk5AxAYW0gBjuo0tqnXqfK7KfH7jBuejyUxazQ0EwDmd8-_qhzPfcgIyUk)

어떤 실수가 들어가든 확률이 반환된다.

정규 확률 함수의 파라미터는 뮤와 시그마.



* 확률변수 X가 평균값을 가질 때 가장 큰 확률을 갖고, 평균으로부터 멀어질수록 확률값은 작아진다.

- 평균을 기준으로 좌우 대칭이다.중간을 뮤(평균)로 정하고, 얼마나 흩어졌는가는 시그마로 표현된다...



#### **표준 정규 분포**

정규 분포인데 평균이 0이고, 표준편차가 1인 경우를 표준 정규 분포라고 한다.

일반적인 정규분포는 항상 표준 정규분포로 바뀔 수 있다.

> 분포 간의 스케일을 맞춰서 비교하기 위해서 표준 정규분포로 바꾸기도 한다.

(정규) 확률 변수 X에다가 평균을 빼주고 표준편차로 나눠준다. => Z

![img](https://lh4.googleusercontent.com/t0pUDrW6Zuw52ot1opMY3nUYp-Jds5Zji8tnuDRO489sRCu9fzj8GwpevRkG55XtWbaLTZjWtBmLpuu8GLYe4Su6tYbdBf5fJzfjfC2MfYR-GEhFs-sLjOzaA5QsaabBfezxShY)

이 새로 생긴 확률 변수 Z의 확률 함수는 다음과 같다. (pdf of Z)

![img](https://lh4.googleusercontent.com/qCD8mJCWjJE7RdymFqclo_tMPtaSXaclBQGPpmDL75cbo285T3OJitL026bfIV1f7upYQgMO9Rwct1TBQuuUmW1aQh-VPxZejfd8hLR02iu43v4MITmCOyucmvNNPq7UW0knPR8)

별게 아니고 표준 확률 함수에 뮤와 시그마에 0과 1을 대입한 것임.

cdf의 결과값 자체가 특정 값보다 작을 확률임 

> cdf(z) = P[X <= z]



![img](https://lh6.googleusercontent.com/mKe_FlMttvsLU8OsO2qF1aUUZUrmiCi5I-jDitUCBY1JxhHGTG2y0oWORB7d66CS_zUOKPOfZZIvwAAk24s1v6gsmvwc8vR5HQuDP82AlncNpi3iW4xBbKOSUbb9NtIc6Cuqe-s)

cdf를 통해 분포의 면적을 구할 수 있다.

z-table : 표준 정규 분포의 cdf 값을 정리해놓은 표.

구간의 확률을 구할 때, pdf를 통해 매번 적분하기 귀찮으니 표로 만들어 놓은 것이다.

![img](https://lh5.googleusercontent.com/kJHCgqxoGZs9vs871ptV6OwDTH1P5twrBUjCzCEq8vnIVsGSJUnxa4pFb1NxGh4WM0E55_Vh_0K3P25C9mfisMGdlfWu1ulInGjizm9-ZZaPOFvOtY_Sb72eHP8k-SfSYkD-hrY)

z-table은 확률변수 X에 대한게 아닌 확률변수 Z에 대한 표이다.그러니 X를 뮤를 빼고, 시그마로 나눠 Z로 바꿔줘야 한다.



![img](https://lh4.googleusercontent.com/-zwPm5AtyUGHwC0pQXUOrxnkCNJQ3XG3befA1DKX2wo2TyLBMkmzoiwdtzhdnVXqXXdqbtVZLV42VriKxXMYeCNFo8CZD9naYj-wKOUXCI46c6C6btG9QVHd2zZUTJoWQ1JEaxI)

표준 정규 분포에서 X(Z?)가 평균을 기준으로 1시그마, 2시그마, 3시그마 떨어져있을 확률이 얼마인지를 이미 구해놈



![img](https://lh4.googleusercontent.com/T-xaPPki4Wxmgv3ujBVJeg3Zv8CXLoPdow8dd6amN4JgFuKN0sIhhlQrVX6w_GJRBJQkAuCp81ldtoNcPh1jbn0ygt-2mwUcoYfEriDULHIhTBtNCtabA7xaKKb11Cp961U4W1o)



### 이항분포와 정규분포의 관계

이항 분포의 파라미터는 n과 p였다.

정규분포는 대표적인 연속형 확률분포고, 이항분포는 대표적인 이산형 확률분포이다. 

이 둘은 근사가 된다. (근사가 된다 == 특정 확률을 구할 때 어떤 방법을 써도 비슷한 값이 나온다)

이항분포(이산형)에서는 cdf를 구할 때 개별적인 확률을 다 더해줘야 하므로 계산이 복잡한데, 이를 정규분포(연속형)으로 근사하여 구하면 더 편하다. 

즉, 근사하면 이항분포의 cdf를 구할 때 편리하다.

그러나 이 근사가 항상 잘되는 것이 아니라 특별한 상황에서 잘 돌아간다.

[ n이 충분히 커야하고, p가 0과 너무 가까워서도, 1과 너무 가까우면 안된다. ]



![img](https://lh4.googleusercontent.com/ZMp2aX1Z7dk1eqQDcnTEn_LWukUtHMrxlvAhijXd-chiIiYGULjAg6pLggvCM3YsUr0VF7viugANmje2scF7X8U399aLrpN1DYtnDbL-JZDeEmzUV309dZ8IWdhEvJE0FoxC_zc)

n이 충분히 크고, p가 0이나 1에 너무 가깝지 않다면 이 이항분포는 평균이 np이고, 분산이 np(1-p)인 정규분포와 비슷해진다.

![img](https://lh3.googleusercontent.com/xEWKSdMsXsyusrezFzLFoSEAddL7vhPoKoEHDq9-ItR9PTAbJcMumFg_2Eeei_R_sy-EYDND69R5cPtIgZ4CZCPPmhUGPHDwrV_rrhjst9Re5saPB4XhM1jsiFT7D6WxHCIIwuI)



#### 이항분포를 표준 정규분포로 근사화
![img](https://lh3.googleusercontent.com/UFnxdKikIBou4xSM84Gd9g_Z-4kjtih274QpIDRNH6sVjfzbrrINCibft5SUtPkfP0bxKnyaIBSKC4AmkD2kr_9ec1HWOZvVM5qWWVMEfjn8fZAtxyFuPRDWT-eSt_TuHO6baNE)

n이 크고, p가 0,1에 너무 가깝지 않으면 분포가 skewed 돼있을 수 있긴 하지만 정규분포 모양을 따른다.



![img](https://lh6.googleusercontent.com/ZetUnqldB_y2tA3hJBA5Cxuip4nFFZHJQHmwUhBQuTPpF2gBwridd37DmbtGwt2EErehb0a95vYn-W1ZK6zFl9pGOW2fOqHR785C4ASiRY8wlO4KZD-B7KtvfiXNU6AcI2g1Vos)





이산형과 연속형은 태생부터 다르기에 완전히 같을 수는 없을 것이다.

그래도 이산형을 연속형으로 바꿔줄 때 경험적으로! 0.5씩 더하고 빼주면 좋더라

> 이 0.5를 continuity correction.



![img](https://lh3.googleusercontent.com/ycwOHm69c4sWIyzI4g_POEHyLMMmqKF-7iFCbb2Yjw-X6cfQD7Xt84iTyt5yzULZY_JKtAWPdF8_fMbrTJd05j7gqJO-wZBIMpvWkIdE6tloEDN9sjSjn0TbnB37-PkZyE6bJqI)
이 근사되는게 중심극한정리에 의해서 되는 것??



![img](https://lh6.googleusercontent.com/N_fx2Tt6Bz3HC-nquKn54eUpkUnnZefZRb43sKCVboc520qpmXFKy0pZXdyju9pi6boHBenwumt3kK3jiNq_Z2UzE34M0zgLMnsnFMbXrhP4CgRDSehkq-01a0GEqKUa9JEKmMM)
이렇게 근사된다는 정당성이 증명이 돼있다.

값을 확인해보면 근사해서 구한 값과 이항분포를 통해 다 더한 값이랑 별 차이가 없다. 

0.7286 ~ 0.73xx범위의 확률이 아닌 특정한 값의 확률도 구할 때 쓸 수 있다.

















Chater 6-4 지수분포
연속형 확률분포에서 일상생활을 정규분포 다음으로 모사할 수 있다.
보통 x가 시간?
\* Pdf 식
![img](https://lh6.googleusercontent.com/kDbt6vPpmORdQh9wRfRW65Dywi659Y_Son0sDD3ivKdJ7YCbSt210-vK7VwN3ZGFUF6KD0lpVm2RQoGhbgTCS0-kcEAy6kMDxrTtq9_sK_yvFeZkxfMEfe2eFkD-sqJh4cDDDIQ)



\* cdf 식
![img](https://lh4.googleusercontent.com/D2vrOMb_Iz24BveqyuYbMyJi1SEIAcmffWk2mV_7uY7FVsfxWKBUAUEk95DoZ4ZoF7HeDWJmZ636yAG6jkikSaC6xis3saliABIfEWazVAz9WQSRnyGWdWEvrxnr8IawfTFFieE)


지수분포에서는 cdf를 이용할 확률이 매우 높기 때문에 이 식까지..지수분포는 시간을 모델링하는데, 이벤트 간 시간을 모델링한다.어떤 이벤트 A가 나왔고, 두번째 이벤트 B가 나왔으면 이 A,B 사이에 걸린 시간이 얼마인지를 모델링한다.* 근데 이 이벤트들은 포아송 분포에 의해 생성돼야한다.
ex) 전자 기기 부품의 고장 간격 시간. (하나 고장이 났을 때, 다음 고장이 발생할 때까지 걸릴 시간)

람다 : 단위 시간 (단위 면적) 당 이벤트 발생 평균 횟수.
![img](https://lh5.googleusercontent.com/MGNw1jbkeNNqpjxqe0LXHcqPhllw0TnQkqKcqKPgda3V_8ycvfATCn5U-SIzj2ns-3qd6qXtW4ARhaN26Fk3FvARBG9uHyKRYQj7kZgQEHsjr7S_5UYjK-iHQizhlEk77TJ6LU0)기댓값과 분산
![img](https://lh5.googleusercontent.com/GvJfF4sohRDvbqDg7zGGBSgG92l3enzykaeKbireZvwH55aQOaYFqH76SQrl7chIt8HQK9EOH3zCkwt9kz9egp3Fr3F_75hiuyNStuqJusX14LTdSZR8fIghSRgLDwgbnA4As_g)





어떤 사람이 전화를 쓰기 위해 기다리는 시간을 x라고 두면, ![img](https://lh4.googleusercontent.com/77wxxWhgZnTahtf9iz8hWxDVqFiRo5WhYlcDWW3fT8t-kvBaDuhrmeY3qYzWdVfDeEMcVCV_EIvBKHRPVDAum43Ctjrs_CkCAPQYktwo1jtyiip67frqDkG47JJTA_qu3j2qx-g)이 x가 지수분포를 따른다.(한사람이 도착하고 또 다른사람이 도착할 때, 이 사이 시간이 x?????????????)
람다가 1/10이니까, f(x) = 1/10 * e ^ (-1/10 * x)

![img](https://lh4.googleusercontent.com/a75B-ZHC6ADqIrjGEeeEC9PSHrhSGXFgTfSDLP1iggDqSIijwNBGWc-isNekatqoq6CLMKASDSlFZp274POpWx59MshMoxuUnjSgK0HOzPihkh5YhX6mQaN2oY-HJ60AbH9rafw)X: 난파선의 위치를 알아내는 데까지 걸리는 시간람다 = 1/5 ( 난파선 위치를 알아내는데 평균 5일이 걸린다고 했으니까 )* 지수 분포의 Memoryless Proerty( 기억상실 특성 )
![img](https://lh4.googleusercontent.com/wIQI5KGhwaR0caME2UxA1byTWZVmG6hioMpx0IRshrlA7tvxOevGq5E2PGFX7_TKuRzqPgiSmaZsgGK-j9eoDA36d3QpopTDxor-kScqFQqERZQuMXarVeVKLOzlj03xiElWAKo)[1] : X가 t시간 이상 진행이 됐는데, additional 하게 s시간 더 갈 확률 (조건부 확률?)[2] : 그냥 additional 하게 s시간 더 갈 확률
1과 2의 차이는 조건부 t가 있냐 없냐. (즉, t시간동안 왔다라는 과거의 사실이 있건 없건)즉, 과거의 무슨 짓을 했던 미래의 일에는 관계가 없다.
어떤 기기가 t시간 작동했다면, 부가적으로 s시간 더 작동할 확률은 !! 그냥 s시간 작동할 확률과 같다. 즉 과거에 몇시간을 작동했던 확률이 같다는 의미..

memoryless property는 확률변수 X가 지수확률 함수를 가져야 한다 (그럼 자동으로 지수분포)조건부식이 풀어지면서 P[x >=s]가 됨을 보이면 증명이 가능.![img](https://lh6.googleusercontent.com/LQze57knCc1-AFc4Oi3Kju5z-6Rc7h_0M5qAkOjRW4kwE7u3tXGJfpKSrIPYHCssDbalYIqdYWjAvhg5IH18m7rlmBRnbKXd7MUI4brxPsaFquTDMt1x8D1Ku_YvhGvUlPgDJaA)이 속성의 속 뜻은 앞에 t시간이 걸렸던 것은 중요하지 않고 미래는 똑같이 된다.
이러한 가정을 갖고 문제를 풀면 쉽게 풀리는 문제들이 많이 있다!!!!이러한(이전에 해온 시간이 추후에 하는 시간에 영향을 미치지 않을 때) 상황에 맞는 문제에만 지수분포를 적용해야 함
(이 예제는 그냥 가정을 하는 것이다.)![img](https://lh6.googleusercontent.com/uQyABZSNsg4kkOszAFkjpFwK9sB3oUjs3mIa2Bx9kgXPL4Il_8t4tDFMQw-SFHn40tDGMUTmUwJdUWNrBnWZbumppZwT0_sU7SyHRHXr57zXb79Mgr1RzlGnS6kOZEEhz5CjyLo)
자동차 배터리가 다 소진될 때까지 평균 1만 마일을 달려야 한다. (=평균 1만마일 달리면 배터리 갈아야 된다)어떤 사람이 5000마일 여행을 하고 싶은데, 배터리를 다 교체하지 않고 5000마일을 다 여행할 확률은 얼마??
이 사람이 배터리를 갖고 있을 때, 이 배터리가 t마일 달렸다고 하자. 배터리가 지수분포로 모사된다고 가정한다면!!!!이 배터리가 t만큼 달렸는데 총 t+5000마일 이상 달릴 확률은 과거와 상관없이 5000마일 더 달릴 확률과 같다

  \* 지수 분포와 포아송 분포의 관계
포아송 분포 : 특정 시간 안에 몇번의 사건이 발생하느냐.지수 분포 : 어떤 이벤트가 포아송분포로부터 발생할텐데 이 발생하는 걸리는 사이 간격(시간)이 얼마인가.
포아송 분포
![img](https://lh5.googleusercontent.com/lxWJMTEwe6pMmJLXnIIjgzTkMpl1P3ADpxWYjEUoVIMNw2x-bRj5Uzqv_V6cXk743piLzXy67sdJo-f9WJQJ59YabMbwYc4Yx3rgRE4MxWgnuT5E4t3lWXNsVp4ssQ0ElWRn9HY)지수 분포
![img](https://lh3.googleusercontent.com/ZjtT8WGrWY7qMaQg9Ewz8gg5MaaQY-j6dEfc49GzL6kvrMXVYi4OoT4JrK3ZQ3oktlXOWn0fJ9Acc2OV8Y_RJsk3xmwK61AnmsmZMijuZW-YdZsO_nc_OYeXFcfnuRqLIme6Omc)포아송 분포로부터 생성된 이벤트들의 사이 시간이 지수 분포이다.







![img](https://lh3.googleusercontent.com/eGwyiiNSdrEJcF7FNtpjk43MzanIHthZGg4Hso1kv122MokrIo8Fek6K26xHbhnJ-AbRrHISTJ6ULLMH4I_dYPblR2kTUCuBc3241ep4ZS5i3NIFfTNXL-Ut5RP0DX96mkvUXKs)
![img](https://lh3.googleusercontent.com/HjdyH8Jbh9j3527iLm7iG4aFAZFZ6KyvBrg8EQwov5EIJdTUVTqwia5N09b0xFbfuMgePX_dXKRiWgaqnu7IWwt_I7bqzZbjp65C3tMwxSoPaktMqGJWAu3ZHFsr-7kD-Qr3gfo)
평균 1분에 3번씩 걸려오는 상황. (람다=3)전화 걸려오는게 X인데, s와 t시간 사이에 걸려온 전화 횟수. (포아송분포, 특정 시간안에 이벤트 횟수. 여기서 단위 시간은 t-s인데 분당 3이니까 => 3(t-s) )
걸리는 시간 i-1번째 전화와 i번째 전화 사이에 걸리는 시간은 지수분포
Question 1 : 0~2분 사이에 전화가 한 건도 오지 않을 확률?- Ans : 이건 포아송 분포를 써야 하는데 t가 2, s가 0이 되서  X ~ Poisson(6)을 구하면 됨
Question 2 : 첫번째 전화가 2분 이후에 올 확률? (발생 간격 시간이 2이상)- Ans : W1 ~ Exp(3),  P(W1 > 2) = 1 – P(W1 <= 2)
위 두 Question은 같은 질문이다. 다른 분포 관점으로 보고 푸는 것

Chapter 6-5. 감마분포, 베타분포
 감마분포는 지수분포와 관련이 있다.감마분포는 지수분포의 일반화된 개념이다. (감마분포가 더 큰 개념)
확률변수 X : k개의 이벤트까지 걸리는 시간 ( 0보다 실수 )
\* 감마 확률 함수
![img](https://lh3.googleusercontent.com/vuYfJJkBQh_eoyJOeRCaf0fGsmzN5yWzBnBzdOoOFKBv39s14fYI5AScZzgB7cv5P_Ddb2jWKcEa0CqdGp_KunlU-XIvsGR-rCZzmgMKTvPsc3rHkbTkHT5GLVJaofGcI_sTN2c)





\* 감마 함수
![img](https://lh4.googleusercontent.com/IawP-OKge84t1Sak15Id4oKPKshPcKWJou7YdB8FwjMGCgD69tNQTVlXHQDl38yv9_n3HkETdKIZW_uDB2-kZCq7BP4aBgZCRwpo9Juq8wEtcXW4y9xLSDykpMJ4nSzJb281QIo)



\* 감마 함수의 성질
![img](https://lh4.googleusercontent.com/nIWu6nqcBJLIUjT0Db-XhDLOHZQjEAuzWGQ8ydQS54aFZaTFC_bIA9oQPJt89s97TRC4b92p3eFmKYydOUWifGaCDt2mzIHG6zFrtdttLlvO8SqQu3OolSNgssRyToUbMl6H8hU)파라미터 : 감마 함수에 들어가는 알파와, 람다가 있다. (이 람다는 지수함수의 람다와 같아)확률함수에는 최소 하나의 파라미터가 있고, 파라미터는 확률 분포의 모양을 결정하는 값.
![img](https://lh6.googleusercontent.com/xfAi5bwFhi-rSTWdoF0Dcp_YEP7F2exbSwWGZ6jNNMhGQlLCCvtqd_Sxn3fgCruQtGdeqMtLjg6hWIe2rDff33jYkVvW1mCY7d1TmIuTpogUCo3M-KAKWoiinzOHPNLrR97NWgA)











\* 기댓값과 분산
![img](https://lh5.googleusercontent.com/-kx3rv5B94MWIxKigsW4hNnvzxWIvr7C9yOSs8NY-AzIbWpp-8PsC-Xe0uqG9ccLIiaY3ECGmJaBcpGuex_6iiardRXyEMxqWIRW0SmHAGv2j1ETl4VZlCMcLF3UON8UuSHVH2I)







![img](https://lh3.googleusercontent.com/4E-9fCYSl4ndjr3Du6d-AKJS0pydhGfsOKvqkV4FhPg6IYsQZo60ATUjo3hBfREBXgrH6AbAQ9LSOszlhZ0V5YcVoVW2W9wxzxmMTiAN3V2fGwBqzJDKvyIKBClDwLKBLNwzt9A)
지수함수(람다) = 감마함수(1,람다)
확률변수 X1, X2 ... Xa 가 모두 파라미터가 람다인 지수분포를 따른다고 하자. (각각의 확률 변수들은 모두 독립)X1 + X2 … + Xa 즉, 모두 더한다면 이 값은 감마 분포를 따른다 (파라미터가 a이고, 람다인)즉, **감마분포는 지수분포의 합**이 된다. (a는 개별 지수분포의 개수)
즉, 서로 독립인 확률 변수들이 지수분포를 따를 때, 이들의 합은 감마분포를 따른다. 
람다(단위시간당 발생 평균 건수)를 파라미터로 가진 포아송 분포가 있을 때,a개의 이벤트가 발생할 떄까지 걸리는 시간을 감마 분포를 따른다 (파라미터를 람다와 a로 갖는)이 a가 1개인 즉, 1개의 이벤트까지 걸리는 시간이 지수분포인 것이다.

![img](https://lh4.googleusercontent.com/2KirmhtlSlaRvMOpjltLl3wXTspzOrmfypvuft4QhjNDJd44KEuK11pMbL4OujHwRpzteJ2a1jWxI6Jk4xU1o8FyIhzywm9gz5iZ3CHNVD1w9ClTXZDscpAnKWtXUwnWl-UcTGs)물고기를 보통 30분에 1마리 씩 잡는다.4마리의 물기를 잡을 때까지 걸리는 시간이 2~4시간일 확률.(여기서 1마리를 잡을 때까지 걸리는 시간이 2~4시간일 확률을 구할 때는 지수분포를 쓰지만 2마리 이상이면 감마 분포를 써야 한다)
sol : 30분당 1마리인데 여기서 단위시간은 1시간이니 람다는 2가 됨.
확률변수 X : 물고기 4마리 잡을 때까지 소요되는 시간이 확률변수 X가 감마분포(4,2)를 따른다.















![img](https://lh6.googleusercontent.com/NeHqDdUyzepIaVyuVIpaavzT0JO0AfZ7rFcbjZUd8IwMu48VYm_Stp-5888YLIyBhocvsvZdXztW37JrGYRP9pS1p8yyU2oolQ6EGjXU85ufiMypeEwpwE6TMcuSCorCO94yFvM)철반 배송이 포아송 이벤트라고 보면,확률변수 X : 20개의 철판을 이동할 때까지 걸리는 시간X는 알파가 20, 람다가 1.6인 감마분포를 따른다.(알파는 이동하는 철판 개수)
20개의 철판을 배달할 때 걸리는 시간이 15분 이내로 걸릴 확률은??

















\* 베타분포베타 분포는 비율에 관련이 있다. (비율을 구할 때 베타분포를 사용한다. 불순율, 작동률 등등..)
\* 확률함수 (확률밀도함수)
확률변수가 비율이기에 갖을 수 있는 값이 0~1![img](https://lh5.googleusercontent.com/uBnaJsLo8M4YUYxLMDz5jtzmnOg9m8ESnCkH6Mjv3qWyEErHwDYiVS3GUvDsoXm2c1hYKqKoTHhCFcjAsPbk1js0anngIQG8_7M5PIljqeaPQSSjxt2yP7WSQ5-J78fnJXI0uV8)
\* 베타함수 (베타함수는 감마함수로 정의된다)
![img](https://lh3.googleusercontent.com/6dAAzwOVG6sskuLJOovAYDENopWXYkoZdJxNpxexYb57YuDKvmpgcx6zZ5nAXPPsj0dNdCMj2cHinROVvT6jj4Gk7GNY9o6AWBOAbujwTQGOUYfQwgfGdDh5lyDigYQ-KKZTf1M)* 기댓값과 분산 (기댓값과 분산은 파라미터의 함수)
![img](https://lh3.googleusercontent.com/ns2ZQB5pib43g2x4COTPGiZTxiL61_O7FFa_0Jy1x0edbHTgEy3Tv1w8KaR-vseMfn2LCCKhKvcDYPq7dmJFUXPmmrqVxdVD4rmvy8pMDNpTM58tC9cVZ9TTMjWsfuOGyBg4aYE)
(추천을 해줬을 때 클릭률이 베타분포를 따른다고 가정하고..)

![img](https://lh4.googleusercontent.com/y-3JDnROvXEdGZpZzfA2kL9DYNR7SQcCs2xUKPuxSHtHHfUq9UXkWHxcFcjMrvvyKCpPbNjxVpWga50t2I5lkL-ZJmf9bwSMChU0XFD_qJx1nB56TFHPtNuqhnQIqRmIT7N_P8I)알파와 베타가 값이 같으면 대칭이 된다.
알파와 베타가 0보다 작으면 수명 분포에 응용이 많이 된다.(제품이 처음에는 고장이 많이 일어났다가 어느정도 시간이 지나면 안정됐다가 특정 시간이 지나면 고장이 많이 남. 초반에 고장이 많은 이유는 불량품이 만들어졌끼에, 정상적인 제품이면 잘 작동하다가 수명이 지나면 고장)

![img](https://lh4.googleusercontent.com/wybZ0SU0KhSJaSTmTWIVAcREU1TB6CEqvN4eVmvYaG2BcLJ9plgkSXfekpB7fVofC3LQfmAEiUH38OOeD1XnxUcPSp9tmgEs1yc5VxBPn1mS59FC7Yh74zJSO55p7Zyj4P24JtI)












배송시 생기는 DVD 불량률이 베타분포를 따른다고 가정한다.
확률변수X는 배송시 발생하는 DVD 불량률 불량률이 0.2 ~ 0.3일 확률을 구하라. 
문제에서는 어떤 분포를 따른다는 것을 알려주지만, 공부를해서 어떤 상황이 어떤 분포를 따른다는 것을 잘 알고 있어야 한다!!!!

![img](https://lh3.googleusercontent.com/Dl1VnmscZq26VjSx0UNjgmEM5bOpg4T0q67piWapitUIk_UcsA8yCuUNaCoah27OKJG6jj-boqz2R3F4nbKayIJd2Rd3Ktfy6Ne45VxqUZOTrIH8BCbSJvZHuPO87mKq0cpj0VI)
일벌들이 여왕벌을 따라가는 비율이 알파가 2이고, 베타가 4.8인 베타 분포로 모사를 한다.이때 절반 이상의 일벌이 따라갈 확률이 얼마인지.
확률변수X : 일벌들이 여왕벌을 따라가는 비율 

연속확률분포1. 균일분포2. 정규분포3. 지수분포4. 감마분포5. 베타분포또한 t분포, 카이제곱분포, f분포도 있따.