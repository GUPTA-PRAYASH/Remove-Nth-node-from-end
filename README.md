# Remove-Nth-node-from-end
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* curr=head; int k=0;ListNode* prev;
        if(head->next==NULL && n==1){delete(head); return NULL;}
        if(head==NULL) return head;
        while(curr!=NULL){
            k++;
            curr=curr->next;
        }
        if(n-k+1==1){
            ListNode* y=head;
            head=head->next;
            delete(y);
            return head;
        }
        ListNode* temp=head;
        for(int i=1;i<k-n+1;i++){
            prev=temp;
            temp=temp->next;
        }
        prev->next=temp->next;
        delete(temp);
        return head;
    }
};
