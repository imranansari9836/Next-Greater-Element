# Next-Greater-Element
Given an array arr[ ] of size N having elements, the task is to find the next greater element for each element of the array in order of their appearance in the array.
Next greater element of an element in the array is the nearest element on the right which is greater than the current element.
If there does not exist next greater of current element, then next greater element for current element is -1. For example, next greater of the last element is always -1.

Example 1:

Input: 
N = 4, arr[] = [1 3 2 4]
Output:
3 4 4 -1
Explanation:
In the array, the next larger element 
to 1 is 3 , 3 is 4 , 2 is 4 and for 4 ? 
since it doesn't exist, it is -1.

class Solution
{
    //Function to find the next greater element for each element of the array.
    public static long[] nextLargerElement(long[] arr, int n)
    {    long []nge = new long [n]; // n is the size of input                                                      array

    

    Stack<Long> st = new Stack<Long>();

    

  st.push(arr[n-1]); // simply pushing the last element                                  of the input array

  nge[n-1] = -1; // place nge for it as -1

    

    for(int i = n-2;i>=0;i--){ // start iterating from 2nd                                                  last element till 1st element

       while(st.size()>0 && arr[i] >= st.peek()){

           st.pop(); // keep poping till stack isn't empty                                and element to be inserted is                                         >= st.peek()

       } 

       if(st.size() == 0){ // stack is empty

         nge[i] = -1;// if no element in "st" is found                                          to be > then i ; put nge = -1

       }

       else{

        nge[i] = st.peek();// peek element becomes nge                                         for the element to be inserted

       }

       st.push(arr[i]); // the element pushes itself as it                                may be NGE for elements to its left 

    }

    return nge;

    } 

}
