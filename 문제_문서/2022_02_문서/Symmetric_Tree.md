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
class Solution {
    public boolean isSymmetric(TreeNode root) {
                
        return dfs(root.left, root.right);
    }
    
    private boolean dfs(TreeNode l, TreeNode r){
        
        if(l == null && r == null){
            return true;
        }
        
        if(l == null || r == null){
            return false;
        }
        
        if(l.val != r.val){
            return false;
        }
        
        return dfs(l.left, r.right) && dfs(l.right, r.left);
    }
}
```

###   분석
-   dfs 문제
-   처음 root에서 좌우로 node를 분할하고 분할한 노드들을 비교하는 dfs를 재귀실행 시키면 된다.
-   solution 중 가장 빠른 답을 보았는데 내 풀이랑 비슷했다.
-   정석 dfs 스타일로 다듬어 지는것 같다.