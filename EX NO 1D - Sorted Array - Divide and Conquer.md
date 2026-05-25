
# EX 1D Sorted Array using Divide and Conquer Approach.
## DATE: 25/05/2026
## AIM:
To write a Java program to for given constraints.
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

## Algorithm

1.Start the program and read the sizes and elements of two sorted arrays, nums1[] and nums2[].

2.Initialize two pointers p1 = 0 and p2 = 0 to traverse both arrays.

3.Merge conceptually:

Use a helper method getMin() to return the smaller of nums1[p1] and nums2[p2], moving the corresponding pointer forward.

Continue calling getMin() until reaching the middle position(s) of the combined sorted sequence.

4.Check the total length (m + n):

If even, take the average of the two middle elements as the median.

If odd, take the middle element as the median.

5.Display the median and stop the program. 

## Program:
```

Program to implement Reverse a String
Developed by: Dappili Vasavi
Register Number:212223040030
import java.util.Scanner;

public class Solution {
    private int p1 = 0, p2 = 0;

    
    private int getMin(int[] nums1, int[] nums2) {
        if (p1 < nums1.length && p2 < nums2.length) {
            return nums1[p1] < nums2[p2] ? nums1[p1++] : nums2[p2++];
        } else if (p1 < nums1.length) {
            return nums1[p1++];
        } else if (p2 < nums2.length) {
            return nums2[p2++];
        }
        return -1; 
    }

    
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int m=nums1.length,n=nums2.length;
        if((m+n)%2==0){
            for(int i=0;i<(m+n)/2-1;i++){
                int tmp=getMin(nums1,nums2);
            }
            return (double) (getMin(nums1,nums2)+getMin(nums1,nums2))/2;
        }else{
            for(int i=0;i<(m+n)/2;i++){
                int tmp=getMin(nums1,nums2);
            }
            return getMin(nums1,nums2);
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        
        int m = sc.nextInt();
        int[] nums1 = new int[m];
      
        for (int i = 0; i < m; i++) {
            nums1[i] = sc.nextInt();
        }

        
        
        int n = sc.nextInt();
        int[] nums2 = new int[n];
        
        for (int i = 0; i < n; i++) {
            nums2[i] = sc.nextInt();
        }

       
        double median = sol.findMedianSortedArrays(nums1, nums2);
        System.out.println("Median of the two sorted arrays = " + median);
        
        sc.close();
    }
}


```

## Output:
<img width="903" height="366" alt="image" src="https://github.com/user-attachments/assets/98e027ac-6de6-4da6-8873-acc96edbf11d" />



## Result:
The program successfully implemented and the expected output is verified.
