# Assignments on Exception Handling | Assignment 4
------------------------------------------------------------------------------
> 1.Write an application that accepts two numbers, divides the first number with the second number and display the result. Hint: You need to handle ArithmeticException which is thrown when there is an attempt to divide a number by zero.
```sh
import java.util.Scanner;

public class Arthimetic {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
	   int a,b;
	   Scanner sc=new Scanner(System.in);
	   System.out.println("Enter value for a : ");
	   a=sc.nextInt();
	   System.out.println("Enter value for b : ");
	   b=sc.nextInt();
	   
	   try {
		   System.out.println(a/b);
	   }catch(ArithmeticException e){
		   System.out.println("Error raised when divided by zero "+ e);
	   }
	}
}
```
#### Output
```sh
Enter value for a : 
10
Enter value for b : 
0
Error raised when divided by zero java.lang.ArithmeticException: / by zero
```
> 2.Carrying forward with the above problem, handle ArithmeticException by raising Unsupported OperationException as a solution.
```sh
import java.util.Scanner;
public class Arthimetic {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
	   int a,b;
	   Scanner sc=new Scanner(System.in);
	   System.out.println("Enter value for a : ");
	   a=sc.nextInt();
	   System.out.println("Enter value for b : ");
	   b=sc.nextInt();
	   
	   try {
		   System.out.println(a/b);
		   throw new UnsupportedOperationException("Number not dividable by zero");
		   
	   }catch(ArithmeticException e){
		   System.out.println("Error raised when divided by zero "+ e);
		   throw e;
	   }
	}
}
```
#### Output
```sh
Enter value for a : 
37
Enter value for b : 
0
Error raised when divided by zero java.lang.ArithmeticException: / by zero
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at Arthimetic.main(Arthimetic.java:15)
```
> 3.Write an application to perform withdraw functionality on a SavingAccount object. Point to
note:
a. Ralse InsufficientBalanceException if you are trying to withdraw more than balance
or when you balance is zero. E.g. if you balance is 2000 and If you are trying to
withdraw 2100 or if you balance is O and you are trying to withdraw positive value.
b. Raise illegalBankTransactionException if you are trying to withdraw a negative value
from your balance. E.g. If you try to withdraw a negative value savingAcc.withdraw-
1000):
Note: SavingAccount
-- long id
--double balance
--double withdraw(double amount)
--double deposit(double amount)
```sh
import java.util.Scanner;
public class SavingAccount{

	public static void main(String[] args) {
		// TODO Auto-generated method stub  
		
		int id[]= {1006,1155,1137};
		double amt[]= {500.0,1000.0,5000.0}; 
		
		Scanner sc = new Scanner(System.in); 
		 char ch;
		 int withd,depid;
		 double withdamt,val=0,depamt;
	        do {  
	            System.out.println("\n ***Welcom to Savings Account Application***");  
	            System.out.println("a. Withdraw \n b. Deposit \n  c.Exit ");  
	            System.out.println("Enter your choice: ");  
	            ch = sc.next().charAt(0);  
	                switch (ch) {  
	                    case 'a':  
	                    	System.out.println("\n ***Withdraw Module***");
	                    	System.out.println("Enter your ID: ");
	                    	withd=sc.nextInt();
	                    	for(int i=0;i<id.length;i++) {
	                    		if(withd==id[i]) {
	                    			System.out.println("Your Balance : "+amt[i]);
	                    			System.out.println("Enter your withdrawal amount : ");
	                    			withdamt=sc.nextDouble();
	                    			if(withdamt <= amt[i] && withdamt > 0) {
	                    				System.out.println("Withdraw done Successfully");
	                    				val=amt[i]-withdamt;
	                    				System.out.println("Your Balance : "+val);
	                    			}
	                    			try {
                    					if(withdamt > amt[i]) {
                    						throw new Exception("InsufficientBalanceException");
                    					}
                    					if(withdamt < 0) {
                    						throw new Exception("IllegalBankTransactionException");
	                    				}
                    				}catch(Exception e){
                    					System.out.println(e.getMessage());
                    					
                    				}
	                    			break;
	                    		}else {
	                    			if(i==(id.length-1)) {
		                    			System.out.println("Please enter valid ID");
		                    			}
	                    		}
	                    	}
	         	            break;
	                    case 'b':  
	                    	System.out.println("\n ***Deposit Module***");
	                    	System.out.println("Enter your ID: ");
	                    	depid=sc.nextInt();
	                    	for(int i=0;i<id.length;i++) {
	                    		if(depid==id[i]) {
	                    			System.out.println("Your Balance : "+amt[i]);
	                    			System.out.println("Enter your deposit amount : ");
	                    			depamt=sc.nextDouble();
	                    			
	                    			System.out.println("Deposit done Successfully");
	                    			val=amt[i]+depamt;
	                    			System.out.println("Your Balance : "+val);
	                    			break;
	                    		}else {
	                    			if(i==(id.length-1)) {
	                    			System.out.println("Please enter valid ID");
	                    			}
	                    		}
	                    	}
	         	            break;
	                    case 'c':  
	                        System.out.println("See you soon...Have a great day!!");  
	                        break;
	                }  
	        }  
	        while (ch != (int)'c');  
	        
	}
}
```
#### Output
```sh
 ***Welcom to Savings Account Application***
a. Withdraw 
 b. Deposit 
  c.Exit 
Enter your choice: 
a

 ***Withdraw Module***
Enter your ID: 
1006
Your Balance : 500.0
Enter your withdrawal amount : 
-144
IllegalBankTransactionException

 ***Welcom to Savings Account Application***
a. Withdraw 
 b. Deposit 
  c.Exit 
Enter your choice: 
a

 ***Withdraw Module***
Enter your ID: 
1155
Your Balance : 1000.0
Enter your withdrawal amount : 
2500
InsufficientBalanceException

 ***Welcom to Savings Account Application***
a. Withdraw 
 b. Deposit 
  c.Exit 
Enter your choice: 
b

 ***Deposit Module***
Enter your ID: 
1137
Your Balance : 5000.0
Enter your deposit amount : 
1000
Deposit done Successfully
Your Balance : 6000.0

 ***Welcom to Savings Account Application***
a. Withdraw 
 b. Deposit 
  c.Exit 
Enter your choice: 
c
See you soon...Have a great day!!
```
