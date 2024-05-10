# 시간복잡도
clothes.forEach 루프:
이 루프는 clothes 배열의 각 요소를 한 번씩 처리합니다. 배열의 길이가 N이라면, 이 루프는 N번 실행됩니다.
루프 내부에서는 간단한 조건 검사와 할당 연산이 수행됩니다. 이 조건 검사(if (clothesMap[type]))는 객체의 속성 접근을 통해 수행되며, JavaScript에서 객체의 속성 접근은 평균적으로 O(1)
O(1)의 시간 복잡도를 가집니다.
따라서, 이 루프의 시간 복잡도는 O(N)입니다.

for (const type in clothesMap) 루프:
이 루프는 clothesMap 객체의 모든 키(의상의 종류)에 대해 실행됩니다. 가정하에 의상의 종류의 수를 K라고 할 때, 이 루프는 최대 K번 실행됩니다.
루프 내에서는 간단한 곱셈과 증감 연산이 수행됩니다. 이러한 연산들은 O(1)의 시간 복잡도를 가집니다.
clothesMap의 키 수 K는 clothes의 요소 수N을 초과할 수 없으므로, 이 루프의 시간 복잡도 역시 최대 O(N)입니다.
종합적으로, 두 루프 모두 O(N)의 시간 복잡도를 가지며, 서로 연속적으로 실행되기 때문에 전체 함수의 시간 복잡도는 O(N)입니다. 여기서 N은 입력 배열 clothes의 길이, 즉 코니가 가진 의상의 수를 나타냅니다. 

# 알게된 지식
```
for (const type in clothesMap) {
    answer *= (clothesMap[type] + 1)
}
    
return answer - 1;
```
이 부분은 의상 조합을 계산하는 과정을 나타냅니다.<br>
아래는 의상조합을 계산하는 과정에 대해 상세하게 설명입니다.

1. 조합의 기본 계산
초기화: 

combinations 변수를 1로 초기화합니다. 이 값은 각 의상 종류별 선택 가능한 옵션의 수를 곱해나가는 데 사용됩니다.
곱셈의 이유: 각 의상 종류에서 선택할 수 있는 옵션의 수는 해당 종류의 의상 수에 "그 종류의 의상을 하나도 선택하지 않는 경우"를 추가해서 계산합니다. 예를 들어, 어떤 종류에서 의상이 3개 있다면, 그 종류에서 선택할 수 있는 옵션은 3개의 의상 중 하나를 선택하거나 아예 선택하지 않는 경우까지 총 4개가 됩니다.

2. 계산 과정
루프에서의 계산: 

for 루프를 사용하여 clothesSet 객체의 각 type을 순회합니다. clothesSet[type]는 해당 type의 의상 수를 나타냅니다. (clothesSet[type] + 1)은 이 의상 수에 "선택하지 않는 경우"를 추가한 것입니다. 이 값을 combinations에 계속 곱해 나가면, 가능한 모든 조합의 수를 계산할 수 있습니다.

3. 조합 수에서
왜 1을 빼나: 

모든 종류에서 "선택하지 않는 경우"도 포함해서 계산했기 때문에, 이는 모든 종류에서 의상을 하나도 선택하지 않는 경우도 포함하고 있습니다. 하지만 문제에서는 코니가 최소 한 개 이상의 의상을 입는다고 했습니다. 따라서, 아무것도 선택하지 않는 하나의 조합(모든 의상을 선택하지 않는 경우)을 최종 결과에서 제거해야 합니다.
이 과정을 통해, 가능한 모든 옷 조합의 수를 정확하게 계산할 수 있습니다. 각 종류별로 의상을 입거나 입지 않는 선택을 하고, 이러한 선택들을 조합하여 최종적으로 얼마나 다양한 방식으로 옷을 입을 수 있는지를 계산하는 것입니다.
