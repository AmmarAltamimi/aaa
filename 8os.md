```java
import java.util.*;


class Test {
    
        static int pageFault (int[] pages , int capacity){
            //1
            HashSet <Integer> s = new  HashSet<>();
            int page_fault = 0;
            //2
            for(int i =0 ; i < pages.length ; i++){
                if(!s.contains(pages[i])){
                    if(s.size() == capacity){
                        s.remove(pages[i-capacity]);
                    }
                    s.add(pages[i]);
                    page_fault++;
                }
            }
            //3
            return page_fault;
                
        }
    
    public static void main(String args[]){
        int[] pages ={7,0,1,2,0,3,0,4,2,3,0,3,2};
        int capacity = 4;
        System.out.println(pageFault(pages,capacity));
    }
    
}

// output
// 9

```

-----------------------------------------------------------------
```java

import java.util.*;


class Test {
    
        static int pageFault (int[] pages , int capacity){
            //1
            HashSet <Integer> s = new  HashSet<>();
            HashMap <Integer,Integer> indexes = new  HashMap<>();
            int page_fault = 0;
            int lru = Integer.MAX_VALUE;
            int val = Integer.MIN_VALUE;
            
            //2
            for(int i =0 ; i < pages.length ; i++){
                if(!s.contains(pages[i])){
                    if(s.size() == capacity){
                        
                        //A
                        for(int n : s )
                            if(indexes.containsKey(n) && indexes.get(n) < lru ){
                                lru = indexes.get(n);
                                val = n;
                            }
                            
                        //B
                        s.remove(val);
                        indexes.remove(val);
                        
                    }
                    
                    s.add(pages[i]);
                    page_fault++;
                }
                indexes.put(pages[i],i);
            }
            //3
            return page_fault;
            
            
        }
    
    public static void main(String args[]){
        int[] pages ={7,0,1,2,0,3,0,4,2,3,0,3,2};
        int capacity = 4;
        System.out.println(pageFault(pages,capacity));
    }
    
}


// output
// 6


```
