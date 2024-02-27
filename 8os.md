```java
import java.util.*;

class Test {
    static int pageFaults(int pages[], int capacity) {
        HashSet<Integer> s = new HashSet<>();
        int page_faults = 0;

        for (int i = 0; i < pages.length; i++) {
            if (!s.contains(pages[i])) {
                if (s.size() == capacity) {
                    s.remove(pages[i - capacity]);
                }
                s.add(pages[i]);
                page_faults++;
            }
        }
        return page_faults;
    }

    public static void main(String args[]) {
        int pages[] = {7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2};
        int capacity = 4;
        System.out.println(pageFaults(pages, capacity));
    }
}
```

-----------------------------------------------------------------
```java

import java.util.*;

class Test {
    static int pageFaults(int pages[], int capacity) {
        HashSet<Integer> s = new HashSet<>();
        HashMap<Integer, Integer> indexes = new HashMap<>();
        int page_faults = 0;

        for (int i = 0; i < pages.length; i++) {
            if (!s.contains(pages[i])) {
                if (s.size() == capacity) {
                    int lru = Integer.MAX_VALUE, val = Integer.MIN_VALUE;
                    for (int page : s) {
                        if (indexes.containsKey(page) && indexes.get(page) < lru) {
                            lru = indexes.get(page);
                            val = page;
                        }
                    }
                    s.remove(val);
                    indexes.remove(val);
                }
                s.add(pages[i]);
                page_faults++;
            }
            indexes.put(pages[i], i);
        }
        return page_faults;
    }

    public static void main(String args[]) {
        int pages[] = {7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2};
        int capacity = 4;
        System.out.println(pageFaults(pages, capacity));
    }
}

```
