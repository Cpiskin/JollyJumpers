import java.util.Scanner;

public class JollyJumper {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (scanner.hasNextLine()) {
            // Read the line of input
            String line = scanner.nextLine();
            // Split the line into parts
            String[] parts = line.split(" ");
            // Get the value of n
            int n = Integer.parseInt(parts[0]);

            // Initialize variables
            boolean isJolly = true;
            boolean[] differencesPresent = new boolean[n - 1];

            // Read the first element as prev
            int prev = Integer.parseInt(parts[1]);

            // Iterate through the rest of the elements
            for (int i = 2; i <= n; i++) {
                // Read the current element
                int current = Integer.parseInt(parts[i]);
                // Calculate the absolute difference
                int diff = Math.abs(current - prev);

                // Check if the difference is within the valid range
                if (diff < 1 || diff > n - 1) {
                    isJolly = false;
                    break;
                }

                // Mark the difference as present
                differencesPresent[diff - 1] = true;

                // Update prev for the next iteration
                prev = current;
            }

            // Check if all required differences are present
            if (isJolly) {
                for (boolean difference : differencesPresent) {
                    if (!difference) {
                        isJolly = false;
                        break;
                    }
                }
            }

            // Output the result
            System.out.println(isJolly ? "Jolly" : "not jolly");
        }
    }
}
