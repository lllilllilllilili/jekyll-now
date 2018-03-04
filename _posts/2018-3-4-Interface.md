---
layout : post
title : Interface?
---

#인터페이스

결론적으로 몸체는 없이 정의되어있는 메소드형태입니다.
abstract과 마찬가지로 반드시 구현해 줘야 하는 형태입니다.

## Interface를 사용하는이유, abstract과 다른점
두 개념이 비슷하고 어쩌면 차이가 없을지도 모른다. 그러나, 코드등을 보면서 느꼈던 점은== abstract ==는 상위클래스에서 정의한 메소드를 하위 메소드에서 다양한 기능으로 구현가능하다는점. 구체적인 메소드도 포함가능하다.
==interface==는 여러 개발자들이 구현시 일종에 약속을 가지고 메소드 형식을 정하여 협엽하는 방식이라고 생각했다. 구체적인 메소드는 (로직이 담긴) 포함할 수 없다.

## Interface 규칙
==abstract == 와 마찬가지로 public으로 정의해야 한다. 한 클래스에 여러개의 interface를 받을 수 있다는 점.
메소드는 몸체 밖에 없다.
다음의 두 가지 형식을 보면서 Interface에 익숙해지자.
```
package *
interface interfaceTest{
	public void interface1(); //블록은 만들지 않는다.
}
interface interfaceTest2{
	public void interface2();
}
class interfaceMan implements interfaceTest, interfaceTest2{
	public void interface1(){
    ...
    }
    public void interface2(){
	...    
    }
}


```

```
package *
interface interfaceTest{
	public void interface1(); //블록은 만들지 않는다.
}
interface interfaceTest2 extends interfaceTest {
	public void interface2();
}
class interfaceMan implements interfaceTest2{
	public void interface1(){
    ...
    }
    public void interface2(){
	...    
    }
    //상속도 가능하다. 하지만 반드시 구현해줘야한다. 상속의 개념이랑      //적용되서 부모클래스에 접근가능하다.
    //Interface의 메소드는 public으로 나와야 한다.
}
```