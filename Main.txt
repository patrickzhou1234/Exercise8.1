import java.lang.Math;
import java.util.ArrayList;

public class Main {
    public static void saveMinimum(double[][] arr, ArrayList<Double> minLs) {
        int i, j;
        double tmpmin;
        for (i = 0; i < arr.length; i++) {
            tmpmin = Double.MAX_VALUE;
            for (j = 0; j < arr[0].length; j++) {
                tmpmin = Math.min(tmpmin, arr[i][j]);
            }
            minLs.add(tmpmin);
        }
    }

    public static void saveMinimumEnhanced(double[][] arr, ArrayList<Double> minLs) {
        double tmpmin;
        for (double[] i : arr) {
            tmpmin = Double.MAX_VALUE;
            for (double j : i) {
                tmpmin = Math.min(tmpmin, j);
            }
            minLs.add(tmpmin);
        }
    }

    public static void saveMaximum(double[][] arr, ArrayList<Double> maxLs) {
        int i, j;
        double tmpmax;
        for (i = 0; i < arr[0].length; i++) {
            tmpmax = Double.MIN_VALUE;
            for (j = 0; j < arr.length; j++) {
                tmpmax = Math.max(tmpmax, arr[j][i]);
            }
            maxLs.add(tmpmax);
        }
    }

    public static void saveMaximumEnhanced(double[][] arr, ArrayList<Double> maxLs) {
        int i;
        double tmpmax;
        for (i = 0; i < arr[0].length; i++) {
            tmpmax = Double.MIN_VALUE;
            for (double[] j : arr) {
                tmpmax = Math.max(tmpmax, j[i]);
            }
            maxLs.add(tmpmax);
        }
    }

    public static double findTotal(double[][] arr) {
        int i, j;
        double sum = 0.0;
        for (i = 0; i < arr.length; i++) {
            for (j = 0; j < arr[0].length; j++) {
                sum += arr[i][j];
            }
        }
        return sum;
    }

    public static double findTotalEnhanced(double[][] arr) {
        double sum = 0.0;
        for (double[] i : arr) {
            for (double j : i) {
                sum += j;
            }
        }
        return sum;
    }

    public static void printLs(ArrayList<Double> ls) {
        int i;
        for (i = 0; i < ls.size(); i++) {
            System.out.print(ls.get(i) + " ");
        }
        System.out.println();
    }

    public static void printLsEnhanced(ArrayList<Double> ls) {
        for (double i : ls) {
            System.out.print(i + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        // initialization of arrays/arraylists.
        ArrayList<Double> minLs = new ArrayList<Double>(), maxLs = new ArrayList<Double>();
        double arr[][] = {
                { -2.0, 3.0, 0.0, 8.0, 10.0 },
                { 0.0, -4.0, 3.0, 1.0, 2.0 },
                { 1.0, 2.0, 3.0, 8.0, -6.0 },
                { -4.0, 1.0, 4.0, 6.0, 82.0 }
        };
        // normal implementation
        saveMinimum(arr, minLs);
        System.out.print("Minimum values for each row: ");
        printLs(minLs);
        saveMaximum(arr, maxLs);
        System.out.print("Maximum values for each column: ");
        printLs(maxLs);
        System.out.print("Total value: " + findTotal(arr));
        // clear arraylist contents.
        maxLs.clear();
        minLs.clear();
        // enhanced for loop part
        System.out.print("\nEnhanced for loop results: \n");
        saveMinimumEnhanced(arr, minLs);
        System.out.print("Minimum values for each row: ");
        printLsEnhanced(minLs);
        saveMaximumEnhanced(arr, maxLs);
        System.out.print("Maximum values for each column: ");
        printLsEnhanced(maxLs);
        System.out.print("Total value: " + findTotalEnhanced(arr));
    }
}