# 완주하지 못한 선수

###### 문제 설명

수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

##### 제한사항

- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.

##### 입출력 예

| participant                                       | completion                               | return   |
| ------------------------------------------------- | ---------------------------------------- | -------- |
| ["leo", "kiki", "eden"]                           | ["eden", "kiki"]                         | "leo"    |
| ["marina", "josipa", "nikola", "vinko", "filipa"] | ["josipa", "filipa", "marina", "nikola"] | "vinko"  |
| ["mislav", "stanko", "mislav", "ana"]             | ["stanko", "ana", "mislav"]              | "mislav" |

##### 입출력 예 설명

예제 #1
"leo"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #2
"vinko"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

예제 #3
"mislav"는 참여자 명단에는 두 명이 있지만, 완주자 명단에는 한 명밖에 없기 때문에 한명은 완주하지 못했습니다.



### 풀이1

```java
import java.util.*;
class Solution {
    public String solution(String[] participant, String[] completion) {
        Arrays.sort(participant);
        Arrays.sort(completion);
        int i; //i를 밖에 선언해서 유효
        for (i = 0; i < completion.length; i++){
            if (!participant[i].equals(completion[i])){
                return participant[i];
            }
        }
        return participant[i]; //값이 배열 마지막에 있으면 for문 끝나고 return participant[i]; 에서 리턴
    }
}
```



### 풀이2

```java
import java.util.HashMap;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String answer = "";
        HashMap<String, Integer> hm = new HashMap<>();
        for (String player : participant) hm.put(player, hm.getOrDefault(player, 0) + 1);
        for (String player : completion) hm.put(player, hm.get(player) - 1);

        for (String key : hm.keySet()) {
            if (hm.get(key) != 0){
                answer = key;
            }
        }
        return answer;
    }
}
```

#### 1. getOrDefault([Object](https://docs.oracle.com/javase/8/docs/api/java/lang/Object.html) key, [V](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) defaultValue)

찾는 키가 존재한다면 찾는 키의 값을 반환하고 없다면 기본 값을 반환한다.

위 예제에선 처음에 put할때는 key값이 없으므로 기본값 0에 1을 더해서 저장되고 중복된 키값이 나오면 키값의 value(1)에 1을 더해 2가 된다.



#### 2. entrySet(), keySet() 메소드

Map에 값을 전체 출력하기 위해서는 entrySet(), keySet() 메소드를 사용하면 되는데 

entrySet() 메서드는 key와 value의 값이 모두 필요한 경우 사용하고, 

keySet() 메서드는 key의 값만 필요한 경우 사용한다.

- entrySet()

```java
Map<String, String> map = new HashMap<String, String>();
map.put("key01", "value01");
map.put("key02", "value02");
map.put("key03", "value03");
map.put("key04", "value04");
map.put("key05", "value05");

// 방법 01 : entrySet()
for (Map.Entry<String, String> entry : map.entrySet()) {
	System.out.println("[key]:" + entry.getKey() + ", [value]:" + entry.getValue());
}
```

- keySet()

```java
Map<String, String> map = new HashMap<String, String>();
map.put("key01", "value01");
map.put("key02", "value02");
map.put("key03", "value03");
map.put("key04", "value04");
map.put("key05", "value05");
        
// 방법 02 : keySet()
for (String key : map.keySet()) {
	String value = map.get(key);
    System.out.println("[key]:" + key + ", [value]:" + value);
}    
```



# 전화번호 목록

###### 문제 설명

전화번호부에 적힌 전화번호 중, 한 번호가 다른 번호의 접두어인 경우가 있는지 확인하려 합니다.
전화번호가 다음과 같을 경우, 구조대 전화번호는 영석이의 전화번호의 접두사입니다.

- 구조대 : 119
- 박준영 : 97 674 223
- 지영석 : 11 9552 4421

전화번호부에 적힌 전화번호를 담은 배열 phone_book 이 solution 함수의 매개변수로 주어질 때, 어떤 번호가 다른 번호의 접두어인 경우가 있으면 false를 그렇지 않으면 true를 return 하도록 solution 함수를 작성해주세요.

##### 제한 사항

- phone_book의 길이는 1 이상 1,000,000 이하입니다.
  - 각 전화번호의 길이는 1 이상 20 이하입니다.
  - 같은 전화번호가 중복해서 들어있지 않습니다.

##### 입출력 예제

| phone_book                        | return |
| --------------------------------- | ------ |
| ["119", "97674223", "1195524421"] | false  |
| ["123","456","789"]               | true   |
| ["12","123","1235","567","88"]    | false  |

##### 입출력 예 설명

입출력 예 #1
앞에서 설명한 예와 같습니다.

입출력 예 #2
한 번호가 다른 번호의 접두사인 경우가 없으므로, 답은 true입니다.

입출력 예 #3
첫 번째 전화번호, “12”가 두 번째 전화번호 “123”의 접두사입니다. 따라서 답은 false입니다.



### 풀이1 => 효율성 통과 x

```java
class Solution {
    public boolean solution(String[] phoneBook) {
       for(int i=0; i<phoneBook.length-1; i++) {
            for(int j=i+1; j<phoneBook.length; j++) {
                if(phoneBook[i].startsWith(phoneBook[j])) {return false;}
                if(phoneBook[j].startsWith(phoneBook[i])) {return false;}
            }
        }
        return true;
    }
}
```



### 풀이2

```java
import java.util.HashMap;
class Solution {
    public boolean solution(String[] phone_book) {
        boolean answer = true;
        HashMap<String, Integer> hm = new HashMap<>();
        
        for(int i = 0; i < phone_book.length; i++) {
            hm.put(phone_book[i], i);
        }
        
        for(int i = 0; i < phone_book.length; i++) {
            for(int j = 0; j < phone_book[i].length(); j++) {
                if(hm.containsKey(phone_book[i].substring(0,j))){
                    answer = false;
                    return answer;
                }
            }    
        }
        return answer;
    }
}
```

