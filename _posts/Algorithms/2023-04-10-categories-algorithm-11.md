---
title: "[Algorithm] 개미군단"
categories:
  - Algorithms
tags:
  - [Algorithms, JavaScript, Remainder(%), Math.floor]
permalink: /Blog/algorithm-11/
toc: true
toc_sticky: true
toc_label: # "ALGORITHM"
date: 2023-04-10
last_modified_at: 2023-04-10
---

## Algorithm 풀기

### 문제 설명

개미 군단이 사냥을 나가려고 합니다. 개미군단은 사냥감의 체력에 딱 맞는 병력을 데리고 나가려고 합니다. 장군개미는 5의 공격력을, 병정개미는 3의 공격력을 일개미는 1의 공격력을 가지고 있습니다. 예를 들어 체력 23의 여치를 사냥하려고 할 때, 일개미 23마리를 데리고 가도 되지만, 장군개미 네 마리와 병정개미 한 마리를 데리고 간다면 더 적은 병력으로 사냥할 수 있습니다. 사냥감의 체력 hp가 매개변수로 주어질 때, 사냥감의 체력에 딱 맞게 최소한의 병력을 구성하려면 몇 마리의 개미가 필요한지를 return하도록 solution 함수를 완성해주세요.

### 제한사항

- hp는 자연수입니다.
- 0 ≤ hp ≤ 1000

### 입출력 예

| hp  | result |
| --- | ------ |
| 23  | 5      |
| 24  | 6      |
| 999 | 201    |

### 입출력 예 설명

- 입출력 예 #1

  - hp가 23이므로, 장군개미 네마리와 병정개미 한마리로 사냥할 수 있습니다. 따라서 5를 return합니다.

- 입출력 예 #2

  - hp가 24이므로, 장군개미 네마리 병정개미 한마리 일개미 한마리로 사냥할 수 있습니다. 따라서 6을 return합니다.

- 입출력 예 #3

  - hp가 999이므로, 장군개미 199 마리 병정개미 한마리 일개미 한마리로 사냥할 수 있습니다. 따라서 201을 return합니다.

### 나의 풀이 방법

```js
function solution(hp) {
  let answer = Math.floor(hp / 5) + Math.floor((hp % 5) / 3) + ((hp % 5) % 3);
  return answer;
}
```

> 한 마리의 정수로 받기 위해 `Math.floor()`함수를 사용해 나눗셈 연산자의 결과를 출력한다. 나머지 연산자 `%`의 경우 나머지(remainder)를 정수로 반환하기 때문에 `Math.floor()`함수를 사용하지 않아도 된다. <br/>
> 사냥감의 체력(24)에 최소한의 병력을 사용해야 하므로 장군 개미(5)를 먼저 나눠 준다. 그리고 나머지 연산자를 사용해 `사냥감의 체력(24) % 장군 개미(5)`의 나머지 값(3)을 구하고 병정개미(3)를 나눠준다. <br>
> 마지막으로 일개미를 이용해야 하는 경우는 1이나 2가 남았을 경우이므로 `사냥감의 체력(24) % 장군 개미(5) % 3`으로 나머지 값을 구해 모두 더해준다.

### 🐳 Remainder (%) / 나머지 연산자 %

- 나머지 연산자는 % 기호로 나타내지만, 비율을 나타내는 퍼센트와 관련없다. 나머지 연산자를 사용한 표현식 `a % b`는 a를 b로 나눈 후 그 나머지(remainder)를 정수로 반환해준다.

```js
console.log(13 % 5);
// output: 3

console.log(-13 % 5);
// output: -3

console.log(4 % 2);
// output: 0

console.log(-4 % 2);
// output: -0
```
