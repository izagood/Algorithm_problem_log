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
    public boolean hasPathSum(TreeNode root, int targetSum) {
        return dfs(root, 0, targetSum);
        
    }
    
    private boolean dfs(TreeNode root, int preSum, int targetSum){
        
        if(root == null){
            return false;
        }else{
            int nowSum = preSum + root.val;
            if(root.left == null && root.right == null && nowSum == targetSum){
                return true;
            }else{
                return dfs(root.left, nowSum, targetSum) || dfs(root.right, nowSum, targetSum);
            }
        }
    }
}
```