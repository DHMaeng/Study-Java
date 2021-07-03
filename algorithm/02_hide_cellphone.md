## 핸드폰 번호 가리기

프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 `*`으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

##### 제한 조건

- s는 길이 4 이상, 20이하인 문자열입니다.

```java
class Solution {
    public String solution(String phone_number) {
        String answer = "";
        String[] temp = phone_number.split("");
        for(int i = 0 ; i < temp.length-4 ; i++){
            temp[i] = "*";
        }
        answer = String.join("",temp);
        return answer;
    }
}
```



**length구분!**

array.length / string.length()



**split vs join**

🔸split : `String[] array = str.split(",");`

🔸join : `str = String.join(",",array);`



### 다른 사람 풀이

🔸`str.toCharArray()` : 문자열을 charArray형으로 반환.

🔸`String.valueof(type)`: type을 String으로 반환.

```java
class Solution {
  public String solution(String phone_number) {
     char[] ch = phone_number.toCharArray();
     for(int i = 0; i < ch.length - 4; i ++){
         ch[i] = '*';
     }
     return String.valueOf(ch);
  }
}
```



**substring! 의 사용**

🔸`str.substring(int index)` : **0부터 시작** index 해당 위치를 **포함**하여 이후의 모든 문자열을 리턴 시키는 함수 ex) `String str = "0123456789";` `str.substring(5)` => 56789

🔸`String substring(int beginIndex, int endIndex)` : beginIndex 위치에서 시작하여 endIndex 전 위치까지의 값을 리턴 

ex) `String str = "0000003565120";`
`System.*out*.println(str.substring(6, 12)); `=> 356512

| 문자열   | 0    | 0    | 0    | 0    | 0    | 0    | **3** | **5** | **6** | **5** | **1** | **2**  | 0    |
| -------- | ---- | ---- | ---- | ---- | ---- | ---- | ----- | ----- | ----- | ----- | ----- | ------ | ---- |
| index 값 | 0    | 1    | 2    | 3    | 4    | 5    | **6** | 7     | 8     | 9     | 10    | **11** | 12   |

```java
class Solution {
  public String solution(String phone_number) {
      String answer = "";

        for (int i = 0; i < phone_number.length() - 4; i++)
            answer += "*";

        answer += phone_number.substring(phone_number.length() - 4);

        return answer;
  }
}
```

