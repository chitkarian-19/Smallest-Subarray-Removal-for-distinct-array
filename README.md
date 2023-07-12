# Smallest-Subarray-Removal-for-distinct-array
Smallest Subarray Removal for distinct array
`````cpp
import java.util.ArrayList;
import java.util.HashSet;
import java.util.Scanner;

public class ArrayDistinct {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] arr = new int[n];
        for(int i=0;i<n;i++){
            arr[i]=sc.nextInt();
        }
        ArrayList<Integer> op = new ArrayList<Integer>();
        op = findSmallestDuplicateSegment(arr,n);
        if(op!=null){
            int st = op.get(0);
            int et = op.get(1);
            for(int i=st;i<=et;i++){
                System.out.print(arr[i]+" ");
            }
        }
    }
    static ArrayList<Integer> findSmallestDuplicateSegment(int [] arr,int n){

        HashSet<Integer> hst1 = new HashSet<Integer>();
        int min = Integer.MAX_VALUE;
        int st = -1;
        int et = -1;
        for(int i=0;i<n;i++){
            if(hst1.contains(arr[i])){
                break;
            }
            hst1.add(arr[i]);
            HashSet<Integer> hst2 = new HashSet<Integer>();
            int j ;
            for(j=n-1;j>i;j--){
                if(hst1.contains(arr[j])||hst2.contains(arr[j])){
                    
                    break;
                }
                else{
                    hst2.add(arr[j]);
                }
            }
            if(j!=i){
                int diff = j-i;
                if(diff<min){
                    st = i+1;
                    et  = j;
                }
            }
        }
        if(st!=-1){
            ArrayList<Integer> al = new ArrayList<Integer>();
            al.add(st);
            al.add(et);
            return al;
        }
        return null;
    }
}

```
