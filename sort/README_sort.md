정렬(Sort) 알고리즘
------------------
1. 버블 정렬
- 이웃한 두 원소의 대소 관계를 비교하여 필요에 따라 교환을 반복하는 알고리즘
- 시간 복잡도 : O(n²)

2. 선택 정렬
- 가장 작은 원소부터 선택해 알맞은 위치로 옮기는 작업을 반복하여 정렬하는 알고리즘
- 시간 복잡도 : O(n²)

3. 삽입 정렬
- 주목한 원소보다 더 앞쪽에서 알맞은 위치로 삽입하며 정렬하는 알고리즘
- 시간 복잡도 : O(n²)

4. 퀵 정렬
- 가장 빠른 정렬 알고리즘으로 알려져 있음
- pivot(피벗)을 도입 = 그룹을 나누는 기준
- 피벗 이하인 원소를 배열 왼쪽으로, 피벗 이상인 원소를 배열 오른쪽으로 이동시켜야 한다.
- 반복하면 배열은 피벗 이하인 그룹과 피벗 이상인 그룹으로 나뉘게 됨
- 시간 복잡도 : O(n log n)

5. 쉘 정렬
- 단순 삽입 정렬의 장점은 살리고 단점은 보완하여 더 빠르게 정렬
- 먼저 정렬할 배열의 원소를 그룹으로 나눠 각 그룹별로 정렬을 수행
- 그 후 정렬된 그룹을 합치는 작업을 반복하여 원소의 이동 횟수를 줄이는 방법
- 시간 복잡도는 O(n¹﹒²⁵)이고 단순 정렬의 시간 복잡도인 O(n²) 보다 매우 빠르다

6. 힙 정렬
- 힙의 특성을 이용하여 정렬
- 힙은 '부모의 값이 자식의 값보다 항상 크다'는 조건을 만족하는 완전 이진 트리
- 힙 정렬은 '힙에서 최댓값은 루트에 위치한다'는 특징을 이용하여 정렬하는 알고리즘
- 다음과 같은 작업을 반복
	- 힙에서 최댓값인 루트를 꺼낸다.
	- 루트 이외의 부분을 힙으로 만든다.
- 시간 복잡도 : O(log n)

[위 정렬들의 소스코드](https://github.com/knurii/computerAlgorithm/blob/main/sort/src/sort.py "src")

7. 정렬 문제의 하한 (lower bound)
- 이론적으로 Ω(nlog₂n) 보다 성능이 좋아질 수 없다
- 정해지지 않은 x,y,z 세개의 숫자가 있다 (입력개수 3개)
- 상태 공간 : [x,y,z] [x,z,y] [y,x,z] [y,z,x] [z,x,y] [z,y,x] (대소관계 경우의수  k = n!, n은 입력 개수)
- 한번에 비교할 수 있는 방식이 없음
- 지금 컴퓨터는 두개의 입력을 받아 한개의 출력을 하는 구조
- decision tree(결정 트리)

![decision_tree](https://user-images.githubusercontent.com/101931446/166949115-76ff5393-4eea-4874-b377-1c3f6a3ebaf5.jpg)
- 여기서 봐야 할 건 비교 횟수
- 최대 3회 비교
- k개 leaf node 있으면 높이는 log₂k 보다 크다
- log₂k = log₂n! = log₂n(n-1)(n-2) ⋯ n = nlog₂n < h (높이, 비교횟수)


알고리즘 성능 분석
----------------
각 정렬의 시간복잡도에 근접하는지 알아보기 위하여, 리스트에 저장된 값들(2⁵~2²⁰) 순서를 랜덤으로 바꾸었다.
그 다음 순서가 바뀐 리스트에 대해 각각의 정렬을 수행한 후 입력 개수 별 수행 시간을 출력하였다.

[1번의 random data src](https://github.com/knurii/computerAlgorithm/blob/main/sort/src/1%20time/random_data_time.py "1 time")

💻 출력 화면
<img width="1440" alt="sort_print" src="https://user-images.githubusercontent.com/101931446/166950154-6ef1f3e4-0d9d-44da-9f5c-01bda10cbf5c.png">

이 과정을 100번 반복 한 후 평균을 낸 수행시간을 구하였다.

[소스코드](https://github.com/knurii/computerAlgorithm/tree/main/sort/src/100%20times "100times")

![1-time-graph](https://user-images.githubusercontent.com/101931446/166964267-daf1d0f2-57cc-4a1f-a4b3-2dfa0f0b5fbd.jpg)

그래프가 들쭉날쭉하나 전체적인 모양은 각 정렬의 시간복잡도 식에 부합한다.

![100-times-graph](https://user-images.githubusercontent.com/101931446/166964273-7c01e932-0dc6-430b-8dcd-23c72b0f11de.jpg)

매끈하게 다듬어진 형태를 관찰할 수 있다.
그리고 수행 시간에 대해 성능이 확연하게 드러난다.
가자 빠른 정렬인 퀵정렬의 수행시간이 가장 짧고, 기본 정렬인 버블 정렬의 수행 시간이 가장 긴 것을 확인할 수 있다.


