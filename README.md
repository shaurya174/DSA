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

