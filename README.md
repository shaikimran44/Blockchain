# Palindrome Java Program

```java
public class PalindromeChecker {
    
    // Method 1: Using Two Pointers (Most Efficient)
    public static boolean isPalindrome(String str) {
        // Remove spaces and convert to lowercase
        str = str.replaceAll("\\s+", "").toLowerCase();
        
        // Check if string reads the same forwards and backwards
        int left = 0;
        int right = str.length() - 1;
        
        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
    
    // Method 2: Using StringBuilder Reverse
    public static boolean isPalindromeReverse(String str) {
        str = str.replaceAll("\\s+", "").toLowerCase();
        String reversed = new StringBuilder(str).reverse().toString();
        return str.equals(reversed);
    }
    
    // Method 3: Using Recursion
    public static boolean isPalindromeRecursive(String str) {
        str = str.replaceAll("\\s+", "").toLowerCase();
        return checkPalindrome(str, 0, str.length() - 1);
    }
    
    private static boolean checkPalindrome(String str, int left, int right) {
        if (left >= right) {
            return true;
        }
        if (str.charAt(left) != str.charAt(right)) {
            return false;
        }
        return checkPalindrome(str, left + 1, right - 1);
    }
    
    // Method 4: Check Only Alphanumeric Characters
    public static boolean isPalindromeAlphanumeric(String str) {
        String cleaned = str.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
        int left = 0;
        int right = cleaned.length() - 1;
        
        while (left < right) {
            if (cleaned.charAt(left) != cleaned.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
    
    // Main method for testing
    public static void main(String[] args) {
        // Test cases
        String[] testStrings = {
            "racecar",
            "hello",
            "A man a plan a canal Panama",
            "madam",
            "was it a car or a cat i saw",
            "12321",
            "java",
            "Able was I ere I saw Elba"
        };
        
        System.out.println("============================================================");
        System.out.println("PALINDROME CHECKER - ALL METHODS");
        System.out.println("============================================================");
        
        for (String test : testStrings) {
            System.out.println("\nInput: \"" + test + "\"");
            System.out.println("Method 1 (Two Pointers):  " + isPalindrome(test));
            System.out.println("Method 2 (Reverse):      " + isPalindromeReverse(test));
            System.out.println("Method 3 (Recursive):    " + isPalindromeRecursive(test));
            System.out.println("Method 4 (Alphanumeric): " + isPalindromeAlphanumeric(test));
            System.out.println("------------------------------------------------------------");
        }
    }
}
```
