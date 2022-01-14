# Oops Concept | Assignment 2
------------------------------------------------------------------------------
> 1.Write a singletone class. Confirm that singletone class cannot be inherited.
##### Singleton Class
```sh
public class Singleton
{
private static Singleton singleton = null;
	//default constructor
   private Singleton() {}
  public static Singleton getInstance(){
   {
         if (singleton == null)
         {
        	 //object is created only Once in singleton
        	 singleton = new Singleton();
         }else {
        	 return singleton;
         }
         return singleton;
         }
   }
}
```
#### Mainclass to call Singletonclass
```sh
public class MainSingletonclass {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Singleton instance1=Singleton.getInstance();
		System.out.println(instance1);	
	}
}
```
##### Output
```sh
Singleton@6504e3b2
```
> 2.Write a program that describes the hierarchy of an organization. Here we need to write 3 classes
Employee, Manager & Labour where Manager & Labour are the sub classes of the Employee.
Manager has incentive & Labour has over time. Add the functionality to calculate total salary of all the employees. Use polymorphism i.e. method overriding.
```sh
import java.util.Scanner;
class Employee{
float salary = 30000;
}
class Manager extends Employee{
double incentive = 5;
double sal=salary*incentive;
	public void salary() {
		System.out.println("Manager salary is :" +salary);
		System.out.println("Incentive for Manager:" +incentive);
	}
}
class Labour extends Employee{
double overtime = 10;
double sal=salary*overtime;
public void salary() {
	System.out.println("Labour salary is :" +salary);
	System.out.println("Overtime for Labour :" +overtime);
}
}
public class Hierarchy
{
public static void main(String args[]){
Manager m = new Manager();
Labour l = new Labour();
// All objects of inherited classes can access the variable of class Employee
m.salary();
l.salary();

//summing salary
salary(m.sal,l.sal);
}
static void salary(double a, double b) {
	Scanner sc =new Scanner(System.in);
	System.out.println("Enter no. of managers : ");
	int mn = sc.nextInt();
	System.out.println("Enter no. of labours : ");
	int emp = sc.nextInt();
	double addsal=(mn*a)+(emp*b);
	System.out.println("Sum of all employees salary :" +addsal);
}
}
```
##### Output
```sh
Manager salary is :30000.0
Incentive for Manager:5.0
Labour salary is :30000.0
Overtime for Labour :10.0
Enter no. of managers : 
5
Enter no. of labours : 
10
Sum of all employees salary :3750000.0
```
> 3.Write a program to consider saving & current account in the bank. Saving account holder has "Fixed Deposits' whereas Current account holder has cash credit. Apply polymorphism to find out total cash in the bank.
```sh
import java.util.Scanner;

class Savings{
	public void show(int fd) {
		System.out.println("Fixed Deposit "+fd);
	}
}
class Current{
	public void show(int cc) {
		System.out.println("Cash Credit "+cc);
	}
}
class Totalcash{
	public void show(int ssal,int csal) {
		int sum;
		sum=ssal+csal;
		System.out.println("Total Cash : "+sum);
	}
}
public class Bank {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int fdep,ccd;
		Savings s = new Savings();
		Current c = new Current();
		Totalcash tc= new Totalcash();
		
		 Scanner scanner = new Scanner(System.in);
	     System.out.println("Enter Fixed deposit for savings account");
	     fdep = scanner.nextInt();
	    
	     System.out.println("Enter Cash credit for Current account");
	     ccd = scanner.nextInt();
	     s.show(fdep);
	     c.show(ccd);
	     tc.show(fdep,ccd);
	}
}
```
##### Output
```sh
Enter Fixed deposit for savings account
20000
Enter Cash credit for Current account
50000
Fixed Deposit 20000
Cash Credit 50000
Total Cash : 70000
```
> 4.Test the following principles of an abstract class:
• If any class has any of its method abstract then you must declare entire class abstract.
Abstract class cannot be instantiated.
When we extend an abstract class, we must either override all the abstract methods in sub
class or declare subclass as abstract.
• Abstract class cannot be private.
Abstract class cannot be final.
You can declare a class abstract without having any abstract method.
```sh
abstract class AbstractClass { // Entire class declared as abstract
   abstract void display();
}   
   class subabst extends AbstractClass{
    //Overriden abstract method
	  void display() {
      System.out.print("From Abstract Class");
   }
 }

public class Abstract {
   public static void main(String args[]) {
	 //created object for abstract subcalss
      AbstractClass obj = new subabst();
      //calling abstract method
      obj.display();
   }
}
```
##### Output
```sh
From Abstract Class
```
> 5.Write the classes Line, Rectangle, Cube etc. & make the Shape as their base class. Add an abstract draw() method in the class Shape & draw all shapes.
```sh
abstract class Shape{  
abstract void draw();  
}  
  
class Line extends Shape{  
void draw(){System.out.println("drawing Line");}  
}
class Square extends Shape{  
void draw(){System.out.println("drawing square");}  
}
class Rectangle extends Shape{  
void draw(){System.out.println("drawing rectangle");}  
}  
class Circle extends Shape{  
void draw(){System.out.println("drawing circle");}  
}  
  
class Paint{  
public static void main(String args[]){  
Shape s1=new Circle();  
Shape s2=new Rectangle();
Shape s3=new Line();
Shape s4=new Square();
s1.draw();
s2.draw();
s3.draw();
s4.draw();
}  
}  
```
##### Output
```sh
drawing circle
drawing rectangle
drawing Line
drawing square
```
> 6.Write an abstract class Persistence' along with two sub classes "FilePersistence &"DatabasePersistence'. The base class with have an abstract method persist() which will be overridden by its sub classes. Write a client who gets the Persistence object at runtime & invokes persist() method on it without knowing whether data is being saved in File or in Database
```sh
abstract class Presistence{
	abstract void presist();
}
class FilePresistenece extends Presistence{

	@Override
	void presist() {
		// TODO Auto-generated method stub
		System.out.println("Data Saved in File");
	}
	
}
class DatabasePresistenece extends Presistence{
	@Override
	void presist() {
		// TODO Auto-generated method stub
		System.out.println("Data saved in Database");
	}
}
public class Client extends Presistence{

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Presistence obj=new Client();
		obj.presist();
	}

	@Override
	void presist() {
		// TODO Auto-generated method stub
		System.out.println("Presist method from client");
		
	}
}
```
##### Output
```sh
Presist method from client
```
> 7.Develop an application for Dessert shop. The application should allow owner to add items like Candy, Cookie or IceCream in the shop storage. Also customers should be able to place an order.
Dessertitem is an abstract class having an abstract method getCost(). Every dessert item has tax associated. Candy item is sold in dollar currency, Cookie in Euro currency & IceCream in Rupees currency. The sub classes are supposed to override these methods. When we run the application, it should ask us our role i.e. owner or customer. If role is owner, we should be able to add dessert items in our storage. If role is customer, then we should be able to place an order. The currency conversion rates are:
1 dollar = 60 rupees.
1 euro = 70 rupees.
```sh
import java.util.Scanner;
abstract class Dessertitem{
	abstract void getCost();
}
class Candy extends Dessertitem{

	@Override
	void getCost() {
		// TODO Auto-generated method stub
		double val=0;
		int orderqty, amt[]= {5,10,50};
		double tax=0.3;
		System.out.println("Tax on Candy dessert : "+tax);
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter quantity to place order :");
		orderqty=sc.nextInt();
    	val = amt[0]*orderqty*60*tax;
		System.out.println("Thank you for placing order!! It costs :"+val+" rupees");
	}
}
class Cookie extends Dessertitem{
	@Override
	void getCost() {
		// TODO Auto-generated method stub
		double val=0;
		int orderqty, amt[]= {5,10,50};
		double tax=0.2;
		System.out.println("Tax on Cookie dessert : "+tax);
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter quantity to place order :");
		orderqty=sc.nextInt();
    	val = amt[1]*orderqty*70*tax;
		System.out.println("Thank you for placing order!! It costs :"+val+" rupees");
	}
}
class Icecream extends Dessertitem{
	@Override
	void getCost() {
		// TODO Auto-generated method stub
		double val=0;
		int orderqty, amt[]= {5,10,50};
		double tax=0.5;
		System.out.println("Tax on Icecream dessert : "+tax);
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter quantity to place order :");
		orderqty=sc.nextInt();
    	val = amt[2]*orderqty*tax;
		System.out.println("Thank you for placing order!! It costs :"+val+" rupees");
	}
}
public class DessertShop {
	public static void main(String[] args) {
		// TODO Auto-generated method stub  
		String desserts[]= {"Candy","Cookie","Icecream"};
		int qty[]= {10,20,15},amt[]= {5,10,50}; 
		Dessertitem can=new Candy();
		Dessertitem ck=new Cookie();
		Dessertitem ice=new Icecream();
		Scanner sc = new Scanner(System.in); 
		 char ch;
		 int own;  
	        do {  
	            System.out.println("\n ***Welcom to Dessert Shop Application***");  
	            System.out.println("a. Owner \n b. Customer\n  c.Exit ");  
	            System.out.println("Enter your choice: ");  
	            ch = sc.next().charAt(0);  
	                switch (ch) {  
	                    case 'a':  
	                    	System.out.println("\n ***Owner Module***");
	                    	System.out.println("\n ***Dessert you want to add***");  
	         	            System.out.println("1. Candy\n2. Cookie\n3.Icecream ");
	         	            System.out.println("Enter your choice: ");
	         	            own=sc.nextInt();
	         	            if(own==1 || own==2 || own ==3) {
	         	            	System.out.println(desserts[own-1]+" Available quantity in stock : "+qty[own-1]);
	         	            	System.out.println("Enter the quantity to add:");
		                    	qty[own-1]=qty[own-1]+sc.nextInt();
		                    	System.out.println("Dessert added succesfully");
		                    	System.out.println("Candy : "+qty[0]+"\nCookie : "+qty[1]+"\nIcecream : "+qty[2]);
		                    	System.out.println("See you soon...Have a great day!!");
	         	            }
	         	            break;
	                    case 'b':  
	                    	System.out.println("\n ***Customer Module***");
	                    	System.out.println("\n ***Dessert you want to place an Order for***");  
	         	            System.out.println("1. Candy\n2. Cookie\n3.Icecream ");
	         	            System.out.println("Enter your choice: ");
	         	            own=sc.nextInt();
	         	           switch(own) {
	         	            case 1:
	         	            	System.out.println("**Candy**");
		                    	System.out.println("quantity Available: "+qty[own-1]);
		                    	System.out.println("Each Candy costs : "+amt[own-1]+" in dollars");
		                    	can.getCost();
		                    	System.out.println("See you soon...Have a great day!!");
		                    	break;
		                    	
	         	           case 2:
	         	            	System.out.println("**Cookie**");
		                    	System.out.println("quantity Available: "+qty[own-1]);
		                    	System.out.println("Each Cookie costs : "+amt[own-1]+" in Euros");
		                    	ck.getCost();
		                    	System.out.println("See you soon...Have a great day!!");
		                    	break;
		                    	
	         	          case 3:
	         	        	  	System.out.println("**Icecream**");
		                    	System.out.println("quantity Available: "+qty[own-1]);
		                    	System.out.println("Each Icecream costs : "+amt[own-1]+" in Rupees");
		                    	ice.getCost();
		                    	System.out.println("See you soon...Have a great day!!");
		                    	break;
		                    	
	         	            }
	                    case 'c':  
	                        System.out.println("See you soon...Have a great day!!");  
	                        break;
	                }  
	        }  
	        while (ch != (int)'c');  
	}
}
```
##### Output
```sh
 ***Welcom to Dessert Shop Application***
a. Owner 
 b. Customer
  c.Exit 
Enter your choice: 
a

 ***Owner Module***

 ***Dessert you want to add***
1. Candy
2. Cookie
3.Icecream 
Enter your choice: 
1
Candy Available quantity in stock : 10
Enter the quantity to add:
5
Dessert added succesfully
Candy : 15
Cookie : 20
Icecream : 15
See you soon...Have a great day!!

 ***Welcom to Dessert Shop Application***
a. Owner 
 b. Customer
  c.Exit 
Enter your choice: 
a

 ***Owner Module***

 ***Dessert you want to add***
1. Candy
2. Cookie
3.Icecream 
Enter your choice: 
3
Icecream Available quantity in stock : 15
Enter the quantity to add:
3
Dessert added succesfully
Candy : 15
Cookie : 20
Icecream : 18
See you soon...Have a great day!!

 ***Welcom to Dessert Shop Application***
a. Owner 
 b. Customer
  c.Exit 
Enter your choice: 
b

 ***Customer Module***

 ***Dessert you want to place an Order for***
1. Candy
2. Cookie
3.Icecream 
Enter your choice: 
2
**Cookie**
quantity Available: 20
Each Cookie costs : 10 in Euros
Tax on Cookie dessert : 0.2
Enter quantity to place order :
2
Thank you for placing order!! It costs :280.0 rupees
See you soon...Have a great day!!
```
