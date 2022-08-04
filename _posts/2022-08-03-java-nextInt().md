---
layout: single
title: nextInt()와 nextLine() 차이
---

저번 포스팅에서 Scanner클래스를 이용하여 화면으로부터 입력받는 방법을 배워보았는데, 그 중에서도 nextLine()메서드로 문자열을 입력받아 Inter.parseInt()메서드를 이용하여
문자열을 숫자로 변환하여 출력하는 방법을 배웠다.  
하지만 타입의 변환없이도 숫자를 바로 입력받을 수 있는 nextInt()나 nextFloat()와 같은 메서드도 있다고 배웠다.  
그러면 당연히 번거로운 과정을 생략하게 해주는 nextInt()메서드를 쓰는 것이 좋겠다고 생각하겠지만, 이 메서드는 연속적으로 값을 입력받아 사용하기에는 까다롭다고 하여 nextLine()을 사용하는 것이
더 나은 방법이라고 책(자바의 정석 3)에 나와있다.  
도대체 어떤 부분이 까다로우며, nextLine()과 nextInt()의 차이점이 무엇인지 궁금하여 이번 포스팅을 작성하게 되었다.  
* * *
## - nextInt()
- 사용자 입력의 가장 **마지막 개행문자(엔터, newline)** 를 제거하지 않으며, **공백 전까지만** 숫자로 입력 받는다.  

## - nextLine()
- 문자 또는 문장 라인 전체를 입력받으며, **개행문자까지 다 가져온다.** 

## - nextInt()의 잘못된 코드
- nextint()메서드가 개행문자를 제거하지 않으므로, **버퍼에 개행문자가 남게된다.** 그래서 nextLine()메서드가 개행문자를 받게되어 사용자가 원하는 문자열을 입력할 수 없다.
- 그러므로 nextInt()메서드는 **연속적으로 다른 타입의 값**을 입력받아서 사용하기에 까다롭다. 
    ```java
    import java.util.*; // Scanner클래스를 사용하기 위해 추가

    public class ScannerEx {
	    public static void main(String[] args) {
		   Scanner scanner = new Scanner(System.in); // Scanner클래스의 객체를 생성
		   System.out.print("나이를 입력해주세요.>");
		   int age = scanner.nextInt();  
       
		   System.out.print("성함을 입력해주세요.>");
		   String name = scanner.nextLine();
       
		   System.out.printf("\nage = %d\n", age);	
		   System.out.printf("name = %s\n", name);	
	    }
    }
    ```
    > **실행결과**
    > > 나이를 입력해주세요.>25  
        성함을 입력해주세요.>  
        age = 25  
        name =   

## 해결방법
1. 이전 포스팅에서 언급했듯이 **모든 값을 nextLine()** 으로 입력받아서 **타입을 변환**해준다.
2. **버퍼에 남아있는 개행문자를 제거**하기 위해 nextint() 다음에 **scanner.nextLine()을 한 줄 추가**해준다.
    ```java
    import java.util.*; // Scanner클래스를 사용하기 위해 추가

    public class ScannerEx {
	    public static void main(String[] args) {
		   Scanner scanner = new Scanner(System.in); // Scanner클래스의 객체를 생성
		   System.out.print("나이를 입력해주세요.>");
		   int age = scanner.nextInt();
		   scanner.nextLine(); // 개행문자 제거
		   
		   System.out.print("성함을 입력해주세요.>");
		   String name = scanner.nextLine();
       
		   System.out.printf("\nage = %d\n", age);	
		   System.out.printf("name = %s\n", name);	
  	    }
    }
    ```
    > **실행결과**
    > > 나이를 입력해주세요.>25  
        성함을 입력해주세요.>홍길동         
        age = 25  
        name = 홍길동
