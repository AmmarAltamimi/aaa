```java
import java.util.*;
import java.util.concurrent.Semaphore;


class Que {
    int item;
    Semaphore semcon = new Semaphore(0);
    Semaphore semprod = new Semaphore(1);
    
    
    void get(){
        try{
            semcon.acquire();
            
        }catch(Exception e){
            System.out.println(e);
        }
        
        
        System.out.println("consumer consemed item : " + item);
        semprod.release();
        
    }
    
    
        void put(int item){
        try{
            semprod.acquire();
            
        }catch(Exception e){
            System.out.println(e);
        }
        
        this.item = item ;
        System.out.println("producer produced item : " + item);
        semcon.release();
        
    }
    
    
    
}




class producer implements Runnable {
     Que q;
      producer (Que q){
          this.q=q;
          new Thread(this).start();
      }
    
     public void run(){
         for(int i = 0  ; i< 5 ; i++){
             q.put(i);
         }
     }
    
    
}



class consumer implements Runnable {
    
        Que q;
      consumer (Que q){
          this.q=q;
          new Thread(this).start();
      }
    
     public void run(){
         for(int i = 0  ; i< 5 ; i++){
             q.get();
         }
     }
    
    
}




class pro {
    public static void main(String args[]){
        
        Que q = new Que();
        new producer(q);
        new consumer(q);
        
    }
}

```
