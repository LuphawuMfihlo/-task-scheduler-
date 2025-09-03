# -task-scheduler-
package mentoring.task.pkg2;

public class MentoringTask2 {
    
    public static int leastInterval(char[] tasks, int n) {
        // Count frequency of each task
        int[] freq = new int[10];
        for (char task : tasks) {
            freq[task - 'A']++;
        }
        
        // Find the maximum frequency
        int maxFreq = 0;
        for (int f : freq) {
            maxFreq = Math.max(maxFreq, f);
        }
        
        // Count how many tasks have the maximum frequency
        int maxCount = 0;
        for (int f : freq) {
            if (f == maxFreq) {
                maxCount++;
            }
        }
        
        // Calculate minimum intervals needed
        int partCount = (maxFreq - 1) * (n + 1) + maxCount;
        
        // Return the maximum of calculated intervals or total tasks
        return Math.max(partCount, tasks.length);
    }
    
    public static void main(String[] args) {
        char[] tasks = {'A', 'A', 'B', 'C'};
        int n = 2;
        System.out.println("Minimum intervals needed: " + leastInterval(tasks, n));
        
        // Additional test cases
        char[] tasks2 = {'A', 'A', 'A', 'B', 'B', 'B'};
        int n2 = 2;
        System.out.println("Test case 2: " + leastInterval(tasks2, n2));
        
        char[] tasks3 = {'A', 'B', 'C', 'D', 'E', 'F'};
        int n3 = 2;
        System.out.println("Test case 3: " + leastInterval(tasks3, n3));
    }
}