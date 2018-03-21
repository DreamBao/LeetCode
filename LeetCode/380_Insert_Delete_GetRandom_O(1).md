# 380. Insert Delete GetRandom O(1)
Insert Delete GetRandom O(1)

## Code
    public class RandomizedSet {
        public List<int> list;
        Random ran = new Random();
        /** Initialize your data structure here. */
        public RandomizedSet() {
            list = new List<int>();
            ran = new Random();
        }
        
        /** Inserts a value to the set. Returns true if the set did not already contain the specified element. */
        public bool Insert(int val) {
            if(!list.Contains(val)) {
                list.Add(val);
                return true;
            }
            return false;

        }
        
        /** Removes a value from the set. Returns true if the set contained the specified element. */
        public bool Remove(int val) {
            if(list.Contains(val)) {
                return list.Remove(val);
            }       
            return false;
        }
        
        /** Get a random element from the set. */
        public int GetRandom() {
            
            return list[ran.Next(0, list.Count)];
        }
    }

    /**
    * Your RandomizedSet object will be instantiated and called as such:
    * RandomizedSet obj = new RandomizedSet();
    * bool param_1 = obj.Insert(val);
    * bool param_2 = obj.Remove(val);
    * int param_3 = obj.GetRandom();
    */