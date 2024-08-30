Smallest Sub-array with sum greater than a given value in Java
Here, in this page we will discuss the program to find smallest sub-array with sum greater than a given value in Java programming language. We are given with an unsorted array contain non-negative integers we need to find a continuous sub-array of minimum length whose sum is greater than the given sum

Smallest Sub-array with sum greater than a given value in Java
Method Discussed :
Method 1 : Naive Approach
Method 2 : Efficient Approach
Let’s discuss them one by one in brief,

Method 1:
Run a loop from 0 to n and declare a variable  curr_sum with value of i-th element.
Chech if curr_sum > sum, if so then return 1.
Otherwise, run another loop inside it, that will traverse from i+1 to n index, and add the value of j-th element to curr_sum.
If curr_sum > sum and (j-i+1 < min_length), then update min_length to (j-i+1)
After coming out from the nested loop return min_length.
Now, in main function check if the return value from the function == n+1 then print “No such array found”
Smallest sub-array with sum greater than given value
Method 1 : Code in Java
Run
class Main
{
    static int smallestSubWithSum(int arr[], int n, int x)
    {
        int min_len = n + 1;
 
        for (int start = 0; start < n; start++)
        {
            int curr_sum = arr[start];
 
            if (curr_sum > x)
                return 1;
 
            for (int end = start + 1; end < n; end++)
            {
                curr_sum += arr[end];
                if (curr_sum > x && (end - start + 1) < min_len)
                    min_len = (end - start + 1);
            }
        }
        return min_len;
    }
 
    
    public static void main(String[] args)
    {
        int arr[] = {1, 4, 45, 6, 10, 19};
        int x = 51;
        int n = arr.length;
        int res = smallestSubWithSum(arr, n, x);
        if (res == n+1)
           System.out.println("Not Possible");
        else
           System.out.println(res);

    }
}
Output :
3
Related Pages
Given an array which consists of only 0, 1 and 2

Move all the negative elements to one side of the array

Find the Union and Intersection of the two sorted arrays

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Method 2:
In this method we will discuss the optimize way to solve the given problem.

Time and Space Complexity :
Time-Complexity : O(n)
Space-Complexity : O(1)
Method 2 : Code in Java
Run
class Main {
    
    static int smallestSubWithSum(int arr[], int n, int x)
    {
       
        int curr_sum = 0, min_len = n + 1;
 
        int start = 0, end = 0;
        while (end < n) {
            
            while (curr_sum <= x && end < n)
                curr_sum += arr[end++];
 
            while (curr_sum > x && start < n) {
                if (end - start < min_len)
                    min_len = end - start;
 
                curr_sum -= arr[start++];
            }
        }
        return min_len;
    }
 
    
    public static void main(String[] args)
    {
        int arr[] = {1, 4, 45, 6, 10, 19};
        int x = 51;
        int n = arr.length;
        int res = smallestSubWithSum(arr, n, x);
        if (res == n+1)
           System.out.println("Not Possible");
        else
           System.out.println(res);

    }
}
Output :
3
