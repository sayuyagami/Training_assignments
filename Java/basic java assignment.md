Core Java | Assignment 1
------------------------------------------------------------------------------------------------------------------

1.Find out if the given number is an Armstrong number. Logic-if 153 is the Supplied value, then 1³+5^3+3^3=1+125+27=153.
This is the same as supplied value hence it is an Armstrong number.

'''
import java.util.Scanner;
public class Armstrong {

    public static void main(String[] args) {

        int temp, originalnum, remainder, result = 0;

        System.out.println("Enter 3 Digit Number");
        Scanner scanner = new Scanner(System.in);
        originalnum = scanner.nextInt();
        scanner.close();
        temp = originalnum;
       
        while (temp != 0)
        {
            remainder = temp % 10;
            result += Math.pow(remainder, 3);
            temp /= 10;
        }

        if(result == originalnum)
            System.out.println(originalnum + " is an Armstrong number.");
        else
            System.out.println(originalnum + " is not an Armstrong number.");
    }
}
'''

Output

Enter 3 Digit Number
153
153 is an Armstrong number.

2. Find out all the Armstrong numbers falling in the range of 100-999

import java.util.Scanner;

public class Armstrong {

    public static void main(String[] args) {

        int temp, lowlimit,uplimit,i, remainder, result;

        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter lower limit");
        lowlimit = scanner.nextInt();
        System.out.println("Enter upper limit");
        uplimit = scanner.nextInt();
        scanner.close();
        for(i=lowlimit;i<=uplimit;i++) {
        temp=i;
        result=0;
        while (temp != 0)
        {
            remainder = temp % 10;
            result += Math.pow(remainder, 3);
            temp /= 10;
            
        }
       
        if(result == i) {
	System.out.println(i+" is a Armstrong number");
        }
       }
    }
}

Output

Enter lower limit
100
Enter upper limit
999
153 is a Armstrong number
370 is a Armstrong number
371 is a Armstrong number
407 is a Armstrong number


3. Find out the simple as well as the compound interest of supplied

import java.util.Scanner;
public class Interest
{
public static void main(String args[ ])
{
double principal, rate, time, simp,comp;
System.out.println("Enter amount:");
Scanner obj=new Scanner(System. in);
principal=obj.nextDouble();
System. out. println("Enter the No.of years:");
time=obj.nextDouble();
System.out. println("Enter the Rate of interest");
rate=obj.nextDouble();
obj.close();
//Formula for simple interest
simp=(principal * time * rate)/100;

//Formula for compound interest
comp=principal * Math.pow(1.0+rate/100.0,time) - principal;

//display only 2 digits after decimal
System.out.println("Simple Interest = "+String.format("%.2f", simp) );
System.out. println("Compound Interest = "+String.format("%.2f", comp));
}
}

Output

Enter amount:
1000
Enter the No.of years:
4
Enter the Rate of interest
10
Simple Interest = 400.00
Compound Interest = 464.10

4. Supply marks of three subject and declare the result, result declaration is based on below conditions 
Condition 1: All subjects marks is greater than 60 is Passed
Condition 2: Any two subjects marks are greater than 60 is Promoted
Condition 3: Any one subject mark is greater than 60 or all subjects marks less than 60 is failed

import java.util.Scanner;

public class Result {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int maths,java,english,result;
		Scanner sc = new Scanner(System. in);
		System.out.println("Enter Maths marks:");
		maths=sc.nextInt();
		System.out.println("Enter java marks:");
		java=sc.nextInt();
		System.out.println("Enter english marks:");
		english=sc.nextInt();
		
		if(maths>=60 && java>=60 && english>=60) {
			System.out.println("Result : Passed!!");
		}else if(maths>=60 && java>=60 || java>=60 && english>=60 || maths>=60 && english>=60) {
			System.out.println("Result : Promoted:)");
		}else {
			System.out.println("Result : Failed:(");
		}	
	}
}

Output

Enter Maths marks:
75
Enter java marks:
59
Enter english marks:
45
Result : Failed:(


5. Calculate the income tax on the basis of following table.

import java.util.Scanner;

class Income
{
	public static void main(String args[])
	{
	double tax=0,inc;
	Scanner sc=new Scanner(System.in);
	System.out.println("Enter income ");
	inc=sc.nextDouble();
	if(inc<=180000) {
		tax=0;
	}else if(inc<=300000) {
		tax=(inc/100)*10;
	}else if(inc<=500000) {
		tax=(inc/100)*20;
	}else if(inc<=1000000) {
		tax=(inc/100)*30;
	}
	System.out.println("Income tax amount is "+tax);
	}
}

Output

Enter income 
510000
Income tax amount is 153000.0

6. Consider a CUI based application, where you are asking a user to enter his Login name and password, 
after entering the valid user-id and password it will print the message "Welcome" along with user name. 
As per the validation is concerned, the program should keep a track of login attempts. 
After three attempts a message should be flashed saying "Contact Admin" and the program should terminate.

import java.util.Scanner;

public class Login {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		String unm="Hima";
		String pwd="haha123";
		String usernm,passwd;
		int cnt;
		Scanner sc = new Scanner(System.in);
		for(cnt=1;cnt<=3;cnt++) {
		System.out.println("Enter username :");
		usernm=sc.nextLine();
		System.out.println("Enter password :");
		passwd=sc.nextLine();
		
		if(usernm.equals(unm) && passwd.equals(pwd)) {
			System.out.println("Welcome "+usernm);
		}else if(cnt==3) {
			System.out.println("Sorry "+usernm+"!! Contact Admin");
		}
		else {
			System.out.println("Invalid credentials.Try Again!!Remaining Attempts "+(3-cnt));
		}
		}
		
	}

}

Output

Enter username :
haha
Enter password :
123
Invalid credentials.Try Again!!Remaining Attempts 2
Enter username :
hey
Enter password :
hey123
Invalid credentials.Try Again!!Remaining Attempts 1
Enter username :
Hima
Enter password :
haha22
Sorry Hima!! Contact Admin

7. There is an Array which is of the size 15, which may or may not be sorted. You should write a program to accept a number and search if it in contained in the array
Value to be search is 19

import java.util.Arrays;
import java.util.Scanner;

public class ArraySearch {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int a[]= {5,12,14,6,78,19,1,23,26,35,37,7,52,86,47};
		int searchNum,cnt=0;
		
		System.out.println("Display array :");
		System.out.println(Arrays.toString(a));
		Scanner sc = new Scanner(System.in);
		System.out.println("Value to be searched :");
		searchNum=sc.nextInt();
		for(int i=0;i<a.length;i++) {
			if(a[i]==searchNum) {
				cnt=0;
				System.out.println(searchNum+" Number Found");
				break;
			}else {
				cnt=cnt+1;
				if(i==a.length-1 && cnt>0)
					System.out.println("Number not Found");
					
			}
		}
	}

}

Output

Display array :
[5, 12, 14, 6, 78, 19, 1, 23, 26, 35, 37, 7, 52, 86, 47]
Value to be searched :
19
19 Number Found

8. Using the above table write method apply sorting using Bubble Sort


public class Bubblesort {

	 public static void main(String[] args) {  
         int a[] ={3,60,35,2,45,320,5};
         int temp;
          
         System.out.println("Array Before Bubble Sort");  
         for(int i=0; i < a.length; i++){  
                 System.out.print(a[i] + " ");  
         }  
         System.out.println();  
           
         //sorting array elements using bubble sort
         for(int j=0;j<a.length;j++) {
        	 for(int k=1;k<a.length-j;k++) {
        		 if(a[k-1]>a[k]) {
        			 temp=a[k-1];
        			 a[k-1]=a[k];
        			 a[k]=temp;
        		 }
        	 }
         }
          
         System.out.println("Array After Bubble Sort");  
         for(int i=0; i < a.length; i++){  
                 System.out.print(a[i] + " ");  
         }  

     }  
}  

Output

Array Before Bubble Sort
3 60 35 2 45 320 5 
Array After Bubble Sort
2 3 5 35 45 60 320 

9. Accept the marks of three students for the subject say A, B, C. Find the total scored and the average in all the subjects.
Also Find the Total and Average scored by students in each respective Subject.

import java.util.Scanner;

public class ScoreAvg {

	public static void main(String[] args) {
		
		//declare and initialize variables
		Scanner scanner = new Scanner(System.in);
		double a[][] = new double[3][3];
		double sum = 0; 
		
		System.out.println("Enter the marks ");
		
		//input array
		for (int i=0;i<3;i++) 
		{
			System.out.println("Enter the marks for student "+(i+1));
			for (int j=0;j<3;j++) 
			{
				a[i][j]=scanner.nextInt() ;
			}
		}
		
		//adding marks
		for (int i=0;i<3;i++) 
		{
			for (int j=0;j<3;j++) 
			{
					sum += a[i][j];
			}
		}
		
		//average all marks
		System. out. println("Total marks in all subjects is: "+ sum);
		System. out. println("Average marks in all subjects is: "+ sum/9) ;
		
		sum = 0;
		
		//student individual marks
		for (int i=0;i<3;i++) 
		{
			sum=0;
			for (int j=0;j<3;j++) 
			{
					sum += a[i][j];
			}
		
			
			System.out.println();
			System. out. println("Total marks for student "+ (i+1) +" of each subject is: "+ sum) ;
			System. out. println("Average marks for student "+ (i+1) +" of each subject is: "+ sum/3);
			System.out.println();
			
			sum = 0;
		}
	}
}

Output

Enter the marks 
Enter the marks for student 1
50
75
80
Enter the marks for student 2
95
85
78
Enter the marks for student 3
77
89
76
Total marks in all subjects is: 705.0
Average marks in all subjects is: 78.33333333333333

Total marks for student 1 of each subject is: 205.0
Average marks for student 1 of each subject is: 68.33333333333333


Total marks for student 2 of each subject is: 258.0
Average marks for student 2 of each subject is: 86.0


Total marks for student 3 of each subject is: 242.0
Average marks for student 3 of each subject is: 80.66666666666667

