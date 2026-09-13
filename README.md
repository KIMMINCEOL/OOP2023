# OOP2023
### Homework1
```java
public class Homework1 {

	public static void main(String []args){

		int i, j;

		for(i=0; i<10; i++) {

			  for(j=0; j<=i; j++) {

			    System.out.print(" ");

			  }

			  for(; j<=10; j++) {

			    System.out.print("#");

			  }

			  System.out.println();

			}

		for(i=0; i<10; i++) {

			  for(j=0; j<=10-i; j++) {

			    System.out.print(" ");

			  }

			  for(; j<=10; j++) {

			    System.out.print("#");

			  }

			  System.out.println();

			}

		for(i=0; i<10; i++) {

			  for(j=0; j<=10-i; j++) {

			    System.out.print("#");

			  }

			  for(; j<=10; j++) {

			    System.out.print("");

			  }

			  System.out.println();

			}

		for(i=0; i<10; i++) {

			  for(j=0; j<=10-i; j++) {

			    System.out.print("");

			  }

			  for(; j<=10; j++) {

			    System.out.print("#");

			  }

			  System.out.println();

			}

	}

}
```
![Alt homework1](./images/homework1.png)

### Homework2
```java
public class homework2 {
    public static void main(String[] args) {
        int n = 20; 
        
        long first = 1;
        long second = 1;
        
        for (int i = 0; i < n; i++) {
            System.out.print(first + " ");

            long next = first + second;
            first = second;
            second = next;
        }
    }
}
```
![Alt homework2](./images/homework2.png)

### Homework3
```java
public class Homework3 {
    public static void main(String[] args) {
        int n = 20; 
        
        long first = 1;
        long second = 1;
        
        for (int i = 1; i <= n; i++) {
            if (i == 1) {
            } else {
                long next = first + second;
                double ratio = (double) second / first;
                
                System.out.printf("%d / %d\t\t%.10f\n", second, first, ratio);
                
                first = second;
                second = next;
            }
        }
    }
}
```
![Alt homework3](./images/homework3.png)

### Homework4
```java
public class Homework4 {
    public static void main(String[] args) {
        for (int i = 1; i <= 9; i++) {
            System.out.println("=== " + i + " ===");
            for (int j = 1; j <= 9; j++) {
                System.out.printf("%d x %d = %d\n", i, j, i * j);
            }
            System.out.println();
        }
    }
}
```
![Alt homework4](./images/homework4.png)

### Homework5
```java
public class homework5 {
    public static void main(String[] args) {
        String fountain = "pi = ";
        int sign = 1;

        // 분모
        for (int i = 1; i <= 30; i += 2) {
            if (i == 1) {
               fountain += "4/1";
            } else {
                // sign이 양수면 +, 음수면 - 기호 붙이기
                if (sign > 0) {
                    fountain += " + 4/" + i;
                } else {
                    fountain += " - 4/" + i;
                }
            }
            sign = -sign; // 다음 항을 위해 부호 반전
        }

        System.out.println(fountain);
    }
}
```
![Alt homework5](./images/homework5.png)

### Homework6
```java
public class homework6 {
    public static void main(String[] args) {
        int n = 7; // 출력할 행의 수 (0승부터 6승까지)
        int[][] binomial = new int[n][];

        // 1. 이항계수 배열 생성 및 파스칼의 삼각형 계산
        for (int i = 0; i < n; i++) {
            binomial[i] = new int[i + 1]; 
            binomial[i][0] = 1;         
            binomial[i][i] = 1;         

          
            for (int j = 1; j < i; j++) {
                binomial[i][j] = binomial[i - 1][j - 1] + binomial[i - 1][j];
            }
        }

        // 2. 파스칼의 삼각형 이항계수 출력
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <= i; j++) {
                System.out.print(binomial[i][j] + " ");
            }
            System.out.println();
        }

        System.out.println(); 

       
        for (int i = 2; i <= 4; i++) {
            System.out.print("(a+b)^" + i + "=");

            for (int j = 0; j <= i; j++) {
                int coeff = binomial[i][j]; 
                int aExp = i - j;          
                int bExp = j;                

              
                if (j > 0) {
                    System.out.print("+");
                }

             
                if (coeff > 1) {
                    System.out.print(coeff);
                }

              
                if (aExp == 1) {
                    System.out.print("a");
                } else if (aExp > 1) {
                    System.out.print("a^" + aExp);
                }

              
                if (bExp == 1) {
                    System.out.print("b");
                } else if (bExp > 1) {
                    System.out.print("b^" + bExp);
                }
            }
            System.out.println();
        }
    }
}
```
![Alt homework6](./images/homework6.png)

### Homework7
```java
public class homework7 {
    public static void main(String[] args) {
        int data[] = new int[20];

        // 1. 랜덤
        for (int i = 0; i < 20; i++) {
            data[i] = (int) (Math.random() * 100);
        }

        // 2. 선택 정렬 전
        System.out.println("before");
        for (int i = 0; i < 20; i++) {
            System.out.print(data[i] + " ");
        }
        System.out.println("\n");

        // 3. 선택 정렬 알고리즘
        for (int i = 0; i < data.length - 1; i++) {
            int minimum = i; // 최솟값의 위치 기록

            for (int j = i + 1; j < data.length; j++) {
                if (data[j] < data[minimum]) {
                    minimum = j; // 더 작은 값을 찾으면 인덱스 갱신
                }
            }

            // 최솟값과 현재 위치(i)의 값을 교환(Swap)
            int temp = data[minimum];
            data[minimum] = data[i];
            data[i] = temp;
        }

        // 4. 정렬 후 배열 출력
        System.out.println("after");
        for (int i = 0; i < 20; i++) {
            System.out.print(data[i] + " ");
        }
        System.out.println();
    }
}


```
![Alt homework7](./images/homework7.png)
