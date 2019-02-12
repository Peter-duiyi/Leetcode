## Bitwise operations

### Introduction

A summery of bitwise operations

------
### Solution 1

There are several things that we need to know before we work on that problem.
* How to declare pointers in one line
```
  char a = '5';  
  int b = a - '0';
```
* how to convert an integer into a char:
```
  ListNode* p1 = l1, *p2 = l2;
```
  explanation further
  
------
### Code 1

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* p1 = l1, *p2 = l2, *head = nullptr;
        vector<int> v1, v2;
        while(p1 || p2){
            if(p1) {
                v1.push_back(p1->val);
                p1 = p1->next;
            }
            if(p2){
                v2.push_back(p2->val);
                p2 = p2->next;
            }
        }
        int index1 = v1.size() - 1, index2 = v2.size() - 1, carry = 0;
        while(index1 >= 0 || index2 >= 0 || carry){
            int v1_val = index1 >=0 ? v1[index1] : 0;
            int v2_val = index2 >=0 ? v2[index2] : 0;
            int sum = v1_val + v2_val + carry;
            carry = sum / 10;
            
            ListNode* newNode = new ListNode(sum % 10); // digit
            if(head) newNode->next = head;
            head = newNode;
            index1 --;
            index2 --;
        }
        return head;
    }
};

```
Complexity  
Time:  
Space:

------
### Reference
Problem: https://leetcode.com/problems/counting-bits/ 
Solution: http://www.cnblogs.com/grandyang/p/5294255.html
