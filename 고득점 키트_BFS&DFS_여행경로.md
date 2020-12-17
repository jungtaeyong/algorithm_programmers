# 고득점 키트 > BFS&DFS > 여행경로



## 풀이

인천국제공항인 ICN부터 출발해서 모든 항공권을 사용하는 문제. 모든 경우의 수를 돌아보며 모든 항공권을 사용할  수 있는지 체크하고, 모든 항공권을 사용 했을 경우, 사전순으로 빠른 경로로 갱신한다. 모든 경우의 수를 돌아보기 위해 DFS를 이용한다.



## 코드

```java
class Solution {
    public String[] solution(String[][] tickets) {
        String[] answer = new String[tickets.length+1];
        String[] res = new String[tickets.length+1];
        res[0] = "ICN";
        boolean[] v = new boolean[tickets.length];
        dfs(1, res, answer, tickets, "ICN", v);
        return answer;
    }
    
    void dfs(int depth, String[] res, String[] ans, String[][] tickets, String cur, boolean[] v){
        if(depth == tickets.length+1){
            if(ans[0]==null){
                for(int i=0;i<depth;i++){
                    ans[i]=res[i];
                }
            }else{
                for(int i=0;i<tickets.length+1;i++){
                    if(res[i].compareTo(ans[i])>=1){
                        break;
                    }else if(res[i].compareTo(ans[i])<=-1){
                        for(int j=0;j<depth;j++){
                            ans[j]=res[j];
                        }
                        break;
                    }
                }
            }
            return;
        }
        for(int i=0;i<tickets.length;i++){
            if(cur.equals(tickets[i][0]) && !v[i]){
                v[i]=true;
                res[depth]=tickets[i][1];
                dfs(depth+1, res, ans, tickets, tickets[i][1], v);
                v[i]=false;
            } 
        }
    }
}
```

