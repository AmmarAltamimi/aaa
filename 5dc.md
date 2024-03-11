```java
import java.util.*;


class bellMan{
    
    //A
    public static class node {
        public int[] dist = new int[20];
        public int[] from = new int[20];
    }
    
    
    //B
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int n,count;
        node[] routerTable = new node[20];
        int[][] cost = new int[20][20];
    
    //1
    System.out.println("Enter the number of nodes");
    n = sc.nextInt();
    
    //3
    for(int i =0 ; i< n ; i++)
        routerTable[i] = new node();
        
    //3
    System.out.println("enter the cost matrix");
    for(int i = 0 ; i< n ; i++)
        for(int j =0 ; j< n ; j++)
            cost[i][j] = sc.nextInt();
            
    //4
    for(int i = 0 ; i<n ; i++)
        for(int j =0 ; j <n ; j++){
            routerTable[i].dist[j]= cost[i][j];
            routerTable[i].from[j]= j;
        }
        
        
    //5
    do{
        count = 0;
        for(int i = 0 ; i<n ; i++)
            for(int j= 0 ; j <n ; j++)
                for(int k =0 ; k < n ; k++){
                    if(routerTable[i].dist[j] >  cost[i][k] + routerTable[k].dist[j]){
                        routerTable[i].dist[j] =  routerTable[i].dist[k] + routerTable[k].dist[j];
                        routerTable[i].from[j]= k;
                        count++;
                    }
                }
        
        
    }while(count != 0);
    
    
    //6
    for(int i =0 ; i< n ; i++){
        
        System.out.println("final router "+ (i+1));
        System.out.println("+------------------+");
        System.out.println("dest dist hop");
        System.out.println("+------------------+");
        for(int j=0 ; j< n ; j++)
             System.out.println( (j+1) +" "+ routerTable[i].dist[j] +" "+ (routerTable[i].from[j] +1) );
        System.out.println("+------------------+");
        
    }
        
        
    }

    
}

```
