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
- 공백 전까지의 숫자만 입력받으므로, 공백 이후의 숫자는 버퍼에 남아있게되어 다음 값을 입력받지않고 바로 22가 출력이 된다.
    ```java
    import java.util.*; // Scanner클래스를 사용하기 위해 추가

    public class ScannerEx {
	    public static void main(String[] args) {
		   Scanner scanner = new Scanner(System.in); // Scanner클래스의 객체를 생성
		   System.out.print("첫번째 정수를 하나 입력해주세요.>");
       int first = scanner.nextInt();
       System.out.print("\n두번째 정수를 하나 입력해주세요.>");
       int second = scanner.nextInt();
       System.out.printf("\nfirst = %d\n", first);	
		   System.out.printf("second = %s\n", second);	
	    }
    }
    ```
    <img src="/Documents/result1.png" width="40%" height="30%"></img>
