#include <stdio.h>
#include<stdlib.h>
struct subarray{           /*this structure is mainly created to store the maximum subarrray"s properties namely where does it start
                             it's end index and the sum of elements between these indices*/
    int start;
    int end;
    int sum;
};
struct subarray findmaxsubarray(int arr[],int low,int mid,int high)
{   struct subarray s;
    int x;                                                   /*this function returns a structure that defines the maximum subarray of a                                                                 given array*/
    int y;                                                     
    int leftsum=-2000,rightsum=-2000,sum=0,i=0,j=0;
    for(i=mid;i>=low;i--)
    {
        sum=sum+arr[i];
        if(sum>leftsum)
        {    x=i;
            leftsum=sum;
        }
    }
    sum=0;
    for(j=mid+1;j<=high;j++)
    {
        sum=sum+arr[j];
        if(sum>rightsum)
        {    y=j;
            rightsum=sum;
        }
    }
    s.sum=leftsum+rightsum;
    s.start=x;
    s.end=y;
    return s;
    
    

    
}
struct subarray maximumsubarray(int arr[],int low,int high)    /* divides  an array into two parts and recursively finds the maximum                                                                     subarray of those two parts*/
{
    int mid,i=low,j=high;
    if(low==high)
        {
            struct subarray s2;
            s2.start=low;
            s2.end=high;
            s2.sum=arr[low];
        }
    else
    {
         mid=(low+high)/2;
        struct subarray s1=maximumsubarray(arr,low,mid);
         struct subarray s2=maximumsubarray(arr,mid+1,high);
         struct subarray s3=findmaxsubarray(arr,low,mid,high);
         if(s1.sum>s2.sum && s1.sum>s3.sum)
         {
             return s1;
         }
        else if(s2.sum>s1.sum && s2.sum>s3.sum)
        
            return s2;
        
         else
            return s3;
    }
    
}
int main()
{
    int arr[]={-2,-5,6,-2,-3,1,5,-6};
    struct subarray sum=maximumsubarray(arr,0,7);
    printf("the maximum subarray starts at %d and ends at %d \t",sum.start,sum.end);
    printf("and has a sum that is maximum and is equal to %d",sum.sum);
   
    
    
    
}
