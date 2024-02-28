```java
import java.util.*;

class bankerAlgorthim {
            
            static void findNeed(int[][] need , int[][] max , int[][]allocation , int n , int m){
                        for(int i=0 ; i< n ; i++)
                            for(int j = 0 ; j < m ; j++)
                                need[i][j] = max[i][j] - allocation[i][j];
                        
            }
            
           
            static boolean check (int[] process , int [][] max , int[][] allocation, int[] available , int n ,int m ){
                    int[][] need = new int [n][m];
                    findNeed(need,max,allocation,n,m);

                    boolean [] finish = new boolean[n];
                    int [] safeSeq = new int[n];
                    int[] work = available.clone();
                    int count = 0 ;
                    
                    
                    while(count < n){
                        //1
                        boolean found = false;
                        
                        //2
                        for(int i = 0 ; i< n ; i++){
                            if(finish[i] == false){
                                
                                //A
                                int j ;
                                for(j=0 ; j < m ; j++)
                                    if(need[i][j] > work[j])
                                        break;
                                
                                //B
                                if(j == m){
                                    for(int k= 0 ; k < m ; k++ )
                                        work[k] += allocation[i][k];
                                        
                                    safeSeq[count++] = i;
                                    finish[i]=true;
                                    found = true;
                                }
                                
                            }
                        }
                        
                        //3
                        if(found == false){
                            System.out.println("unsafe due to resource sacrcity");
                            return false;
                        }
                            
                    }
                    
                    
                    
                    System.out.print("the safeSeq is ");
                    for(int i = 0 ; i < n ; i++){
                        System.out.print("p"+safeSeq[i]+" ");
                    }
                    return true ; 
            }
    
    
    // main 
    public static void main (String args[]){
        Scanner sc = new Scanner(System.in);
        
        // no of processes
        int n ; 
        System.out.println("Enter no of processes");
        n = sc.nextInt();
        int[] process = new int [n];
        for(int i = 0 ; i < n ; i++)
            process[i]=i;
            
        // no of resource
        int m ;
         System.out.println("Enter no of resuorce");
        m = sc.nextInt();
        
        //available 
        int[] available = new int [m];
        System.out.println("Enter the availablitiy ");
        for(int i = 0 ; i < m ; i++){
            available[i] = sc.nextInt();
        }
        //max 
        int[][] max = new int [n][m];
         System.out.println("Enter the max matrix ");
        for(int i = 0 ; i < n ; i++)
            for(int j=0 ; j< m ; j++)
                max[i][j] = sc.nextInt();
                
        //allocation 
        int [][] allocation = new int[n][m];
        System.out.println("Enter the allocation matrix ");
        for(int i = 0 ; i < n ; i++)
            for(int j=0 ; j< m ; j++)
                allocation[i][j] = sc.nextInt();  
                
                
        check (process , max , allocation ,available ,n,m);
        
    }
    
}
```
