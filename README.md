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
