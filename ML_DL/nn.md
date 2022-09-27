다층 퍼셉트론

# 신경망

- 인공 신경망은 생물학적 신경망의 중추신경계인 인간의 뇌가 문제를 처리하는 방식을 모방한 모형

- adline(적응형 선형뉴런) : 퍼셉트론과 비슷하지만 활성함수로 선형함수를 사용한다.

  - 퍼셉트론은 계단함수를 사용

- **특성**

  - 신경망의 각 노드에 미분 가능한 비선형 활성함수를 적용
  - 신경망은 하나 이상의 은닉층을 포함한다.
  - 신경망은 높은 수준의 연결성을 나타냄. 이 때 연결강도는 신경망의 가중치에 의해 결정

- **신경망 훈련은 역방향 알고리즘을 가장 많이 사용한다.**

  1. 전방향 단계에서는 신경망의 가중치가 고정, 입력신호는 출력에 도달할 때 까지 층별로 전파

     - 함수 신호 : 신경망의 입력 노드로 들어와서, 신경망을 통해 노드별로 전방햐응로 전파되어 신경망의 출력노드에서 출력신호로 나오는 신호

  2. 역방향 단계에서는 신경망 출력을 목표출력과 비교해서 오차신호를 생성. 

     - 오차 신호 : 신경망의 출력노드에서 시작하여, 신경망을 통해 틍별로 역방향으로 전파되어 신경망의 모든 노드에 의한 오차신호 계산에서 오차함수가 포함되는 신호

     이 오차신호는 역방향으로 층별로 전파. 이 단계에서는 신경망의 가중치가 연속적으로 조정



- 인공 뉴런
  - d개의 입력에 대한 x1~xd 에 대한 출력이 o 일 때,


  	<img src="C:\Users\wlsgy\AppData\Roaming\Typora\typora-user-images\image-20220927151920067.png" alt="image-20220927151920067" style="zoom: 80%;" />

- - xi : 입력층의 i번째 노드의 입력

  - Wi : 관련 가중치

  - b: 편향

  - f : 활성함수

  

## 다층 퍼셉트론

  퍼셉트론의 한계(선형 분류기)를 지적하며 나오게 된 다층 구조

- 아이디어

  - 은닉층을 둔다. 은닉층은 원래의 특징 공간을 분류하는 데 훨씬 유리한 새로운 특징공간으로 변환한다.

    - 특징 공간 변환

      - 퍼셉트론이 2개라면

        1. 각각으로 보면 입력당 결과가 2개씩 나옴. (1이냐 0이냐)

           ![image-20220927154546123](C:\Users\wlsgy\AppData\Roaming\Typora\typora-user-images\image-20220927154546123.png)

        2. 병렬로 연결해서 보면, 새로운 공간으로 mapping이 된다.

           ![image-20220927154605654](C:\Users\wlsgy\AppData\Roaming\Typora\typora-user-images\image-20220927154605654.png)

        3. 즉, 퍼셉트론이 하나의 직선을 얘기하는 것이므로,

           퍼셉트론의 갯수  = n 이라면, 공간을 n개의 직선으로 잘라낸 만큼의 차원 공간으로 나올 수 있음

  - Sigmoid(현재는 RELU) 활성함수를 도입. 이전에 쓰인 계단함수와는 다르게 출력값이 연속값이므로, 출력을 신뢰도로 간주함으로써 융퉁성있는 의사결정이 가능

    - 활성함수를 통해 딱딱한 공간 분할을 부드러운 공간 분할로 바꾸었음

    - ***종류*** ![image-20220927155235545](C:\Users\wlsgy\AppData\Roaming\Typora\typora-user-images\image-20220927155235545.png)

      - 1차 도함수 계산이 빠르다는 특징이 있음

      

  - 오류 역전파 알고리즘을 사용. 역방향으로 진행하면서 한 번에 한 층씩 gradient를 계산하고 가중치를 갱신하는 방식의 오류 역전파 알고리즘을 사용한다.