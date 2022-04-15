###   정답(Solution)
```java
class Solution {
    public TreeNode trimBST(TreeNode root, int low, int high) {
        if (root == null) return root;
        if (root.val > high) return trimBST(root.left, low, high);
        if (root.val < low) return trimBST(root.right, low, high);

        root.left = trimBST(root.left, low, high);
        root.right = trimBST(root.right, low, high);
        return root;       
    }
}
```

###   분석
-   이진 탐색 트리에서 high와 low 사이 범위의 상대적 구조를 유지하며 범위 밖의 node를 제거