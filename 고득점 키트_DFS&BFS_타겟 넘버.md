# 고득점 키트 > DFS&BFS > 타겟 넘버



## 풀이

DFS를 이용해 모든 경우를 탐색한다. 더하는 경우와 빼는 경우 2가지 경우가 있기 때문에 재귀적으로 2가지 경우를 탐색한다.



## 코드

```java
class Solution {
    int answer= 0;
    public int solution(int[] numbers, int target) {
        dfs(numbers, 0, target);
        return answer;
    }
    
    public void dfs(int[] arr, int depth, int target){
        if(depth==arr.length){
            int num = 0;
            for(int i=0;i<arr.length;i++){
                num+=arr[i];
            }
            if(num==target) answer++;
            return;
        }
        dfs(arr, depth+1, target);
        arr[depth]*=-1;
        dfs(arr, depth+1, target);
    }
}
```

