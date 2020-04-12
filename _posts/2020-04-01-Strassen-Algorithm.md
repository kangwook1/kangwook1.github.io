---
layout: single
date: 2020-04-12 09:30 +0900
title: Strassen Algorithm 
author: kangwook
---

## 슈트라센 알고리즘이란

기존 행렬곱에서는 복잡도가![img](https://ssl.pstatic.net/images.se2/smedit/2015/3/24/i7n4jh1maw9srq.jpg)입니다. 여기서 n항이 늘어 날수록 계산량이 어마어마해지죠. 이를 보완하기 위해 나온 행렬곱셈법이 슈트라센 알고리즘입니다.

## 슈트라센 알고리즘 분석

그럼 어떻게 보완했는지 알아봅시다. 먼저 A와 B를  정사각 행렬(**크기는 2n × 2n**)이라고 가정을 합니다. 그리고 두 행렬의 곱 C는 다음과 같습니다.![{\displaystyle \mathbf {C} =\mathbf {A} \mathbf {B} \qquad \mathbf {A} ,\mathbf {B} ,\mathbf {C} \in F^{2^{n}\times 2^{n}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/f4c680ec4a32379114e0326ba69b179881b69e8e)

만약 A와 B가 정사각형 꼴의크기가 아니면 0으로 채워줍니다.

![{\displaystyle \mathbf {A} ={\begin{bmatrix}\mathbf {A} _{1,1}&\mathbf {A} _{1,2}\\\mathbf {A} _{2,1}&\mathbf {A} _{2,2}\end{bmatrix}}{\mbox{ , }}\mathbf {B} ={\begin{bmatrix}\mathbf {B} _{1,1}&\mathbf {B} _{1,2}\\\mathbf {B} _{2,1}&\mathbf {B} _{2,2}\end{bmatrix}}{\mbox{ , }}\mathbf {C} ={\begin{bmatrix}\mathbf {C} _{1,1}&\mathbf {C} _{1,2}\\\mathbf {C} _{2,1}&\mathbf {C} _{2,2}\end{bmatrix}}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/41c6337190684aff7b69f124226d6e62d79ebca5)

 C는 다음과 같습니다.

![{\displaystyle \mathbf {C} _{1,1}=\mathbf {A} _{1,1}\mathbf {B} _{1,1}+\mathbf {A} _{1,2}\mathbf {B} _{2,1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8d91fa79d27697a5c6551698c1a83a3d5837c57b)

![{\displaystyle \mathbf {C} _{1,2}=\mathbf {A} _{1,1}\mathbf {B} _{1,2}+\mathbf {A} _{1,2}\mathbf {B} _{2,2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/a08bea24eec9422cda82e6e04af1d96fc6822038)

![{\displaystyle \mathbf {C} _{2,1}=\mathbf {A} _{2,1}\mathbf {B} _{1,1}+\mathbf {A} _{2,2}\mathbf {B} _{2,1}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/7adffe97db091ce8ba231352b3721bbe261985ca)

![{\displaystyle \mathbf {C} _{2,2}=\mathbf {A} _{2,1}\mathbf {B} _{1,2}+\mathbf {A} _{2,2}\mathbf {B} _{2,2}}](https://wikimedia.org/api/rest_v1/media/math/render/svg/8b40ed74cf54465d8e54d09b8492e50689928313)

여기까지는 기존의 행렬곱과 다른게 없습니다. 다음부터가 중요합니다.

![img](https://postfiles.pstatic.net/20150324_33/forever1363_1427160639733gW4mx_PNG/%C4%B8%C3%B32.PNG?type=w3)

갑자기 뜬금없는 M값이 나오는데요.

위의 M1부터 M7을 가지고 덧셈만으로 C행렬을 구할 수 있습니다.

![img](https://postfiles.pstatic.net/20150324_72/forever1363_1427160639903NdPdB_PNG/%C4%B8%C3%B33.PNG?type=w3)

위의 과정은 곱셈이 사용되지 않기떄문에 기존에는 8번의 곱셈과 4번의 덧셈이 있었지만  슈트라센 알고리즘에서는 7번의 곱셈과 18번의 덧셈으로 처리를 할 수 있습니다. 이 과정을 반복 할 경우 ![O(%5Ccombi%20%5E%7B%202.807...%20%7D%7B%20n%20%7D)%20](https://ssl.pstatic.net/images.se2/smedit/2015/10/7/ifgnj7vpdn8pdg.jpg)가 나온다고합니다.

### 여담

슈트라센 알고리즘은 기본적으로 분할정복을 기반으로 한다고 합니다.

따라서 행렬을 나눠서 계산한다는 것인데요.  M을 이용해 덧셈만으로 C를 구성하는 과정은 아직도 이해가 잘 안되긴합니다. 

출처는 [위키피디아]([https://ko.m.wikipedia.org/wiki/%EC%8A%88%ED%8A%B8%EB%9D%BC%EC%84%BC_%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98](https://ko.m.wikipedia.org/wiki/슈트라센_알고리즘))입니다.



