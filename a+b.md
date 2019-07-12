**题目链接**

> https://leetcode-cn.com/problems/two-sum/

**题目大意**

> 给你几个数，然后再给你一个数，问你从这几个数里面选出来两个，能不能构成给定的数（题目保证解一定存在）

**具体解题思路**

1. 方法一，两个for循环暴力跑.复杂度 O（n*n）

`class Solution {`
`public:`
   `vector<int> twoSum(vector<int>&nums, int target) {`
        `for (int i = 0;i < nums.size() ;i++ ){`
          `for ( int j = i + 1 ; j < nums.size() ; j++ ){`  
              `if(nums[i] + nums[j] == target ){`
                  `vector<int>tmp;`
                  `tmp.push_back(i);`
                  `tmp.push_back(j);`
                  `return tmp;`
              `}`
          `}`
        `}` 
       `vector<int>tmp;`
       `return tmp;
   `}`
`};`

2. 方法二，这个方法适用于样例中的数都比较小的时候。打一个桶，储存每个值都在哪些位置出现过，然后遍历两边数组就可以了。空间换时间。复杂度O（2n）

   `class Solution {`
   `public:`
      `vector<int> twoSum(vector<int>&nums, int target) {`
        `vector<int>ans;`
        `vector<int>mp[1000000+10];`
          `int len = nums.size();`
          `for (int i = 0 ; i< len ; i++ ){`
             `mp[nums[i]].push_back(i);`
          `}`
          `for( int i = 0 ; i< len ; i++ ){`
             `if(target < nums[i] )continue;`
              `if(nums[i] + nums[i] == target && mp[ nums[i] ].size()>=2){`
               `ans.push_back(mp[nums[i]][0]);`
               `ans.push_back(mp[nums[i]][1]);`
                  `break;`
              `}`
              `if(mp[target - nums[i]].size() >= 1){`
                `ans.push_back(i);`
                `ans.push_back(mp[ target - nums[i] ][0]);`
                  `break;`
              `}`
          `}`
          `return ans;`
      `}`
   `};`









