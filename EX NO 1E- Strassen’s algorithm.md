
# EX 1E Integer Multiplication using Divide and Conquer Approach(Strassen’s algorithm).
## DATE: 25/05/2026
## AIM:
To write a Java program to for given constraints.
You are given two square matrices A and B of size n × n (where n is a power of 2). Your task is to compute their matrix product using Strassen’s Matrix Multiplication algorithm and return the resulting matrix.

Unlike traditional matrix multiplication which takes O(n3)O(n^3)O(n3) time, Strassen’s algorithm improves this by reducing the number of recursive multiplications from 8 to 7, achieving approximately O(n2.81)O(n^{2.81})O(n2.81) complexity.
## Algorithm

1.Start the program and read the size of the square matrices n (must be a power of 2) and the elements of matrices A and B.
2.Divide each matrix (A and B) into four equal submatrices:
A11, A12, A21, A22
B11, B12, B21, B22
3.Recursively compute the following seven products using Strassen’s formulas:
M1 = (A11 + A22) × (B11 + B22)
M2 = (A21 + A22) × B11
M3 = A11 × (B12 − B22)
M4 = A22 × (B21 − B11)
M5 = (A11 + A12) × B22
M6 = (A21 − A11) × (B11 + B12)
M7 = (A12 − A22) × (B21 + B22)
4.Combine the results to form the four quadrants of the result matrix C:
C11 = M1 + M4 − M5 + M7
C12 = M3 + M5
C21 = M2 + M4
C22 = M1 − M2 + M3 + M6
5.Merge all quadrants (C11, C12, C21, C22) into a single result matrix C, print the final product matrix, and stop the program.

## Program:
```

Program to implement Reverse a String
Developed by: Dappili Vasavi
Register Number:212223040030
import java.util.Scanner;

public class StrassenMatrix {

   
    static int[][] add(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] + B[i][j];
        return C;
    }

   
    static int[][] subtract(int[][] A, int[][] B) {
        int n = A.length;
        int[][] C = new int[n][n];
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                C[i][j] = A[i][j] - B[i][j];
        return C;
    }

   
    static int[][] strassen(int[][] A, int[][] B) {
        int n=A.length;
        int[][] C=new int[n][n];
        if(n==1){
            C[0][0]=A[0][0]*B[0][0];
            return C;
        }
        int mid=n/2;
        int[][] A11=new int[mid][mid],A12=new int[mid][mid],A21=new int[mid][mid],A22=new int[mid][mid];
        int[][] B11=new int[mid][mid],B12=new int[mid][mid],B21=new int[mid][mid],B22=new int[mid][mid];
        for(int i=0;i<mid;i++)
            for(int j=0;j<mid;j++){
                A11[i][j]=A[i][j];
                A12[i][j]=A[i][j+mid];
                A21[i][j]=A[i+mid][j];
                A22[i][j]=A[i+mid][j+mid];
                B11[i][j]=B[i][j];
                B12[i][j]=B[i][j+mid];
                B21[i][j]=B[i+mid][j];
                B22[i][j]=B[i+mid][j+mid];
            }
        int[][] M1=strassen(add(A11,A22),add(B11,B22));
        int[][] M2=strassen(add(A21,A22),B11);
        int[][] M3=strassen(A11,subtract(B12,B22));
        int[][] M4=strassen(A22,subtract(B21,B11));
        int[][] M5=strassen(add(A11,A12),B22);
        int[][] M6=strassen(subtract(A21,A11),add(B11,B12));
        int[][] M7=strassen(subtract(A12,A22),add(B21,B22));
        int[][] C11=add(subtract(add(M1,M4),M5),M7);
        int[][] C12=add(M3,M5);
        int[][] C21=add(M2,M4);
        int[][] C22=add(subtract(add(M1,M3),M2),M6);
        for(int i=0;i<mid;i++)
            for(int j=0;j<mid;j++){
                C[i][j]=C11[i][j];
                C[i][j+mid]=C12[i][j];
                C[i+mid][j]=C21[i][j];
                C[i+mid][j+mid]=C22[i][j];
            }
            return C;
    }

   
    static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

   
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

       
        int n = sc.nextInt();

        int[][] A = new int[n][n];
        int[][] B = new int[n][n];

       
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                A[i][j] = sc.nextInt();

       
        for (int i = 0; i < n; i++)
            for (int j = 0; j < n; j++)
                B[i][j] = sc.nextInt();

       
        int[][] result = strassen(A, B);

        
        System.out.println("Result of Strassen Matrix Multiplication:");
        printMatrix(result);
    }
}


```

## Output:
<img width="962" height="855" alt="image" src="https://github.com/user-attachments/assets/106e1484-3bf7-47b9-b52c-6a2c95d6a9b7" />



## Result:
The program successfully implemented and the expected output is verified.
