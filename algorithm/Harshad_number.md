### 하샤드 수

양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 예를 들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다. 
자연수 x를 입력받아 x가 하샤드 수인지 아닌지 검사하는 함수, solution을 완성해주세요.

제한 조건
x는 1 이상, 10000 이하인 정수입니다.

```java
package algorithm;

public class HarshadNumber{
    public boolean isHarshad(int num){
//  String.valueOf() - 파라미터가 null이면 문자열 "null"을 만들어서 String으로 반환한다.
//  split("")은 ""안에 있는 값(ex , :) 으로 나누는 메소드인데 아무것도 지정하지 않으면 한글자씩 짜르게된다 
//	Integer.valueOf 의 리턴되는 결과값은 new Integer() 로 객체
//	Integer.parseInt 의 리턴되는 결과값은 int 로 기본 자료형 (primitive type)으로 반환한다.
	
	String[] temp = String.valueOf(num).split("");

    int sum = 0;
    for (String s : temp) {
        sum += Integer.parseInt(s); //parse(사전:분석하다,해석하다) 다른 데이터 형식으로 바꾼다는 의미
    }

    if (num % sum == 0) {
            return true;
    } else {
      return false;
    }
    }

    // 아래는 테스트로 출력해 보기 위한 코드입니다.
    public static void  main(String[] args){
        HarshadNumber sn = new HarshadNumber();
        System.out.println(sn.isHarshad(18));
    }
}
```

