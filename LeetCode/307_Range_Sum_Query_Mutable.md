# 307. Range Sum Query - Mutable
Range Sum Query - Mutable

## Code
    //Time Limit Exceeded
    public class NumArray {
        int[] myNums;
        int[] sumNums;
        int len = 0;
        
        public NumArray(int[] nums) {
            len = nums.Length;
            if(len == 0) 
                return;
            myNums = nums;
            sumNums = new int[len];
            sumNums[0] = nums[0];
            for(int i = 1; i < len; i ++) {
                sumNums[i] = sumNums[i - 1] + nums[i];
            }
        }
        
        public void Update(int i, int val) {
            int diff = val -  myNums[i];
            for(int j = i; j < len; j ++){
                sumNums[j] += diff;
            }
            myNums[i] = val;
        }
        
        public int SumRange(int i, int j) {
            if(i == 0) 
                return sumNums[j];
            return sumNums[j] - sumNums[i - 1];
        }
    }

    /**
    * Your NumArray object will be instantiated and called as such:
    * NumArray obj = new NumArray(nums);
    * obj.Update(i,val);
    * int param_2 = obj.SumRange(i,j);
    */

    //Segment Tree
    public class SegmentTreeNode {
        public int start, end;
        public SegmentTreeNode left, right;
        public int sum;

        public SegmentTreeNode(int start, int end) {
            this.start = start;
            this.end = end;
            this.left = null;
            this.right = null;
            this.sum = 0;
        }
    }

    public class NumArray {


        SegmentTreeNode root = null;
        
        public NumArray(int[] nums) {
            root = BuildTree(nums, 0, nums.Length - 1);
        }
        
        public SegmentTreeNode BuildTree(int[] nums, int start, int end) {
            if (start > end) {
                return null;
            } else {
                SegmentTreeNode ret = new SegmentTreeNode(start, end);
                if (start == end) {
                    ret.sum = nums[start];
                } else {
                    int mid = start  + (end - start) / 2;             
                    ret.left = BuildTree(nums, start, mid);
                    ret.right = BuildTree(nums, mid + 1, end);
                    ret.sum = ret.left.sum + ret.right.sum;
                }         
                return ret;
            }
        }
        
        public void Update(int i, int val) {
            UpdateTree(root, i, val);
        }
        
        
        public void UpdateTree(SegmentTreeNode root, int pos, int val) {
            if (root.start == root.end) {
            root.sum = val;
            } else {
                int mid = root.start + (root.end - root.start) / 2;
                if (pos <= mid) {
                    UpdateTree(root.left, pos, val);
                } else {
                    UpdateTree(root.right, pos, val);
                }
                root.sum = root.left.sum + root.right.sum;
            }
        }
        
        public int SumRange(int i, int j) {
            return GetSum(root, i, j);
        }
        
        public int GetSum(SegmentTreeNode root, int start, int end) {
            if (root.end == end && root.start == start) {
                return root.sum;
            } else {
                int mid = root.start + (root.end - root.start) / 2;
                if (end <= mid) {
                    return GetSum(root.left, start, end);
                } else if (start >= mid+1) {
                    return GetSum(root.right, start, end);
                }  else {    
                    return GetSum(root.right, mid+1, end) + GetSum(root.left, start, mid);
                }
            }
        }
    }

    /**
    * Your NumArray object will be instantiated and called as such:
    * NumArray obj = new NumArray(nums);
    * obj.Update(i,val);
    * int param_2 = obj.SumRange(i,j);
    */