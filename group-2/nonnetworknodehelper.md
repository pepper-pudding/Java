---
description: GameAnvil의 NonNetworkNodeHelper 클래스의 다음 자료 구조에 대해 아주 구체적으로 설명하시오.
---

# NonNetworkNodeHelper

```
// future
private final static int FUTURES_MAX_SIZE = GameAnvilConfig.common().getRouterFutures(); //default: 65536
private List<SettableFuture<GameAnvilPacket>> futures = new ArrayList<>(FUTURE_MAX_SIZE);
```
