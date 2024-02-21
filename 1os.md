**1)FCFS**
```java
import java.util.*;



class main{


    static void avgtime(int p[],int n,int bt[]){
        
        
            // wt & tat 
            int wt[] = new int[n];
            int tat[] = new int[n];
            
            // waiting time
            wt[0]=0;
            for(int i = 1 ; i <n ; i++)
                wt[i]=bt[i-1] + wt[i-1];
                
            //total around avgtime
            for(int i = 0 ; i<n ; i++)
                tat[i]=bt[i] + wt[i];
                
            
            //Table with total
            int total_wt = 0;
            int total_tat = 0;
            System.out.println("process\tburstTime\twaitingTime\ttotalAroundTime\n");
            for(int i = 0 ; i< n ; i++){
             total_wt +=wt[i]; 
             total_tat +=tat[i]; 
            System.out.print((i+1)+"\t");
            System.out.print(bt[i]+"\t");
            System.out.print(wt[i]+"\t");
            System.out.print(tat[i]+"\n");
            
            
            }
            
            //avg 
            float avg_wt = (float)total_wt / (float)n;
            float avg_tat =(float) total_tat / (float)n;
             System.out.println("wating time average is " + avg_wt);
             System.out.println("total around time average is " + avg_tat);

            //drive 
            
    }
            public static void main(String args[]){
                int p[]={1,2,3};
                int n = p.length;
                int bt[] = {3,2,1};
                
                 avgtime(p,n,bt);
                
            }

}
```
-----------------------------------
**2)SJF**
```java
import java.util.*;



class main{


    static void avgtime(int p[],int n,int bt[]){
        
            // sort in sjf
            for(int i = 0 ; i < n ; i++)
                     for(int j = 0 ; j<n ; j++)
                        if(bt[i] < bt[j]){
                                          
                            int temp = p[i];
                            p[i]= p[j];
                            p[j]= temp;
                            
                             temp = bt[i];
                            bt[i]=bt[j];
                            bt[j]=temp;
              
                        }
    
             
            // wt & tat 
            int wt[] = new int[n];
            int tat[] = new int[n];
            
            // waiting time
            wt[0]=0;
            for(int i = 1 ; i <n ; i++)
                wt[i]=bt[i-1] + wt[i-1];
                
            //total around avgtime
            for(int i = 0 ; i<n ; i++)
                tat[i]=bt[i] + wt[i];
                
            
            //Table with total
            int total_wt = 0;
            int total_tat = 0;
            System.out.println("process\tburstTime\twaitingTime\ttotalAroundTime\n");
            for(int i = 0 ; i< n ; i++){
             total_wt +=wt[i]; 
             total_tat +=tat[i]; 
            System.out.print((i+1)+"\t");
            System.out.print(bt[i]+"\t");
            System.out.print(wt[i]+"\t");
            System.out.print(tat[i]+"\n");
            
            
            }
            
            //avg 
            float avg_wt = (float)total_wt / (float)n;
            float avg_tat = (float) total_tat /(float)n;
             System.out.println("wating time average is " + avg_wt);
             System.out.println("total around time average is " + avg_tat);

            //drive 
            
    }
            public static void main(String args[]){
                int p[]={1,2,3};
                int n = p.length;
                int bt[] = {3,2,1};
                
                 avgtime(p,n,bt);
                
            }

    

}
```
