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
            
            int n = 5;
            int m = 3;
            int [] process = {0,1,2,3,4};
            int [] available = {4,4,4};
            int [][] max = {{7,5,3},{3,2,2},{9,0,2},{2,2,3},{4,3,3}};
            int [][] allocation = {{0,1,0},{2,0,0},{3,0,2},{2,1,1},{0,0,2}};
                
        check (process , max , allocation ,available ,n,m);
        
    }
    
}

//output
// the safeSeq is p1 p2 p3 p4 p0


```
