# CSS

- flex

## flex
Flex는 Flexible box, Flexbox라고 부르기도 한다. 레이아웃 배치 전용 기능으로 고안되어 float나 inline-block을 이용한 기존 방식보다 강력하고 편리한 기능이 많다.
```
<div class="container">
	<div class="item">A</div>
	<div class="item">B</div>
	<div class="item">C</div>
</div>

해당 구조에서 부모 요소인 container를 Flex Container, 자식 요소인 item들을 Flex Item이라고 부른다.
Flex의 속성들은
1. 컨테이너에 적용하는 속성
2. 아이템에 적용하는 속성
두 가지로 나뉜다.
```
1. 컨테이너에 적용하는 속성
```
display: flex;
```
를 통해 Flex 컨테이너에 flex속성을 적용한다.
