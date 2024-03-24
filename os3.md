```java
import java.util.*;
import java.util.concurrent.Semaphore;



class philosoher implements Runnable {
    
    //1
    Semaphore room;
    Semaphore chopsticks[];
    int phil;
    public philosoher( Semaphore room, Semaphore chopsticks[], int phil){
        this.room=room;
        this.chopsticks=chopsticks;
        this.phil=phil;
    }
    
    
    //2
    public void run(){
        try{
            room.acquire();
            System.out.println("philosoher" + phil + "enter the room");
            chopsticks[phil].acquire();
            chopsticks[(phil+1) %  5].acquire();
            System.out.println("philosoher" + phil + "start eating");
            Thread.sleep(2000);
            System.out.println("philosoher" + phil + "finishing eating");
            chopsticks[phil].release();
            chopsticks[(phil+1) %  5].release();           
              room.release();
        }catch(Exception e){
            System.out.println(e);
        }
        
    }
    
 
}



class Main {
    
    public static void main(String[] args){
        
    //1
    Semaphore room = new Semaphore(4);
    Semaphore chopsticks[] = new Semaphore[5];
    for(int i =0 ; i < 5 ; i++)
        chopsticks[i]= new Semaphore(1);
    Thread[] phil = new Thread[5];
    for(int i = 0 ;i <5 ;i ++){
        phil[i] = new Thread(new philosoher(room,chopsticks,i));
        phil[i].start();
    }
        
    //2
    for(int i = 0 ; i<5 ; i++){
            try{
                phil[i].join();
            }catch(Exception e){
              System.out.println(e);  
            }
        }
        
        
    }
    
}


```
