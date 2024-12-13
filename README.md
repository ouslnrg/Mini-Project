public class Bestfit {
    public static void main(String[] args) {
        int[] memoryBlocks = {10, 20, 30, 40, 80}; // Memory block sizes
        int[] processes = {65};   // Process sizes

        // Array to store allocation of each process
        int[] allocation = new int[processes.length];
        for (int i = 0; i < allocation.length; i++) {
            allocation[i] = -1; // Initialize with -1 (not allocated)
        }

        // Best Fit Allocation
        for (int i = 0; i < processes.length; i++) {
            int bestIndex = -1;
            for (int j = 0; j < memoryBlocks.length; j++) {
                if (memoryBlocks[j] >= processes[i]) {
                    if (bestIndex == -1 || memoryBlocks[j] < memoryBlocks[bestIndex]) {
                        bestIndex = j;
                    }
                }
            }

            // Allocate the process to the best fit block
            if (bestIndex != -1) {
                allocation[i] = bestIndex;
                memoryBlocks[bestIndex] -= processes[i];
            }
        }

        // Print allocation results
        System.out.println("Process No.\tProcess Size\tBlock Allocated");
        for (int i = 0; i < processes.length; i++) {
            System.out.printf("%-12d%-16d", i + 1, processes[i]);
            if (allocation[i] != -1) {
                System.out.println("Block " + (allocation[i] + 1));
            } else {
                System.out.println("Not Allocated");
            }
        }
    }
}
