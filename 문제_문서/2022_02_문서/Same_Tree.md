###   정답(Solution)
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
import java.util.*;
class Solution {
    
    public boolean isSameTree(TreeNode p, TreeNode q) {
        List<Integer> iL1 = new ArrayList<>();
        List<Integer> iL2 = new ArrayList<>();
        dfs(p, iL1);
        dfs(q, iL2);
        
        for(int i=0; i<iL1.size(); i++){
            if(iL1.get(i) == null && iL2.get(i) == null){
                continue;
            }
            
            if(iL1.get(i) == null || iL2.get(i) == null){
                return false;
            }
            
            if(!iL1.get(i).equals(iL2.get(i))){
                return false;
            }
        }
        return true;
    }
    
    private void dfs(TreeNode node, List<Integer> iList){
        if(node == null){
            iList.add(null);
            return;
        }
        
        iList.add(node.val);
        dfs(node.left, iList);
        dfs(node.right, iList);
        
    }
}
```

###   분석
-   트리를 이용하는 dfs 문제

###   참고할 만한 정답
```java
class Solution {
    
    public boolean isSameTree(TreeNode p, TreeNode q) {
                
        if(p == null && q == null){
            return true;
        }
        
        if(p == null || q == null){
            return false;
        }
        
        if(p.val != q.val){
            return false;
        }
        
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }
}
```

###   비교 분석
-   isSameTree를 재귀의 기본으로 사용하면 좀 더 빠르고 굳이 ArraysList를 사용하지 않아도 풀 수 있다.