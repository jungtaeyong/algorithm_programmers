# Summer&Winter Coding > 2018 > 스킬트리



## 풀이

배워야하는 스킬을 배열에 차례대로 저장한다. 인덱스를 처음부터 비교해가며 해당 스킬을 배울 수 있다면 현재 인덱스를 갱신하고, 배울수 없다면 빠져나가 flag로 체크한다.



## 코드

```java
class Solution {
    public int solution(String skill, String[] skill_trees) {
        int answer = 0;
        int[] arr = new int[26];
        for(int i=0;i<skill.length();i++){
            arr[skill.charAt(i)-'A']=i+1;
        }
        for(int i=0 ;i<skill_trees.length;i++){
            int cur=1;
            boolean flag=true;
            for(int j=0;j<skill_trees[i].length();j++){
                int idx = arr[skill_trees[i].charAt(j)-'A'];
                if(idx>0){
                   if(idx<=cur){
                       cur=Math.max(cur, idx+1);
                   }else{
                       flag=false;
                       break;
                   }
                }
            }
            if(flag) answer++;
        }
        return answer;
    }
}
```

