# 고득점 키트 > 동적계획법 > N으로 표현



## 풀이

다이나믹 프로그래밍으로 분류된 문제지만 dfs를 이용하여 풀었다. 조건 중 **최솟값이 8보다 크면 -1을 return 한다** 가 있다. 따라서 모든 경우의 수를 탐색하더라도 깊이가 8을 넘지 않기 때문에, 시간초과가 나는 경우는 없다.



## 코드

```java
class Solution {
    int answer;
    public int solution(int N, int number) {
        answer = 9;
        dfs(0, 0, N, number);
        return answer > 8 ? -1 : answer;
    }
    
    private void dfs(int cnt, int number, int N, int target) {
        if(cnt >8) {
            return;
        }
        if(number == target) {
            answer = Math.min(answer, cnt);
            return;
        }
        
        for(int i=1; i<=8-cnt; i++) {   // digit
            dfs(cnt+i, number+getNum(i,N), N, target);
            dfs(cnt+i, number-getNum(i,N), N, target);
            dfs(cnt+i, number/getNum(i,N), N, target);
            dfs(cnt+i, number*getNum(i,N), N, target);
        }
    }
    private int getNum(int digit, int N) {
        int result =0;
        for(int i=0; i<digit; i++) {
            result += Math.pow(10,i)*N;
        }
        return result;
    }
}
```

