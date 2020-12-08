# 고득점 키트 > 정렬 > H-Index



# 풀이

논문 n 편 중, h번 이상 인용 된 논문이 h편이 이상이고 나머지 논문이 h번 이하로 인용된 h의 최대값을 찾는 문제. 정렬을 이용해 간단히 풀 수 있다. 오름차순 정렬한 뒤,  `citations[i], citations.length-i`값 중 최소값을 answer에 갱신해준다. i번째 이후로도  `citations[i]`값 만큼 배열이 존재하면 `citations[i]`값이 H-index가 되지만 아닐 경우는 `citations.length-i`만큼이 최대 H-index이기 때문이다.



## 코드

```java
import java.util.*;
class Solution {
    public int solution(int[] citations) {
        int answer = 0;
        Arrays.sort(citations);
        for(int i=0;i<citations.length;i++){
            int min=0;
            min=Math.min(citations[i], citations.length-i);
            answer=Math.max(answer, min);
        }
        return answer;
    }
}
```

