---
description: >-
  다음과 같이 Hash에 관련된 릴레이 퀴즈 문제가 주어졌습니다. 각자 자신이 알고 있는 범위 내에서 최대한 상세하게 답변을 해주세요. 객관식
  문제의 경우는 답을 선택한 후, 그 이유를 함께 설명해주세요.
---

# Hash Relay Quiz!

### 문제1 <a href="#eb-ac-b8-ec-a0-9c1" id="eb-ac-b8-ec-a0-9c1"></a>

Hash 충돌 처리에는 크게 두 가지 기법이 있습니다. 각각 (Separate) Chaining 방식과 Open Address 방식이라고 부릅니다. 이에 대해 동작 방식을 간단하게 설명해주세요.

➔ 아래 페이지에서 자세하게 소개하고 있습니다!

{% content-ref url="hash-collision.md" %}
[hash-collision.md](hash-collision.md)
{% endcontent-ref %}

\


### 문제 2 <a href="#eb-ac-b8-ec-a0-9c-2" id="eb-ac-b8-ec-a0-9c-2"></a>

길이 10의 해쉬 테이블(index 0 \~ 9)이 있습니다. 해쉬 함수 h(k) = k mod 10 일 때, 다음의 조건에 맞게 키 값 106, 204, 52, 73, 82, 13 를 순서대로 해쉬 테이블에 추가하세요. (화이트 보드 사용)

#### 문제 2-1 <a href="#eb-ac-b8-ec-a0-9c-2-1" id="eb-ac-b8-ec-a0-9c-2-1"></a>

* 해쉬 테이블이 충돌 해결을 위해 Chaining 방식을 사용합니다.

#### 문제 2-2 <a href="#eb-ac-b8-ec-a0-9c-2-2" id="eb-ac-b8-ec-a0-9c-2-2"></a>

* 해쉬 테이블이 충돌 해결을 위해 Open Addressing 방식을 사용하며, Linear probing을 사용해서 바로 다음 버킷을 탐사합니다.
  * 참고> Linear Probing(탐사)은 해당 버킷이 충돌일 경우, 일정 구간 떨어진 버킷에 값을 넣을 수 있는지 탐사하는 기법입니다. 만일 탐색한 다음 버킷에도 값을 넣을 수 없다면 그 다음 버킷을 반복적으로 탐사합니다.

\


### 문제 3 <a href="#eb-ac-b8-ec-a0-9c-3" id="eb-ac-b8-ec-a0-9c-3"></a>

문제 2에서 작성한 두 개의 해쉬 테이블 상태를 바탕으로 다음의 문제를 푸세요. (화이트 보드 사용)

#### 문제 3-1 <a href="#eb-ac-b8-ec-a0-9c-3-1" id="eb-ac-b8-ec-a0-9c-3-1"></a>

* 52와 82를 순서대로 삭제해보세요.

#### 문제 3-2 <a href="#eb-ac-b8-ec-a0-9c-3-2" id="eb-ac-b8-ec-a0-9c-3-2"></a>

* 각 방식의 특징와 장/단점을 유추해서 설명해주세요.

\


### 문제 4 <a href="#eb-ac-b8-ec-a0-9c-4" id="eb-ac-b8-ec-a0-9c-4"></a>

Chaining 방식을 사용하는 길이 10의 해쉬 테이블(index 0 \~ 9)이 있습니다. 이 해쉬 테이블에 0 \~ 3060까지의 값을 넣을 예정입니다. 이 때, 가장 고른 분포를 보이는 해쉬 함수를 고르고 선택한 이유를 설명해주세요.

1. h(i) = (12 \* i) mod 10
2. h(i) = (11 \* i^2) mod 10
3. h(i) = i^2 mod 10
4. h(i) = i^3 mod 10

➔ 일단 생각하기 전에 직접 테스트를 해봤는데 2, 3, 4번은 모두 동일한 분포를 보이는 듯 하네요... \
&#x20;   제가 뭔가 잘못한 걸까요?

```
import java.util.Map;
import java.util.HashMap;

public class hash {
	public static void main(String[] args) {
		Map<Integer, Integer> map = new HashMap<>();
		int num = 3060;
		
		for(int i = 0; i <= num; i++) {
			int index = hashFunction1(i);
			if(map.containsKey(index))
				map.put(index, map.get(index) + 1);
			else
				map.put(index, 1);
		}

		System.out.println("(12 * key) mod 10 결과");
		for( int key : map.keySet() ) {
            		System.out.println( String.format("키 : %s, 값 : %s", key, map.get(key)) );
        	}
		System.out.println("----------------------");

		map.clear();
		for(int i = 0; i <= num; i++) {
			int index = hashFunction2(i);
			if(map.containsKey(index))
				map.put(index, map.get(index) + 1);
			else
				map.put(index, 1);
		}

		System.out.println("(11 * key ^ 2) % 10 결과");
		for( int key : map.keySet() ) {
			System.out.println( String.format("키 : %s, 값 : %s", key, map.get(key)) );
		}
		System.out.println("----------------------");

		map.clear();
		for(int i = 0; i <= num; i++) {
			int index = hashFunction3(i);
			if(map.containsKey(index))
				map.put(index, map.get(index) + 1);
			else
				map.put(index, 1);
		}

		System.out.println("(key ^ 2) mod 10 결과");
		for( int key : map.keySet() ) {
			System.out.println( String.format("키 : %s, 값 : %s", key, map.get(key)) );
		}
		System.out.println("----------------------");

		map.clear();
		for(int i = 0; i <= num; i++) {
			int index = hashFunction4(i);
			if(map.containsKey(index))
				map.put(index, map.get(index) + 1);
			else
				map.put(index, 1);
		}

		System.out.println("(key ^ 3) mod 10 결과");
		for( int key : map.keySet() ) {
			System.out.println( String.format("키 : %s, 값 : %s", key, map.get(key)) );
		}
	}

	public static int hashFunction1(int key) {
		return (12 * key) % 10;
	}

	public static int hashFunction2(int key) {
		return (11 * key ^ 2) % 10;
	}

	public static int hashFunction3(int key) {
		return (key ^ 2) % 10;
	}

	public static int hashFunction4(int key) {
		return (key ^ 3) % 10;
	}
}
```

<figure><img src="../.gitbook/assets/스크린샷 2022-12-04 오후 7.53.43.png" alt=""><figcaption></figcaption></figure>
