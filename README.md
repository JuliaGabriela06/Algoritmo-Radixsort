# Algoritmo-Radixsort

package testradix;
import java.util.LinkedList;

public class TestRadix {
    private static final int MAX_CHARS = 28;
	
    private static void radixSort(String[] v) {
		LinkedList<String> queues[] = createQueues();
		for (int pos = maxSize(v) - 1; pos >= 0; pos--) {
                    for (String v1 : v) {
                        int q = queueNo(v1, pos);
                        queues[q].add(v1);
                    }
			restore(queues, v);
		}
	}

	private static void restore(Queue<String>[] qs, String[] v) {
		int contv = 0;
        for (Queue<String> q : qs) {
            while (q.size() > 0) {
                v[contv++] = q.remove();
            }
        }
	}

	private static LinkedList<String>[] createQueues() {
		LinkedList<String>[] result = new LinkedList[MAX_CHARS];
		for (int i = 0; i < MAX_CHARS; i++) {
			result[i] = new LinkedList<>();
		}
		return result;
	}

	private static int queueNo(String string, int pos) {
		if (pos >= string.length()) {
			return 0;
		}
		char ch = string.charAt(pos);
		if ((ch >= 'A') && (ch <= 'Z')) {
			return (ch - 'A' + 1);
		}
		else if (ch >= 'a' && ch <= 'z') {
			return ch - 'a' + 1;
		}
		else {
			return 27;
		}
	}

	private static int maxSize(String[] v) {
		int maxValue = v[0].length();

		for (int i = 1; i < v.length; i++) {
			if (maxValue < v[i].length()) {
				maxValue = v[i].length();
			}
		}
		return maxValue;
	}

	public static void printStringArray(String[] arrToPrint) {
        for (String arrToPrint1 : arrToPrint) {
            System.out.print(arrToPrint1 + " ");
        }
		System.out.println();
	}
	
	/**
	 * @param args Array of strings (set of words) to be sorted (ordered) - Must be passed as parameters
	 */
	public static void main(String[] args) {
		System.out.print("Input: ");
		printStringArray(args);
		radixSort(args);
		System.out.print("\nOutput: ");
		printStringArray(args);
	}

    private static void restore(LinkedList<String>[] queues, String[] v) {
        throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
    }

}
