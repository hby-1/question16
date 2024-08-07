# 统计一致字符串的数目

给你一个由不同字符组成的字符串 `allowed` 和一个字符串数组 `words` 。如果一个字符串的每一个字符都在 `allowed` 中，就称这个字符串是 一致字符串 。
找出 `words` 数组中 一致字符串 的数目。

## 示例 1：
>### 输入：
>allowed = "ab", words = ["ad","bd","aaab","baa","badab"]
>### 输出：
>2
>### 解释：
>字符串 "aaab" 和 "baa" 都是一致字符串，因为它们只包含字符 'a' 和 'b' 。

## 示例 2：
>### 输入：
>allowed = "abc", words = ["a","b","c","ab","ac","bc","abc"]
>### 输出：
>7
>### 解释：
>所有字符串都是一致的。

## 代码：
1.

    public class Solution {
        public int CountConsistentStrings(string allowed, string[] words) {
            int num=words.Length;
            foreach(string word in words){
                for(int i=0;i<word.Length;i++){
                    if(!allowed.Contains(word[i])){
                        num--;
                        break;
                    }
                }
            }
            return num;
        }
    }
2.

    public class Solution {
        public int CountConsistentStrings(string allowed, string[] words) {
            // 将 allowed 中的字符存入 HashSet 中，以便快速查找
            HashSet<char> allowedSet = new HashSet<char>(allowed);
            int consistentCount = 0;

            // 遍历 words 数组中的每个字符串
            foreach (string word in words) {
                bool isConsistent = true;

                // 检查 word 的每个字符
                foreach (char c in word) {
                    // 如果字符不在 allowedSet 中，标记为不一致并退出检查
                    if (!allowedSet.Contains(c)) {
                        isConsistent = false;
                        break;
                    }
                }

                // 如果字符串是一致的，增加计数
                if (isConsistent) {
                    consistentCount++;
                }
            }

            return consistentCount;
        }
    }
3.

    public class Solution {
        public int CountConsistentStrings(string allowed, string[] words) {
            ISet<char> allowedSet = new HashSet<char>();
            foreach (char c in allowed) {
                allowedSet.Add(c);
            }
            int consistent = 0;
            foreach (string word in words) {
                bool flag = true;
                int wordLength = word.Length;
                for (int i = 0; i < wordLength && flag; i++) {
                    char c = word[i];
                    if (!allowedSet.Contains(c)) {
                        flag = false;
                    }
                }
                if (flag) {
                    consistent++;
                }
            }
            return consistent;
        }
    }
