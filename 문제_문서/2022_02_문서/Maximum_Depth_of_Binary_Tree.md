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
    private int max = 0;
    public int maxDepth(TreeNode root) {
        dfs(root, 0);
        return max;
    }
    
    private void dfs(TreeNode node, int depth){
        if(node == null){
            max = Math.max(max, depth);
            return;
        }
        
        dfs(node.left, depth + 1);
        dfs(node.right, depth + 1);
    }
}
```

###   분석
-   모든 depth를 확인하고 그중에서 가장 큰(max)를 리턴하면 된다.

###   참고할 만한 정답
```java
class Solution {
    public int maxDepth(TreeNode root) {
        if (root == null) return 0;
            
        int leftDepth = maxDepth(root.left);
        int rightDepth = maxDepth(root.right);
        return Math.max(leftDepth, rightDepth) + 1;
    }
}
```

###   비교 분석
-   위 처럼 풀면 굳이 Math.max()로 일일히 큰 값을 판단할 필요가 없다.