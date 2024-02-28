```java
import java.util.*;


class Main {
    
    public static void main(String args[]){
        Scanner sc = new Scanner(System.in);
        int ms,ps,nop,rempages,np,x,y,offset,pa;
        int [] s = new int[20];
        int [][] fno = new int[20][20];
        
        //1
        System.out.println("Enter the memory size");
        ms = sc.nextInt();
        System.out.println("Enter the page size");
        ps = sc.nextInt();
        nop = ms/ps;
        System.out.println("the no of pages is "+nop);
        rempages = nop;
        
        //2
        System.out.println("Enter the no of processes");
        np = sc.nextInt();
        
        for(int i = 1 ; i<= np ; i++){
            //A
             System.out.println("Enter the no of page requied for p["+i+"]");
            s[i]=sc.nextInt();
            //B
            if(s[i] > rempages){
            System.out.println("memory is full");
            break;
            }
            rempages = rempages - s[i];
            //C
            System.out.println("Enter pagetable for p["+i+"] ");
            for(int j =0 ; j < s[i] ;j++)
                fno[i][j] = sc.nextInt();
        }
        
        //3
         System.out.println("Enter the logical address to find phyical address");
         System.out.println("Enter the process no and pageNumber and offset");
         x=sc.nextInt();
         y=sc.nextInt();
         offset=sc.nextInt();
         
         if(x > np || y >=s[x] || offset >= ps){
             System.out.println("Invalid process no or pageNumber or offset");
         } else {
             pa = fno[x][y] * ps + offset ;
             System.out.println("Enter the phyical address is " + pa);
         }
        
        

        
    }
    
    
}


//output
// Enter the memory size
// 1000
// Enter the page size
// 100
// the no of pages is 10
// Enter the no of processes
// 3
// Enter the no of page requied for p[1]
// 4
// Enter pagetable for p[1] 
// 8 6 9 5
// Enter the no of page requied for p[2]
// 5
// Enter pagetable for p[2] 
// 1 4 5 7 3
// Enter the no of page requied for p[3]
// 5
// memory is full
// Enter the logical address to find phyical address
// Enter the process no and pageNumber and offset
// 2
// 3
// 60
// Enter the phyical address is 760
```
