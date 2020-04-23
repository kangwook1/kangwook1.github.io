---
layout: single
date: 2020-04-24 12:30 +0900
title: Greedy Algorithm 
author: kangwook
---

오늘은 그리디 알고리즘에 대해 알아보겠습니다.

그리디 알고리즘은 기업 코딩테스트에서 종종 볼 수 있는 알고리즘입니다.

그래서 그리디 알고리즘을 연습 할 수 있는 예제를 소개드리겠습니다.

보통 그리디 알고리즘 예제라하면 거스름돈과 활동 선택 등 이 있는데요.

오늘 소개할 예제는 프로그래머스 코딩테스트 연습문제인 *조이스틱* 예제입니다.

## 문제 설명

조이스틱으로 알파벳 이름을 완성하세요. 맨 처음엔 A로만 이루어져 있습니다.
ex) 완성해야 하는 이름이 세 글자면 AAA, 네 글자면 AAAA

조이스틱을 각 방향으로 움직이면 아래와 같습니다.

```
▲ - 다음 알파벳
▼ - 이전 알파벳 (A에서 아래쪽으로 이동하면 Z로)
◀ - 커서를 왼쪽으로 이동 (첫 번째 위치에서 왼쪽으로 이동하면 마지막 문자에 커서)
▶ - 커서를 오른쪽으로 이동
```

예를 들어 아래의 방법으로 JAZ를 만들 수 있습니다.

```
- 첫 번째 위치에서 조이스틱을 위로 9번 조작하여 J를 완성합니다.
- 조이스틱을 왼쪽으로 1번 조작하여 커서를 마지막 문자 위치로 이동시킵니다.
- 마지막 위치에서 조이스틱을 아래로 1번 조작하여 Z를 완성합니다.
따라서 11번 이동시켜 "JAZ"를 만들 수 있고, 이때가 최소 이동입니다.
```

만들고자 하는 이름 name이 매개변수로 주어질 때, 이름에 대해 조이스틱 조작 횟수의 최솟값을 return 하도록 solution 함수를 만드세요.

##### 제한 사항

- name은 알파벳 대문자로만 이루어져 있습니다.
- name의 길이는 1 이상 20 이하입니다.

##### 입출력 예

| name   | return |
| ------ | ------ |
| JEROEN | 56     |
| JAN    | 23     |



## 코드

~~~
public class 조이스틱 {

	public static void main(String[] args) {
		String name = "JEROEN";
		int len = name.length();
		int min_move = len-1; 
		// 처음부터 끝까지 오른쪽으로 갈 때의 이동횟수

		int answer = 0 ;
		
		for(int i=0; i<len; ++i) {
			// 1. 상하: A로 가는 가까운 길
			// a ... l  'm'  n ... z
			if(name.charAt(i)<='M') {
				answer += name.charAt(i)-'A';
			}
			else {
				answer +='Z'-name.charAt(i)+1;
			}
			
			// 2. 좌우: 연속된 A의 등장에 따라 달라지는 최소 움직임
			int next = i+1;
			while(next<len && name.charAt(next)=='A') {
				++next;
			}
			min_move = Math.min(min_move,i+len-next+Math.min(i,len-next));
			// len - next : 
			// 총 길이에서 현재 바로 다음에 연속된 A가 지나고 남은 문자 갯수
			// i : 오른쪽으로의 현재까지의 이동횟수
			// i + len - next + i : 현재까지 왔다가 다시 돌아가서 남은 거 까지 가는 이동 횟수
			// min(i,len-next)에서,
			// i 보다 len-next 값이 작은 경우에 len-next를 선택하는데
			// 이는, 마지막 문자가 A인 경우를 제외 하면
			// 무조건 len-1 보다 크게 된다 (len-next >=1)
			// 따라서,i가 len-next(남은 문자)보다 큰 경우는
			// 굳이 왼쪽으로 다시 돌아갈 필요가 없다.
			// 대신 끝이 A인 경우는, len-next가 0이 되므로,
			// 무조건 len-1 보다 작은 i 가 최소 이동횟수가 된다.
			// 따라서 Math.min(i,len-next) 이 부분은 식에서 필요하게 된다.
			
			
		}
		answer += min_move;
		
		System.out.println(answer);
	}

}
~~~

---출처--- 

[https://mishuni.tistory.com/36?category=828254](https://mishuni.tistory.com/36?category=828254)

## 여담

이 코드를 보고 String 문자열 명령어인 charAt를 알게 되었고 조이스틱을 상하방향으로 움직일 때는 최소 움직임을 계산하는 건 쉬웠지만

좌우 방향으로 움직일 때 최소 움직임을 계산하는 방법이 되게 까다로웠고 코드를 한참 보고나서야 이해가 되었다. 

좌우 방향 최소 움직임을 구현 할 수 있으면 코딩테스트는 합격이다!





