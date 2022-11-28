---
description: HashMap vs TreeMap에 대해 할 말 다 하시오.
---

# HashMap vs TreeMap

## HashMap

HashMap은 Map 인터페이스를 구현한 대표적인 Map Collection입니다.

Map 인터페이스를 상속하고 있기에 Map의 성질을 그대로 가지고 있습니다. Map은 키와 값으로 구성된 Entry 객체를 저장하는 구조를 가지고 있는 자료구조입니다. 여기서 키와 값은 모두 객체입니다. 값은 중복 저장될 수 있지만 키는 중복 저장될 수 없습니다. 만약 기존에 저장된 키와 동일한 키로 값을 저장하면 기존의 값은 없어지고 새로운 값으로 대치됩니다.&#x20;

HashMap은 이름 그대로 해싱을 사용하기 때문에 많은 양의 데이터를 검색하는 데 있어서 뛰어난 성능을 보입니다.

### HashTable과 HashMap의 차이

HashMap과 사용법이 거의 동일한 컬렉션(Collection)에는 Hashtable이 있습니다. 두 클래스의 차이점은 **Thread-Safe 여부**에 있습니다.

|             | HashTable | HashMap |
| :---------: | :-------: | :-----: |
| Thread-Safe |     O     |    X    |
| Synchronize |     O     |    X    |
|    Speed    |   Slower  |  Faster |

****

****

****
