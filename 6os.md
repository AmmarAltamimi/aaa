```java
import java.util.Scanner;

public class BankersAlgorithm {
    static void calculateNeed(int[][] need, int[][] max, int[][] alloc) {
        for (int i = 0; i < need.length; i++)
            for (int j = 0; j < need[i].length; j++)
                need[i][j] = max[i][j] - alloc[i][j];
    }

    static boolean checkSafety(int[] processes, int[] available, int[][] max, int[][] alloc) {
        int[][] need = new int[processes.length][available.length];
        calculateNeed(need, max, alloc);
        boolean[] finish = new boolean[processes.length];
        int[] safeSeq = new int[processes.length];
        int[] work = available.clone();
        int count = 0;

        while (count < processes.length) {
            boolean found = false;
            for (int i = 0; i < processes.length; i++) {
                if (!finish[i]) {
                    int j;
                    for (j = 0; j < available.length; j++) {
                        if (need[i][j] > work[j])
                            break;
                    }
                    if (j == available.length) {
                        for (int k = 0; k < available.length; k++)
                            work[k] += alloc[i][k];
                        safeSeq[count++] = i;
                        finish[i] = true;
                        found = true;
                    }
                }
            }
            if (!found) {
                System.out.print("Unsafe due to resource scarcity");
                return false;
            }
        }

        System.out.print("Safe sequence: ");
        for (int i = 0; i < processes.length; i++)
            System.out.print("P" + safeSeq[i] + " ");
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter total number of processes");
        int n = sc.nextInt();
        System.out.println("Enter total number of resources");
        int m = sc.nextInt();

        int[] processes = new int[n];
        for (int i = 0; i < n; i++)
            processes[i] = i;

        int[] available = new int[m];
        for (int i = 0; i < m; i++) {
            System.out.println("Enter the availability of resource " + i + ":");
            available[i] = sc.nextInt();
        }

        int[][] max = new int[n][m];
        System.out.println("Enter the maximum demand matrix:");
        for (int i = 0; i < n; i++)
            for (int j = 0; j < m; j++)
                max[i][j] = sc.nextInt();

        int[][] allocation = new int[n][m];
        System.out.println("Enter the allocation matrix:");
        for (int i = 0; i < n; i++)
            for (int j = 0; j < m; j++)
                allocation[i][j] = sc.nextInt();

        checkSafety(processes, available, max, allocation);
    }
}
```
