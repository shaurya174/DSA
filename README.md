# 💻 DSA Problem Tracker

Welcome to my **DSA Solutions Repository**!  
Here, I store all the problems I’ve solved along with my solutions. Organized day-wise and by problem.

---

## 📅 Day 1

### 1️. **Reverse String**  
**Difficulty:** Easy  
**Concept/Approach:** Two Pointers 


**Solution:**
```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {
        int st = 0,end = s.size()-1;
        while(st<end){
            swap(s[st++],s[end--]);
        }
    }
};
```
### 2. **Valid Palindrome**  
**Difficulty:** Easy  
**Concept/Approach:** Two Pointers 


**Solution:**
```cpp
class Solution {
public:
    bool isPalindrome(string s) {
        int st = 0;
        int end = s.size()-1;
        while(st<end){
            if(!isalnum(s[st])){
                st++;
            }
            else if(!isalnum(s[end])){
                end--;
            }
            else{
                if(tolower(s[st])==tolower(s[end])){
                    st++;
                    end--;
                }
                else{
                    return false;
                }
            }
        }
        return true;
    }
};
```
### 3. **Remove All Occurences**  
**Difficulty:** Medium  
**Concept/Approach:** String


**Solution:**
```cpp
class Solution {
public:
    string removeOccurrences(string s, string part) {
        while(true){
            if(s.find(part)>=s.size()){
                break;
            }
            else{
                int pos = s.find(part);
                s.erase(pos,part.size());
            }
        }
        return s;
    }
};
```
### 4. **Permutation In String**  
**Difficulty:** Medium  
**Concept/Approach:** Sliding Window


**Solution:**
```cpp
class Solution {
public:
    bool checkInclusion(string s1, string s2) {
        if(s1.size()>s2.size()){
            return false;
        }
        vector<int>vec1(26,0);
        vector<int>vec2(26,0);
        for(int i = 0;i<s1.size();i++){
            vec1[s1[i]-'a']++;
            vec2[s2[i]-'a']++;
        }
        if(vec1==vec2){
            return true;
        }
        for(int i = s1.size();i<s2.size();i++){
            vec2[s2[i-s1.size()]-'a']--;
            vec2[s2[i]-'a']++;
            if(vec1==vec2){
                return true;
            }
        }
        return false;
    }
};
```
### 5. **Reverse Words**  
**Difficulty:** Medium  
**Concept/Approach:** String


**Solution:**
```cpp
class Solution {
public:
    string reverseWords(string s) {
        string ans = "";
        string curr = "";
        for(int i = s.size()-1;i>=0;i--){
            if(s[i]==' '){
                if(curr.size()>0){
                    reverse(curr.begin(),curr.end());
                    ans += curr;
                    curr = "";
                    ans +=" ";
                }
            }
            else{
                curr+=s[i];
            }
        }
        if(curr.size()>0){
            reverse(curr.begin(),curr.end());
            ans+=curr;
        }
        if(ans[ans.size()-1]==' '){
            ans.erase(ans.size()-1,1);
        }
        return ans;
    }
};
```
### 6. **String Compression**  
**Difficulty:** Medium  
**Concept/Approach:** Two Pointer


**Solution:**
```cpp
class Solution {
public:
    int compress(vector<char>& chars) {
        int j = 0;
        if(chars.size()==1){
            return 1;
        }
        int ans = 0;
        int curr = 1;
        char wor = chars[0];
        for(int i = 1;i<chars.size();i++){
            if(wor==chars[i]){
                curr++;
            }
            else{
                if(curr==1){
                    chars[j]=wor;
                    j++;
                    wor = chars[i];
                    ans++;
                }
                else{
                    chars[j]=wor;
                    j++;
                    string cc = to_string(curr);
                    for(int k = 0;k<cc.size();k++){
                        chars[j]=cc[k];
                        j++;
                    }
                    ans+=(cc.size()+1);
                    wor = chars[i];
                    curr = 1;
                }
            }
        }
        if(curr==1){
            chars[j]=wor;
            ans++;
        }
        else{
            chars[j]=wor;
            j++;
            string cc = to_string(curr);
            for(int k = 0;k<cc.size();k++){
                chars[j]=cc[k];
                j++;
            }
            ans+=1;
            ans+=cc.size();
        }
        return ans;
    }
};
```
## 📅 Day 2

### 7. **Binary Search**  
**Difficulty:** Easy  
**Concept/Approach:** Binary Search 


**Solution:**
```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int st=0,end = nums.size()-1;
        while(st<=end){
            int mid = st+(end-st)/2;
            if(nums[mid]==target){
                return mid;
            }
            else if(nums[mid]<target){
                st = mid+1;
            }
            else{
                end = mid-1;
            }
        }
        return -1;
    }
};
```
### 8. **Single Number**  
**Difficulty:** Easy  
**Concept/Approach:** Bit Manipulation


**Solution:**
```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int ans = 0;
        for(int i = 0;i<nums.size();i++){
            ans = ans ^ nums[i];
        }
        return ans;
    }
};
```
### 9. **Fibonacci Number**  
**Difficulty:** Easy  
**Concept/Approach:** Recursion


**Solution:**
```cpp
class Solution {
public:
    int fib(int n) {
        if(n==0){
            return 0;
        }
        if(n==1){
            return 1;
        }
        return fib(n-1)+fib(n-2);
    }
};
```
### 10. **Two Sum**  
**Difficulty:** Easy  
**Concept/Approach:** Hashing


**Solution:**
```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int>vec;
        for(int i = 0;i<nums.size();i++){
            vec[nums[i]]=i;
        }
        for(int i = 0;i<nums.size();i++){
            int indd = target-nums[i];
                if(vec.find(indd)==vec.end()){
                    continue;
                }
                else{
                    int idx = vec[indd];
                    if(idx==i){
                        continue;
                    }
                    return {i,idx};
                }
        }
        return {0,0};
    }
};
```
### 11. **Find Missing and Repeated Values**  
**Difficulty:** Easy  
**Concept/Approach:** Maths


**Solution:**
```cpp
class Solution {
public:
    vector<int> findMissingAndRepeatedValues(vector<vector<int>>& grid) {
        long long n = grid.size() * grid.size();
        long long gridsum = 0, gridsqsum = 0;
        
        for(int i = 0; i < grid.size(); i++) {
            for(int j = 0; j < grid.size(); j++) {
                gridsum += grid[i][j];
                gridsqsum += 1LL * grid[i][j] * grid[i][j];
            }
        }
        
        long long exsum = n * (n + 1) / 2;
        long long exsqsum = n * (n + 1) * (2 * n + 1) / 6;
        
        long long diff = exsum - gridsum;            // a - b
        long long sqdiff = exsqsum - gridsqsum;      // a^2 - b^2
        
        long long sum_ab = sqdiff / diff;            // a + b
        
        long long a = (diff + sum_ab) / 2;           // missing
        long long b = a - diff;                      // repeated
        
        return {(int)b, (int)a};
    }
};
```
### 12. **Find Duplicate**  
**Difficulty:** Medium  
**Concept/Approach:** Hashing


**Solution:**
```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        unordered_set<int>s;
        for(int i = 0;i<nums.size();i++){
            if(s.find(nums[i])!=s.end()){
                return nums[i];
            }
            s.insert(nums[i]);
        }
        return nums[0];
    }
};
```
### 13. **First Unique Character in String**  
**Difficulty:** Easy
**Concept/Approach:** Counting


**Solution:**
```cpp
class Solution {
public:
    int firstUniqChar(string s) {
        vector<int>vec(26,0);
        for(int i = 0;i<s.size();i++){
            vec[s[i]-'a']++;
        }
        for(int i = 0;i<s.size();i++){
            if(vec[s[i]-'a']==1){
                return i;
            }
        }
        return -1;
    }
};
```
## 📅 Day 3

### 14. **Valid Parenthesis**  
**Difficulty:** Easy
**Concept/Approach:** Stack


**Solution:**
```cpp
class Solution {
public:
    bool isValid(string s) {
        stack<char>ss;
        for(int i = 0;i<s.size();i++){
            if(ss.empty()){
                ss.push(s[i]);
            }
            else if(s[i]=='('){
                ss.push(s[i]);
            }
            else if(s[i]=='{'){
                ss.push(s[i]);
            }
            else if(s[i]=='['){
                ss.push(s[i]);
            }
            else{
                if(s[i]==']'){
                    if(ss.top()=='['){
                        ss.pop();
                    }
                    else{
                        ss.push(s[i]);
                    }
                }
                else if(s[i]==')'){
                    if(ss.top()=='('){
                        ss.pop();
                    }
                    else{
                        ss.push(s[i]);
                    }
                }
                else{
                    if(ss.top()=='{'){
                        ss.pop();
                    }
                    else{
                        ss.push(s[i]);
                    }
                }
            }
        }
        if(ss.empty()){
            return true;
        }
        return false;
    }
};
```
### 15. **Implement Stack Using Queue**  
**Difficulty:** Easy
**Concept/Approach:** Queues

**Solution:**
```cpp
class MyStack {
public:
    queue<int>q;
    MyStack() {
        
    }
    
    void push(int x) {
        q.push(x);
    }
    
    int pop() {
        queue<int>q2;
        while(true){
            if(q.size()==1){
                int tt = q.front();
                q = q2;
                return tt;
            }
            int cc = q.front();
            q2.push(cc);
            q.pop();
        }
    }
    
    int top() {
        return q.back();
    }
    
    bool empty() {
        return q.empty();
    }
};
```
### 16. **Implement Queue Using Stack**  
**Difficulty:** Easy
**Concept/Approach:** Stack

**Solution:**
```cpp
class MyQueue {
public:
    stack<int>s;
    MyQueue() {
        
    }
    
    void push(int x) {
        if(s.empty()){
            s.push(x);
        }
        else{
            stack<int>s2;
            while(!s.empty()){
                s2.push(s.top());
                s.pop();
            }
            s.push(x);
            while(!s2.empty()){
                s.push(s2.top());
                s2.pop();
            }
        }
    }
    
    int pop() {
        int x = s.top();
        s.pop();
        return x;
    }
    
    int peek() {
        return s.top();
    }
    
    bool empty() {
        return s.empty();
    }
};
```
### 17. **Preorder Traversal**  
**Difficulty:** Easy
**Concept/Approach:** Recursion

**Solution:**
```cpp
class Solution {
public:
    vector<int>ans;
    void pree(TreeNode* root){
        if(root==nullptr){
            return;
        }
        ans.push_back(root->val);
        pree(root->left);
        pree(root->right);
    }
    vector<int> preorderTraversal(TreeNode* root) {
        pree(root);
        return ans;
    }
};
```
### 18. **Inorder Traversal**  
**Difficulty:** Easy
**Concept/Approach:** Recursion

**Solution:**
```cpp
class Solution {
public:
    vector<int>ans;
    void inn(TreeNode* root){
        if(root==nullptr){
            return;
        }
        
        inn(root->left);
        ans.push_back(root->val);
        inn(root->right);
    }
    vector<int> inorderTraversal(TreeNode* root) {
        inn(root);
        return ans;
    }
};
```
### 19. **Postorder Traversal**  
**Difficulty:** Easy
**Concept/Approach:** Recursion

**Solution:**
```cpp
class Solution {
public:
    vector<int>ans;
    void poos(TreeNode* root){
        if(root==nullptr){
            return;
        }
        
        poos(root->left);
        
        poos(root->right);
        ans.push_back(root->val);
    }
    
    vector<int> postorderTraversal(TreeNode* root) {
        poos(root);
        return ans;
    }
};
```
### 20. **Level Order Traversal**  
**Difficulty:** Medium
**Concept/Approach:** Queue,BFS

**Solution:**
```cpp
class Solution {
public:
    
    vector<vector<int>> levelOrder(TreeNode* root) {
    vector<vector<int>> ans;
    if(!root) return ans;

    queue<TreeNode*> q;
    q.push(root);
    q.push(nullptr);  // marker for level end

    vector<int> curr;

    while(!q.empty()) {
        TreeNode* node = q.front();
        q.pop();

        if(node == nullptr) { // end of current level
            ans.push_back(curr);
            curr.clear();
            if(!q.empty()) q.push(nullptr);
        } else {
            curr.push_back(node->val);
            if(node->left) q.push(node->left);
            if(node->right) q.push(node->right);
        }
    }

    return ans;
}

};
```
### 21. **3 Sum**  
**Difficulty:** Medium
**Concept/Approach:** Hashing

**Solution:**
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        vector<vector<int>>ans;
        for(int i = 0;i<nums.size();i++){
            if(i > 0 && nums[i] == nums[i-1]) continue;
            int target = 0-nums[i];
            int start = i+1;
            int end = nums.size()-1;
            while(start<end){
                if(nums[start]+nums[end]<target){
                    start++;
                }
                else if(nums[start]+nums[end]>target){
                    end--;
                }
                else{
                    vector<int>cans={nums[i],nums[start],nums[end]};
                    ans.push_back(cans);
                    start++;
                    end--;
                    while(start < end && nums[start] == nums[start-1]) start++;
                    // skip duplicates for end
                    while(start < end && nums[end] == nums[end+1]) end--;     
                }
            }
        }
        return ans;
             
    }
};
```

## 📅 Day 4

### 22. **Middle Of Linked List**  
**Difficulty:** Easy
**Concept/Approach:** “Tortoise and Hare” (Slow and Fast Pointer)

**Solution:**
```cpp
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode* tem = head;
        ListNode* cem = head;
        if(head->next==nullptr){
            return head;
        }
        while(true){
            cem = cem->next->next;
            tem=tem->next;
            if((cem==nullptr)||(cem->next==nullptr)){
                break;
            }
        }
        return tem;
    }
};
```

### 23. **Count Primes**  
**Difficulty:** Medium
**Concept/Approach:** Sieve Of Erastrothenes

**Solution:**
```cpp
class Solution {
public:
    int countPrimes(int n) {
        if(n <= 2) return 0; // nothing to do if n < 2

        vector<int> vec(n, 1);
        vec[0] = 0;
        vec[1] = 0;

        for(int i = 2; i < n; i++){
            if(vec[i] == 0) continue;

            for(int j = i*2; j < n; j += i){
                vec[j] = 0;
            }
        }

        int ans = 0;
        for(int i = 2; i < n; i++){
            if(vec[i] == 1) ans++;
        }
        return ans;
    }
};
```

### 24. **Reverse Integer**  
**Difficulty:** Medium
**Concept/Approach:** Math

**Solution:**
```cpp
class Solution {
public:
    int reverse(int x) {
        int revNum = 0;
        while(x!=0){
            int dig = x%10;
            x=x/10;
            if(revNum>INT_MAX/10){
                return 0;
            }
            if(revNum<INT_MIN/10){
                return 0;
            }
            revNum=revNum*10+dig;
        }
        return revNum;
    }
};
```

### 25. **Palindrome Number**  
**Difficulty:** Easy
**Concept/Approach:** Math

**Solution:**
```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0){
            return false;
        }
        int n = x;
        int revNum = 0;
        int cc = 0;
        while(n!=0){
            int dig = n%10;
            n=n/10;
            if(revNum<INT_MIN/10){
                return 0;
            }
            else if(revNum>INT_MAX/10){
                return 0;
            }
            revNum = revNum*10 + dig;
        }
        if(revNum==x){
            return true;
        }
        return false;
    }
};
```

### 26. **Identical Tree**  
**Difficulty:** Easy
**Concept/Approach:** Recursion

**Solution:**
```cpp
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p==nullptr){
            if(q==nullptr){
                return true;
            }
            else{
                return false;
            }
        }
        if(q==nullptr){
            if(p==nullptr){
                return true;
            }
            else{
                return false;
            }
        }
        if(p->val==q->val){
            if(!isSameTree(p->left,q->left)){
                return false;
            }
            if(!isSameTree(p->right,q->right)){
                return false;
            }
        }
        else{
            return false;
        }
        return true;
    }
};
```

## 📅 Day 5

### 27. **Valid Anagram**  
**Difficulty:** Easy
**Concept/Approach:** Counting

**Solution:**
```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
        vector<int>vec(26,0);
        if(s.size()!=t.size()){
            return false;
        }
        for(int i = 0;i<s.size();i++){
            vec[s[i]-'a']++;
            vec[t[i]-'a']--;
        }
        for(int i = 0;i<26;i++){
            if(vec[i]!=0){
                return false;
            }
        }
        return true;
    }
};
```

### 28. **Recursive Binary Search**  
**Difficulty:** Easy
**Concept/Approach:** Recursion

**Solution:**
```cpp
class Solution {
public:
    int binsearch(vector<int>nums,int start,int end,int target){
        if(start>end){
            return -1;
        }
        int mid = start+(end-start)/2;
        if(nums[mid]==target){
            return mid;
        }
        else if(nums[mid]<target){
            return binsearch(nums,mid+1,end,target);
        }
        else{
            return binsearch(nums,start,mid-1,target);
        }
        return -1;

    }
    int search(vector<int>& nums, int target) {
        return binsearch(nums,0,nums.size()-1,target);
    }
};
```

### 29. **Array Intersection 2**  
**Difficulty:** Easy
**Concept/Approach:** Hashmap

**Solution:**
```cpp
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        unordered_map<int,int>m1;
        unordered_map<int,int>m2;
        for(int i = 0;i<nums1.size();i++){
            m1[nums1[i]]++;
        }
        for(int i = 0;i<nums2.size();i++){
            m2[nums2[i]]++;
        }
        vector<int>ans;
        for(auto it:m1){
            if(m2[it.first]>0){
                int freq = min(it.second,m2[it.first]);
                for(int k = 0;k<freq;k++){
                    ans.push_back(it.first);
                }
            }
        }
        return ans;
    }
};
```

### 30. **Power Of Two**  
**Difficulty:** Easy
**Concept/Approach:** Bit Manipulation

**Solution:**
```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if(n<0){
            return false;
        }
        if(n==0){
            return false;
        }
        if((n & (n-1))==0){
            return true;
        }
        return false;
    }
};
```

### 31. **XOR OP IN AN ARRAY**  
**Difficulty:** Easy
**Concept/Approach:** Bit Manipulation

**Solution:**
```cpp
class Solution {
public:
    int xorOperation(int n, int start) {
        int ans = 0;
        for(int i = 0;i<n;i++){
            ans=ans^(start+2*i);
        }
        return ans;
    }
};
```

### 32. **Move Zeroes**  
**Difficulty:** Easy
**Concept/Approach:** Two Pointer

**Solution:**
```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int cc = 0;
        int j = 0;
        for(int i = 0;i<nums.size();i++){
            if(nums[i]!=0){
                cc++;
            }
        }
        for(int i = 0;i<nums.size();i++){
            if(nums[i]!=0){
                nums[j]=nums[i];
                j++;
            }
            

        }
        for(int i = 0;i<nums.size();i++){
            if(i>=cc){
                nums[i]=0;
            }
        }
        

    }
};
```

### 33. **Maximum Depth of Binary Tree**  
**Difficulty:** Easy
**Concept/Approach:** Recursion

**Solution:**
```cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        int ans = 0;
        int ind=0;
        int cnd=0;
        if(root==nullptr){
            return 0;
        }
        ans++;
        ind =maxDepth(root->left);
        cnd = maxDepth(root->right);
        ans+=max(ind,cnd);
        return ans;
    }
};
```

### 34. **Symmetric Tree**  
**Difficulty:** Easy
**Concept/Approach:** Recursion

**Solution:**
```cpp
class Solution {
public:
    bool isMirror(TreeNode* t1, TreeNode* t2) {
        if(t1 == nullptr && t2 == nullptr) return true;
        if(t1 == nullptr || t2 == nullptr) return false;
        if(t1->val != t2->val) return false;
        
        return isMirror(t1->left, t2->right) && isMirror(t1->right, t2->left);
    }
    
    bool isSymmetric(TreeNode* root) {
        if(root == nullptr) return true;
        return isMirror(root->left, root->right);
    }
};

```

### 35. **Delete Node in a Linked List**  
**Difficulty:** Medium
**Concept/Approach:** Linked List

**Solution:**
```cpp
class Solution {
public:
    void deleteNode(ListNode* node) {
        ListNode* temp = node;
        while(temp!=nullptr){
            temp->val=temp->next->val;
            if(temp->next->next==nullptr){
                break;
            }
            temp=temp->next;
        }
        temp->next=nullptr;

    }
};
```

## 📅 Day 6

### 36. **Group Anagrams**  
**Difficulty:** Medium
**Concept/Approach:** Hashmap

**Solution:**
```cpp
vector<vector<string>> groupAnagrams(vector<string>& strs) {
        unordered_map<string,vector<string>>vec;
        for(int i = 0;i<strs.size();i++){
            vector<int>vecc(26,0);
            for(int j = 0;j<strs[i].size();j++){
                vecc[strs[i][j]-'a']++;
            }
            string strr = "";
            for(int j = 0;j<26;j++){
                strr+=vecc[j];
                strr+=",";
            }
            vec[strr].push_back(strs[i]);
        }
        vector<vector<string>>ans;
        for(auto it:vec){
            ans.push_back(it.second);
        }
        return ans;
    }
```

### 37.Find All Anagrams in a String
**Difficulty:** Medium
**Concept/Approach:** Hashmap

**Solution:**
```cpp
vector<int> findAnagrams(string s, string p) {
        if(p.size()>s.size()){
            return {};
        }
        vector<int>ans;
        vector<int>vec1(26,0);
        vector<int>vec2(26,0);
        for(int i = 0;i<p.size();i++){
            vec1[p[i]-'a']++;
            vec2[s[i]-'a']++;
        }
        if(vec1==vec2){
            ans.push_back(0);
        }
        for(int i = p.size();i<s.size();i++){
            vec2[s[i-p.size()]-'a']--;
            vec2[s[i]-'a']++;
            if(vec1==vec2){
                ans.push_back(i-p.size()+1);
            }
        }
        return ans;
    }
```

