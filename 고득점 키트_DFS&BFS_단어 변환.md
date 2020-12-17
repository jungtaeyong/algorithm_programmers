# 고득점 키트 > DFS&BFS > 단어 변환



## 풀이

현재 단어에서 words의 단어로 한 번에 한 개의 알파벳만 바꾸면서 target단어로 바꿀 때 최소 변경수를 리턴하는 문제. 이 문제 역시 모든 경우를 탐색해야 한다. 단, 이미 탐색한 경우는 다시 탐색할 필요가 없으므로, 방문한 배열을 체크하기위해 배열 v를 선언해 저장했다.



## 코드

```java
class Solution {
    int answer = 10000000;
    public int solution(String begin, String target, String[] words) {
        boolean[] v = new boolean[words.length];
        dfs(begin, target, words, v, 0);
        if(answer == 10000000) return 0;
        else return answer;
    }
    void dfs(String begin, String target, String[] words, boolean[] v, int sum){
        if(begin.equals(target)){
            answer = Math.min(answer, sum);
            return;
        }
        for(int i=0;i<words.length;i++){
            if(v[i]) continue;
            int cnt=0;
            for(int j=0;j<words[i].length();j++){
                if(begin.charAt(j)!=words[i].charAt(j)) cnt++;
            }
            if(cnt==1){
                v[i]=true;
                dfs(words[i], target, words, v, sum+1);
                v[i]=false;
            }
        }
    }
}
```

