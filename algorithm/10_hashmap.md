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



---



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



---



# 위장

###### 문제 설명

스파이들은 매일 다른 옷을 조합하여 입어 자신을 위장합니다.

예를 들어 스파이가 가진 옷이 아래와 같고 오늘 스파이가 동그란 안경, 긴 코트, 파란색 티셔츠를 입었다면 다음날은 청바지를 추가로 입거나 동그란 안경 대신 검정 선글라스를 착용하거나 해야 합니다.

| 종류 | 이름                       |
| ---- | -------------------------- |
| 얼굴 | 동그란 안경, 검정 선글라스 |
| 상의 | 파란색 티셔츠              |
| 하의 | 청바지                     |
| 겉옷 | 긴 코트                    |

스파이가 가진 의상들이 담긴 2차원 배열 clothes가 주어질 때 서로 다른 옷의 조합의 수를 return 하도록 solution 함수를 작성해주세요.

##### 제한사항

- clothes의 각 행은 [의상의 이름, 의상의 종류]로 이루어져 있습니다.
- 스파이가 가진 의상의 수는 1개 이상 30개 이하입니다.
- 같은 이름을 가진 의상은 존재하지 않습니다.
- clothes의 모든 원소는 문자열로 이루어져 있습니다.
- 모든 문자열의 길이는 1 이상 20 이하인 자연수이고 알파벳 소문자 또는 '_' 로만 이루어져 있습니다.
- 스파이는 하루에 최소 한 개의 의상은 입습니다.

##### 입출력 예

| clothes                                                      | return |
| ------------------------------------------------------------ | ------ |
| [["yellowhat", "headgear"], ["bluesunglasses", "eyewear"], ["green_turban", "headgear"]] | 5      |
| [["crowmask", "face"], ["bluesunglasses", "face"], ["smoky_makeup", "face"]] | 3      |

##### 입출력 예 설명

예제 #1
headgear에 해당하는 의상이 yellow_hat, green_turban이고 eyewear에 해당하는 의상이 blue_sunglasses이므로 아래와 같이 5개의 조합이 가능합니다.

```
1. yellow_hat
2. blue_sunglasses
3. green_turban
4. yellow_hat + blue_sunglasses
5. green_turban + blue_sunglasses
```

예제 #2
face에 해당하는 의상이 crow_mask, blue_sunglasses, smoky_makeup이므로 아래와 같이 3개의 조합이 가능합니다.

```
1. crow_mask
2. blue_sunglasses
3. smoky_makeup
```



### 풀이

```java
import java.util.HashMap;
import java.util.Iterator;
class Solution {
    public int solution(String[][] clothes) {
        int answer = 1; 
        
        // 1. Create Hash Map 
        HashMap<String, Integer> hm = new HashMap<>(); 
        
        // 2. Make count table of each clothing type 
        for(int i = 0; i < clothes.length; i++) { 
            String key = clothes[i][1]; hm.put(key, hm.getOrDefault(key, 0) + 1 ); 
        } 
        
        // 3. Iterate through all types of clothes and calculate combination 
        Iterator<Integer> it = hm.values().iterator(); 
        while(it.hasNext()) { 
            answer *= it.next().intValue()+1; 
        } 
        
        // 4. decrease 1 for no clothes case 
        return answer-1; }
}
```



### 1. Iterator

> import java.util.Iterator;

Iterator는 이런 집합체로부터 정보를 얻어낸다고 볼 수 있다. 집합체를 다룰 때는 개별적인 클래스에 대해 데이터를 읽는 방법을 알아야 하기 때문에 각 컬렉션에 접근이 힘들어진다. Iterator를 쓰게 되면 어떤 컬랙션이라도 동일한 방식으로 접근이 가능하여 그 안에 있는 항목들에 접근할 수 있는 방법을 제공한다.(다형성)

Iterator 메소드에는 hasNext(), next(), remove()가 있다.

각각의 기능은 다음과 같다.

hasNext() : 읽어올 요소가 남아있는지 확인하는 메소드이다. 요소가 있으면 true, 없으면 false

next() : 다음 데이터를 반환한다.

remove() : next()로 읽어온 요소를 삭제한다.

메소드 호출 순서는 hasNext() -> next() -> remove()이다.



```java
ArrayList list = new ArrayList(); 
list.add("일"); 
list.add("월"); 
list.add("수"); 
Iterator iter = list.iterator(); 
while (iter.hasNext()) { 
	String day = (String) iter.next(); 
	if (day == "수") { 
		iter.remove(); 
	}
}

```



---



# 베스트 앨범

###### 문제 설명

스트리밍 사이트에서 장르 별로 가장 많이 재생된 노래를 두 개씩 모아 베스트 앨범을 출시하려 합니다. 노래는 고유 번호로 구분하며, 노래를 수록하는 기준은 다음과 같습니다.

1. 속한 노래가 많이 재생된 장르를 먼저 수록합니다.
2. 장르 내에서 많이 재생된 노래를 먼저 수록합니다.
3. 장르 내에서 재생 횟수가 같은 노래 중에서는 고유 번호가 낮은 노래를 먼저 수록합니다.

노래의 장르를 나타내는 문자열 배열 genres와 노래별 재생 횟수를 나타내는 정수 배열 plays가 주어질 때, 베스트 앨범에 들어갈 노래의 고유 번호를 순서대로 return 하도록 solution 함수를 완성하세요.

##### 제한사항

- genres[i]는 고유번호가 i인 노래의 장르입니다.
- plays[i]는 고유번호가 i인 노래가 재생된 횟수입니다.
- genres와 plays의 길이는 같으며, 이는 1 이상 10,000 이하입니다.
- 장르 종류는 100개 미만입니다.
- 장르에 속한 곡이 하나라면, 하나의 곡만 선택합니다.
- 모든 장르는 재생된 횟수가 다릅니다.

##### 입출력 예

| genres                                          | plays                      | return       |
| ----------------------------------------------- | -------------------------- | ------------ |
| ["classic", "pop", "classic", "classic", "pop"] | [500, 600, 150, 800, 2500] | [4, 1, 3, 0] |

##### 입출력 예 설명

classic 장르는 1,450회 재생되었으며, classic 노래는 다음과 같습니다.

- 고유 번호 3: 800회 재생
- 고유 번호 0: 500회 재생
- 고유 번호 2: 150회 재생

pop 장르는 3,100회 재생되었으며, pop 노래는 다음과 같습니다.

- 고유 번호 4: 2,500회 재생
- 고유 번호 1: 600회 재생

따라서 pop 장르의 [4, 1]번 노래를 먼저, classic 장르의 [3, 0]번 노래를 그다음에 수록합니다.





### 풀이

```java
import java.util.*;
class Solution {
    public int[] solution(String[] genres, int[] plays) {
        HashMap<String, Integer> map = new HashMap<>();
        for(int i = 0; i < genres.length; i++) {
            map.put(genres[i], map.getOrDefault(genres[i], 0) + plays[i]);
        }
        
        //key값만 가져와서 genre에 넣어준다
        ArrayList<String> genre = new ArrayList<>();
        for(String key : map.keySet()) {
            genre.add(key);
        }
        Collections.sort(genre, (o1, o2) -> map.get(o2) - map.get(o1)); //key값에 해당하는 value를 내림차순으로 정렬한다.
        
        ArrayList<Integer> al = new ArrayList<>();
        for(int i = 0; i < genre.size(); i++) {
            String g = genre.get(i);
            
            int max = 0;
            int firstIdx = -1;
            for(int j = 0 ; j < genres.length ; j++) {
                if(g.equals(genres[j]) && max < plays[j]) {
                    max = plays[j];
                    firstIdx = j;
                }
            }
            
            max = 0;
            int secondIdx = -1;
            for(int j = 0 ; j <genres.length ; j++) {
                if(g.equals(genres[j]) && max < plays[j] && j != firstIdx) {
                    max = plays[j];
                    secondIdx = j;
                }
            }
            al.add(firstIdx);
            if(secondIdx >= 0) { 
                al.add(secondIdx);
            }
        }
        int[] answer = new int[al.size()];
        for(int i = 0; i < al.size(); i++) {
            answer[i] = al.get(i);
        }
        return answer;
    }
}
```

문제는 다음과 같은 과정으로 풀어 나갔다.

1. hashmap에 장르별 play횟수를 중첩해서 더해준다.
2. hashmap의 key값만을 추출하여 리스트를 만들고, 리스트를 play횟수를 기준으로 정렬한다. (hashmap은 순서가 없기 때문에 정렬할 수 없으므로 리스트를 만들어 정렬해 주어야 한다.)
3. key값을 정렬한 리스트에서 제일 많은 횟수를 재생한 장르부터 장르별 제일 많은 횟수가 플레이된 인덱스, 두번째로 많은 횟수가 플레이된 인덱스를 찾아 정답 배열에 순서대로 넣어준다.
4. 이때 두번째로 많은 횟수가 플레이된 인덱스는 존재하지 않을 수도 있기 때문에 이를 잘 처리해준다.
5. 정답 리스트를 배열로 변환하여 반환한다.



### 1. Collections.sort()

***Collections.sort(list);***

ArrayList를 오름차순으로 정렬합니다.

 

***Collections.sort(list, Collections.reverseOrder());***

Collections.sort()의 2번째 파라미터로

내림차순 정렬을 나타내는 Comparator를 전달해서,

ArrayList를 내림차순으로 정렬하였습니다.

 

***Collections.sort(list, String.CASE_INSENSITIVE_ORDER);***

String.CASE_INSENSITIVE_ORDER 를 전달하면, 대소문자 구분없이 오름차순으로 정렬됩니다.

여기서 'a'와 'A'는 같은 순위로 취급되므로, 원래의 순서를 유지합니다.

 

***Collections.sort(list, Collections.reverseOrder(String.CASE_INSENSITIVE_ORDER));***

대소문자 구분없이, 내림차순으로 정렬합니다.



출처: https://hianna.tistory.com/569 [어제 오늘 내일]
