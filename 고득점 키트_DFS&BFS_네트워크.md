# 고득점 키트 > DFS&BFS > 네트워크



## 풀이

유니온 파인드 알고리즘을 이용해 노드를 연결하고, HashSet을 이용해 네트워크 수를 구한다. HashSet을 사용하므로써, 중복을 없애 네트워크 수를 구할 수 있다.



## 코드

```java
import java.util.*;

class Solution {
    public int solution(int n, int[][] computers) {
        int answer = 0;
        HashSet<Integer> s = new HashSet<>();
        int[] parent = new int[n];
        for(int i = 0 ;i<n;i++){
            parent[i]= i;
        }
        
        for(int i=0;i<n;i++){
            for(int j=0;j<n;j++){
                if(i==j) continue;
                if(computers[i][j]==1){
                    union(i,j,parent);
                }
            }
        }
        for(int i=0;i<n;i++) s.add(getparent(i, parent));
        return s.size();
    }
    
    int getparent(int x, int[] parent){
        if(x==parent[x]) return x;
        return getparent(parent[x], parent);
    }
    void union(int x, int y, int[] parent){
        x = getparent(x, parent);
        y = getparent(y, parent);
        if(x<y) {
            parent[y]=x;
            
        }else {
            parent[x]=y;
            
        }        
    }
    boolean iscon(int x, int y, int[] parent){
        return getparent(x, parent)==getparent(y,parent);
    }
}
```

