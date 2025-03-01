```java
import java.util.Scanner;

public class Solution {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[][] matrix = new int[n][n];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                matrix[i][j] = sc.nextInt();
            }
        }

        for (int i = 0; i < n; i++) {
            int temp = matrix[i][i];
            matrix[i][i] = matrix[i][n - i - 1];
            matrix[i][n - i - 1] = temp;
        }

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }

        sc.close();
    }
}
```

- Selection Sort

```java
import java.util.Scanner;

public class Solution {

    public static void printArray(int[] array) {
        for (int i : array) {
            System.out.print(i + " ");
        }
        System.out.println();
    }

    public static void selectionSort(int[] array) {
        int n = array.length;
        for (int i = 0; i < n - 1; i++) {
            int minIndex = i;
            for (int j = i + 1; j < n; j++) {
                if (array[j] < array[minIndex]) {
                    minIndex = j;
                }
            }
            int temp = array[minIndex];
            array[minIndex] = array[i];
            array[i] = temp;
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] data = new int[n];
        for (int i = 0; i < n; i++) {
            data[i] = scanner.nextInt();
        }
        selectionSort(data);
        printArray(data);
    }
}
```

- **Insertion Sort**

```java
import java.util.Scanner;

public class Solution {

    public static void insertionSort(int[] array) {
        for (int i = 1; i < array.length; i++) {
            int key = array[i];
            int j = i - 1;
            while (j >= 0 && key < array[j]) {
                array[j + 1] = array[j];
                j--;
            }
            array[j + 1] = key;
        }
    }

    public static void printArray(int[] array) {
        for (int i : array) {
            System.out.print(i + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] array = new int[n];
        for (int i = 0; i < n; i++) {
            array[i] = scanner.nextInt();
        }
        insertionSort(array);
        printArray(array);
    }
}
```

- **Bubble Sort**

```java
import java.util.Scanner;

public class Solution {

    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int size = scanner.nextInt();
        int[] data = new int[size];
        for (int i = 0; i < size; i++) {
            data[i] = scanner.nextInt();
        }
        bubbleSort(data);
        for (int i = 0; i < data.length; i++) {
            System.out.print(data[i] + " ");
        }
    }
}
```

- **Merge Sort**

```java
import java.util.Scanner;

public class Solution {

    public static void mergeSort(int[] array) {
        if (array.length > 1) {
            int mid = array.length / 2;
            int[] L = new int[mid];
            int[] R = new int[array.length - mid];

            System.arraycopy(array, 0, L, 0, mid);
            System.arraycopy(array, mid, R, 0, array.length - mid);

            mergeSort(L);
            mergeSort(R);

            int i = 0, j = 0, k = 0;
            while (i < L.length && j < R.length) {
                if (L[i] <= R[j]) {
                    array[k] = L[i];
                    i++;
                } else {
                    array[k] = R[j];
                    j++;
                }
                k++;
            }

            while (i < L.length) {
                array[k] = L[i];
                i++;
                k++;
            }

            while (j < R.length) {
                array[k] = R[j];
                j++;
                k++;
            }
        }
    }

    public static void printList(int[] array) {
        for (int i = 0; i < array.length; i++) {
            System.out.print(array[i] + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int size = scanner.nextInt();
        int[] data = new int[size];
        for (int i = 0; i < size; i++) {
            data[i] = scanner.nextInt();
        }

        mergeSort(data);
        printList(data);
    }
}
```

- **Quick Sort**

```java
import java.util.Scanner;

public class Solution {

    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pi = partition(arr, low, high);
            quickSort(arr, low, pi - 1);
            quickSort(arr, pi + 1, high);
        }
    }

    public static int partition(int[] arr, int low, int high) {
        int pivot = arr[high];
        int i = low - 1;
        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;
        return i + 1;
    }

    public static void printArray(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }

        quickSort(arr, 0, n - 1);
        printArray(arr);
    }
}
```

- **Prefix Sum**

```java
import java.util.Scanner;

public class PrefixSum {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        int N = scanner.nextInt();
        int[] arr = new int[N];
        for (int i = 0; i < N; i++) {
            arr[i] = scanner.nextInt();
        }

        int[] prefixSum = new int[N];
        prefixSum[0] = arr[0];
        for (int i = 1; i < N; i++) {
            prefixSum[i] = arr[i] + prefixSum[i - 1];
        }

        for (int i = 0; i < N; i++) {
            System.out.print(prefixSum[i] + " ");
        }
        System.out.println();
    }
}
```

- **Suffix Sum**

```java
import java.util.Scanner;

public class SuffixSum {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        int N = scanner.nextInt();
        int[] arr = new int[N];
        for (int i = 0; i < N; i++) {
            arr[i] = scanner.nextInt();
        }

        int[] suffixSum = new int[N];
        suffixSum[N - 1] = arr[N - 1];
        for (int i = N - 2; i >= 0; i--) {
            suffixSum[i] = arr[i] + suffixSum[i + 1];
        }

        for (int i = 0; i < N; i++) {
            System.out.print(suffixSum[i] + " ");
        }
        System.out.println();
    }
}
```

- **Left Rotate Array**

```java
import java.util.Scanner;

public class LeftRotation {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int d = scanner.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        d = d % n;
        int[] rotatedArr = new int[n];
        int index = 0;
        // Copy elements from index d to n-1
        for (int i = d; i < n; i++) {
            rotatedArr[index++] = arr[i];
        }
        // Copy elements from index 0 to d-1
        for (int i = 0; i < d; i++) {
            rotatedArr[index++] = arr[i];
        }
        // Print rotated array
        for (int i = 0; i < n; i++) {
            System.out.print(rotatedArr[i] + " ");
        }
        System.out.println();
    }
}
```

- **Right Rotate Array**

```java
import java.util.Scanner;

public class RightRotation {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int d = scanner.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }
        d = d % n;
        int[] rotatedArr = new int[n];
        int index = 0;
        // Copy the last d elements to the beginning of rotatedArr
        for (int i = n - d; i < n; i++) {
            rotatedArr[index++] = arr[i];
        }
        // Copy the first n-d elements to rotatedArr after the d elements
        for (int i = 0; i < n - d; i++) {
            rotatedArr[index++] = arr[i];
        }
        // Print rotated array
        for (int i = 0; i < n; i++) {
            System.out.print(rotatedArr[i] + " ");
        }
        System.out.println();
    }
}
```

- **Remove First Occurrence**

```java
import java.util.Scanner;

public class RemoveFirstOccurrence {

    public static String removeFirst(String s, String w) {
        int wordLen = w.length();
        int firstOccurrence = -1;

        for (int i = 0; i <= s.length() - wordLen; i++) {
            if (s.substring(i, i + wordLen).equals(w)) {
                firstOccurrence = i;
                break;
            }
        }

        if (firstOccurrence != -1) {
            return s.substring(0, firstOccurrence) + s.substring(firstOccurrence + wordLen);
        }
        return s;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.nextLine().strip();
        String w = scanner.nextLine().strip();

        System.out.println(removeFirst(s, w));
    }
}
```

- **Remove Last Occurrence**

```java
import java.util.Scanner;

public class RemoveLastOccurrence {

    public static String removeLast(String s, String w) {
        int wordLen = w.length();
        int lastOccurrence = -1;

        for (int i = 0; i <= s.length() - wordLen; i++) {
            if (s.substring(i, i + wordLen).equals(w)) {
                lastOccurrence = i;
            }
        }

        if (lastOccurrence != -1) {
            return s.substring(0, lastOccurrence) + s.substring(lastOccurrence + wordLen);
        }
        return s;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.nextLine().strip();
        String w = scanner.nextLine().strip();

        System.out.println(removeLast(s, w));
    }
}
```

- **Valid Parenthesis**

```java
import java.util.Scanner;
import java.util.Stack;

public class ValidBrackets {

    public static boolean isValidBrackets(String s) {
        java.util.Map<Character, Character> brackets = new java.util.HashMap<>();
        brackets.put('(', ')');
        brackets.put('{', '}');
        brackets.put('[', ']');
        Stack<Character> stack = new Stack<>();

        for (char charAt : s.toCharArray()) {
            if (brackets.containsKey(charAt)) {
                stack.push(charAt);
            } else if (brackets.containsValue(charAt)) {
                if (stack.isEmpty() || brackets.get(stack.pop()) != charAt) {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.nextLine().strip();

        boolean result = isValidBrackets(s);
        System.out.println(result ? "true" : "false");
    }
}
```

- **Character Count**

```java
import java.util.Scanner;

public class CountCharacters {

    public static void countCharacters(String s) {
        int alphabetCount = 0;
        int digitCount = 0;
        int specialCount = 0;

        for (char c : s.toCharArray()) {
            if (Character.isAlphabetic(c)) {
                alphabetCount++;
            } else if (Character.isDigit(c)) {
                digitCount++;
            } else {
                specialCount++;
            }
        }

        System.out.println(alphabetCount + " " + digitCount + " " + specialCount);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.nextLine();

        if (s.length() >= 1 && s.length() <= 1000) {
            countCharacters(s);
        }
    }
}
```

- **String Compression**

```java
import java.util.Scanner;

public class StringCompression {

    public static String compressString(String s) {
        if (s.isEmpty()) {
            return "";
        }

        StringBuilder result = new StringBuilder();
        int count = 1;

        for (int i = 1; i < s.length(); i++) {
            if (s.charAt(i) == s.charAt(i - 1)) {
                count++;
            } else {
                result.append(s.charAt(i - 1)).append(count);
                count = 1;
            }
        }

        result.append(s.charAt(s.length() - 1)).append(count);
        String compressedString = result.toString();

        return compressedString.length() < s.length() ? compressedString : s;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.nextLine().strip();

        System.out.println(compressString(s));
    }
}
```

- **Remove Duplicates and Print Array without Duplicates**

```java
import java.util.Scanner;
import java.util.ArrayList;
import java.util.HashSet;

public class RemoveDuplicates {

    public static ArrayList<Integer> removeDuplicates(int[] arr) {
        HashSet<Integer> seen = new HashSet<>();
        ArrayList<Integer> result = new ArrayList<>();
        for (int num : arr) {
            if (!seen.contains(num)) {
                seen.add(num);
                result.add(num);
            }
        }
        return result;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }

        ArrayList<Integer> result = removeDuplicates(arr);
        for (int num : result) {
            System.out.print(num + " ");
        }
        System.out.println();
    }
}
```

- **Second Largest Number**

```java
import java.util.Scanner;

public class SecondLargest {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int[] arr = new int[n];

        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }

        int first = Integer.MIN_VALUE;
        int second = Integer.MIN_VALUE;

        for (int num : arr) {
            if (num > first) {
                second = first;
                first = num;
            } else if (num > second && num < first) {
                second = num;
            }
        }

        System.out.println(second);
    }
}
```

- **Character Frequency Analysis**

```java
import java.util.Scanner;
import java.util.HashMap;
import java.util.ArrayList;
import java.util.Collections;

public class CharacterFrequency {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.nextLine().strip();

        HashMap<Character, Integer> freq = new HashMap<>();
        for (char c : s.toCharArray()) {
            freq.put(c, freq.getOrDefault(c, 0) + 1);
        }

        int maxFreq = Collections.max(freq.values());
        int minFreq = Collections.min(freq.values());

        ArrayList<Character> maxChars = new ArrayList<>();
        ArrayList<Character> minChars = new ArrayList<>();

        for (char c : freq.keySet()) {
            if (freq.get(c) == maxFreq) {
                maxChars.add(c);
            }
            if (freq.get(c) == minFreq) {
                minChars.add(c);
            }
        }

        Collections.sort(maxChars);
        Collections.sort(minChars);

        for (char c : maxChars) {
            System.out.print(c + " ");
        }
        System.out.println(maxFreq);

        for (char c : minChars) {
            System.out.print(c + " ");
        }
        System.out.println(minFreq);
    }
}
```