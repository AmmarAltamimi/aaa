**1)fisrtfit**

```java
import java.util.*;


class first_fit{
    
    static void firstFit(int blockSize [],int m , int processSize[],int n){
        
        int allocation [] = new int [n];
        for(int i = 0 ; i < n ; i++){
            allocation[i]=-1;
            for(int j = 0 ; j <m ; j++ ){
                
                if(blockSize[j] >= processSize[i]){
                    allocation[i]=j;
                    blockSize[j] -= processSize[i];
                    break;
                }
            }
        }
        
        
        System.out.println("\nprocess no\tprocessSize\tblock no");
        for(int i = 0 ; i< n ; i ++){
            System.out.print(" "+(i+1)+"\t\t"+processSize[i]+"\t\t");
            if(allocation[i] != -1){
             System.out.print(allocation[i]+1);
            }else{
              System.out.print("Not allocated");
            }
          System.out.println();

        }
        
    }
    
    



    
    public static void main(String[] args){
        int blockSize[] = {100, 500, 200, 300, 600};
        int m = blockSize.length;
        int  processSize[] = {212, 417, 112, 426};
        int n = processSize.length;
        
        firstFit(blockSize,m ,processSize,n);
  
}
}
```

-----------------------------------
**2)bestfit**

```java
import java.util.*;


class best_fit{
    
    static void bestFit(int blockSize [],int m , int processSize[],int n){
        
        int allocation [] = new int [n];
        for(int i = 0 ; i < n ; i++){
            int bestidx=-1;
            for(int j = 0 ; j <m ; j++ ){
                
                if(blockSize[j] >= processSize[i]){
                    
                    if(bestidx == -1){
                        bestidx =j;
                    }else if(blockSize[bestidx] > blockSize[j]){
                          bestidx =j;
                    }


                }
            }
            
                if(bestidx != -1){
                    allocation[i]=bestidx;
                    blockSize[bestidx] -= processSize[i];
               
                }
            
        }
        
        
        System.out.println("\nprocess no\tprocessSize\tblock no");
        for(int i = 0 ; i< n ; i ++){
            System.out.print(" "+(i+1)+"\t\t"+processSize[i]+"\t\t");
            if(allocation[i] != -1){
             System.out.print(allocation[i]+1);
            }else{
              System.out.print("Not allocated");
            }
          System.out.println();

        }
        
    }
    
    



    
    public static void main(String[] args){
        int blockSize[] = {100, 500, 200, 300, 600};
        int m = blockSize.length;
        int  processSize[] = {212, 417, 112, 426};
        int n = processSize.length;
        
        bestFit(blockSize,m ,processSize,n);
  
}
}
```

---------------------------------
**3)worstfit**

```java
import java.util.*;


class worst_fit{
    
    static void  worstFit(int blockSize [],int m , int processSize[],int n){
        
        int allocation [] = new int [n];
        for(int i = 0 ; i < n ; i++){
            int  worstidx=-1;
            for(int j = 0 ; j <m ; j++ ){
                
                if(blockSize[j] >= processSize[i]){
                    
                    if( worstidx == -1){
                         worstidx =j;
                    }else if(blockSize[worstidx] < blockSize[j]){
                           worstidx =j;
                    }


                }
            }
            
                if( worstidx != -1){
                    allocation[i]= worstidx;
                    blockSize[ worstidx] -= processSize[i];
               
                }
            
        }
        
        
        System.out.println("\nprocess no\tprocessSize\tblock no");
        for(int i = 0 ; i< n ; i ++){
            System.out.print(" "+(i+1)+"\t\t"+processSize[i]+"\t\t");
            if(allocation[i] != -1){
             System.out.print(allocation[i]+1);
            }else{
              System.out.print("Not allocated");
            }
          System.out.println();

        }
        
    }
    
    



    
    public static void main(String[] args){
        int blockSize[] = {100, 500, 200, 300, 600};
        int m = blockSize.length;
        int  processSize[] = {212, 417, 112, 426};
        int n = processSize.length;
        
         worstFit(blockSize,m ,processSize,n);
  
}
}
```
