---
layout : post
title : JAVA에서 Final 은?
---

# Final
++final은 abstract과 반대되는 개념이다++

*abstract을 간단하게 정리하면 class 앞에 abstract를 작성해야하며, 반드시 abstract은 ==상속== 받아야한다. 또한, class 앞에 abstract가 없다고 하더라도 멤버함수에 abstract 되면 이또한 반드시 ==상속== 받아야 한다. 일종에 재정의라고 생각하면 될것 같다. 상속이라는 규제가 따를뿐*

코드를 보면 쉽게 이해할 수 있다.
```
class finaltest{
	static double x = 1.1;
}

public class test{
	public void main(String args[]){
    	finaltest f1 = new finaltest();
        ... //static은 생성된 객체 끼리 공유가 가능하기때문에 x값을 고정으로 사용한다면 좋지 않다. 따라서 final을 붙여쓴다. 변경을 막기 위함
    	}
	}
```
==final로 지정된 변수는 수정할 수 없다.==

## 메소드 와 final
다음 두가지를 살펴보자.
```
class finaltest{
	final default void fianltestfunction(){
    	...
    }
}
public class finaltestmain extends finaltest{
	public void main(String args[]){
    ...
    }
    void finalestfunction(){
        	...
        }
    }
}
//error : final은 변경할수 없다.
```
```
final class finaltest{
	 default void fianltestfunction(){
    	...
    }
}
public class finaltestmain extends finaltest{
	public void main(String args[]){
    ...
    }
    void finalestfunction(){
        	...
        }
    }
}
//error : class도 마찬가지다.
```

틀린게 있다면 댓글 주시면 감사하겠습니다!
# Reference 
생활코딩 자바프로그래밍 입문 도서

[TOC]

