# Generics Concept | Assignment 5
------------------------------------------------------------------------------
> 1.Use a HashSet to hold Employee Objects. Upon running the application, the details of the employees added to the HashSet should be displayed.
Employee <<class>>
|-- id
| -- name
| -- salary
|-- department
|-- displayDetails()
Feel free to add properties and methods to Employee Class
Note: if we try to store any object other than Employee Object in HashSet, we should not be allowed to.
##### Employees Class
```sh
import java.util.regex.Pattern;
public class Employees {
	
		int id,salary;
		long phnum;
		String name,department,email;
		
		public Employees(int id, int salary, long phnum, String name, String department, String email) {
			super();
			this.id = id;
			this.salary = salary;
			this.phnum = phnum;
			this.name = name;
			this.department = department;
			this.email = email;
		}

		public int getId() {
			return id;
		}

		public void setId(int id) {
			this.id = id;
		}

		public int getSalary() {
			return salary;
		}

		public void setSalary(int salary) {
			this.salary = salary;
		}

		public long getPhnum() {
			return phnum;
		}

		public void setPhnum(long phnum) {
			this.phnum = phnum;
		}

		public String getName() {
			return name;
		}

		public void setName(String name) {
			this.name = name;
		}

		public String getDepartment() {
			return department;
		}

		public void setDepartment(String department) {
			this.department = department;
		}

		public String getEmail() {
			return email;
		}

		public void setEmail(String email) {
			this.email = email;
		}
		
		public void displayDetails() {
			System.out.println("Employee ID :"+ getId()+"\n Employee name :"+ getName()+"\nDepartment :"+getDepartment()+
					"\nEmail ID :"+getEmail()+"\nMobile No. : "+getPhnum());
		}

		public void checknum(long l) {
			// TODO Auto-generated method stub
			int len = String.valueOf(l).length();
			try {
				if(len < 10 || len > 10) {
					throw new InvalidMobileNumber();
				}else if(len == 10){
					setPhnum(l);
					 System.out.println("Verified Mobile number"); 
				 }
				
			}catch(InvalidMobileNumber e) {
				System.out.println("Please enter valid mobile number");
				}
			}

		public void checkmail(String mail) {
			// TODO Auto-generated method stub
			 String emailRegex = "^[a-zA-Z0-9_+&*-]+(?:\\."+
                     "[a-zA-Z0-9_+&*-]+)*@" +
                     "(?:[a-zA-Z0-9-]+\\.)+[a-z" +
                     "A-Z]{2,7}$";
                       
			 Pattern pat = Pattern.compile(emailRegex);
			 try {
			 if (!(pat.matcher(mail).matches()))
			 {
				 throw new InValidEmailId();
			 }else {
				 setEmail(mail);
				 System.out.println("Verified email id");
				 
			 }
			 }catch(InValidEmailId e) {System.out.println("Please enter valid email id");}
		}
}
class InvalidMobileNumber extends RuntimeException{}
class InValidEmailId extends RuntimeException{}
```
#### Mainclass to call EmployeesClass
```sh
import java.util.HashSet;
import java.util.Scanner;

public class Hashset {
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		HashSet<Employees> data = new HashSet<>();
		Employees emp= new Employees(0,0,0,null,null,null);
		//data.add(emp);
		Scanner sc= new Scanner(System.in);
		
		System.out.println("/**Enter employee details**/");
		System.out.println("Employee ID : ");
		emp.setId(sc.nextInt());
		System.out.println("Employee name : ");
		emp.setName(sc.next());
		System.out.println("Employee department : ");
		emp.setDepartment(sc.next());
		System.out.println("Employee Email id : ");
		for(int i=0;i<3;i++) {
			emp.checkmail(sc.next());
			if(i==2 && emp.email==null) {
				System.out.println("You have exhausted your attempts.PLease try Again!!");
				System.exit(0);
			}else if(emp.email!=null) {break;}
			}

		System.out.println("Employee Mobile no : ");
		
		for(int i=0;i<3;i++) {
			emp.checknum(sc.nextLong());
			 int val = String.valueOf(emp.phnum).length();
			if(i==2 && val == 0){
				System.out.println("You have exhausted your attempts.PLease try Again!!");
				System.exit(0);
			}else if(val!=1) {break;}
			}
		
		//adding data through hashset
		data.add(emp);
		
		System.out.println("---Employee details display---");
		emp.displayDetails();
	}
}
```
##### Output
```sh
/**Enter employee details**/
Employee ID : 
111
Employee name : 
Hima
Employee department : 
IT
Employee Email id : 
hima11
Please enter valid email id
hima11@gmail.com
Verified email id
Employee Mobile no : 
76217682917890
Please enter valid mobile number
7282457890
Verified Mobile number
---Employee details display---
Employee ID :111
 Employee name :Hima
Department :IT
Email ID :hima11@gmail.com
Mobile No. : 7282457890
```
> 2.Write an application to hold 10 random int values as keys and 10 random double values as values for a HashMap. Print the data store in the HashMap. Note: Keys can only be int and values double
```sh
import java.util.HashMap;
import java.util.TreeMap;

         public class Hashmap {
         public static void main(String[] args)
         {
	  
        	//TreeMap<Integer,Double> map=new TreeMap<>();--to display in sorted order
        	HashMap<Integer,Double> map=new HashMap<>();
			map.put(829, 37.5);
			map.put(22, 144.7);
			map.put(125, 57.7);
			map.put(66, 32.5);
			map.put(55, 38.9);
			map.put(125, 59.9);
			map.put(137, 72.8);
			map.put(37, 231.4);
			map.put(995, 9.51);
			map.put(557, 87.62);
	        System.out.println(map);
	     }
     }
```
##### Output
```sh
{66=32.5, 995=9.51, 37=231.4, 22=144.7, 55=38.9, 137=72.8, 829=37.5, 125=59.9, 557=87.62}
```
> 3.Write a generic method to exchange the positions of two different elements in an array.
```sh
import java.util.Arrays;
public class GenericSwap{

	public static final <T> void swap(T[] a, int i, int j) {
		T t = a[i];
		a[i] = a[j];
		a[j] = t;
		}

public static void main(String[] args){
String[] a={"11","55","37"};
System.out.println("Array before Swap: "+Arrays.toString(a));
swap(a,0,2);
System.out.println("Array after Swap: "+Arrays.toString(a));
}
}
```
##### Output
```sh
Array before Swap: [11, 55, 37]
Array after Swap: [37, 55, 11]
```
> 4.Design a class named Pair which has two properties. The name of the first property is key and that of the second property is volue. When designing the class take case of the following scenarios:
a. Create an Object of Pair class to store String value for the property key and String value for the property value. Restriction Apart from String type no other types should be acceptable as key or value input
e.g.
myObj.setKey("1");
myObj.setValue("Hello");
b.Create an object of the class Pair to store String value for the property key and java.util.Date as value for the property value
e.g.
myObj.setKey("Today is");
myObj.setValue(new java.util.Date());
Note: In scenario a. no data apart from String should be used for key and value, in scenario b. no data apart from String for key and java.util.Date should be allowed
##### Generic Interface Class
```sh
public interface GInterface<E> {
	void setValue(E e);
	E getValue();
}
```
##### Pair1 Class
```sh
public class Pair1<E,K> implements GInterface<E> {

	private E e;
	private K k;
	@Override
	public void setValue(E e) {
		// TODO Auto-generated method stub
		this.e=e;
	}
	@Override
	public E getValue() {
		// TODO Auto-generated method stub
		return e;
	}
	public K getK() {
		return k;
	}
	public void setK(K k) {
		this.k = k;
	}
}
```
##### Main Class(Pairs)
```sh
import java.util.Date;
import java.util.HashMap;
import java.text.ParseException;
import java.text.SimpleDateFormat;
import java.time.format.DateTimeParseException;
import java.util.Scanner;

public class Pairs {
	
	public static void main(String[] args) throws ParseException {
		// TODO Auto-generated method stub
		HashMap<String,String> obj1=new HashMap<>();
		HashMap<String,Date> obj2=new HashMap<>();
		
		Pair1<String,String> p1=new Pair1();
		Pair1<String,Date> p2=new Pair1();
		
		Scanner sc= new Scanner(System.in);
		//object pair 1
		System.out.println("Enter property key1 : ");
		p1.setK(sc.nextLine());
		String k1 = p1.getK();
		System.out.println("Enter property value :");
		p1.setValue(sc.nextLine());
		String val1=p1.getValue();
		//keypairs
		obj1.put(k1, val1);
		
		//object pair 2
		System.out.println("Enter property key2 : ");
		p2.setValue(sc.nextLine());
		String k2=p2.getValue();
		System.out.println("Enter date (DD/MM/YYYY): ");
		for(int i=0;i<3;i++) {
			checkDatePattern(sc.next());
			
			//setting the date value
			SimpleDateFormat format = new SimpleDateFormat("dd/MM/yyyy");
	        Date date1 = format.parse(sc.next());
	        p2.setK(date1);
	        
			if(i==2 && p2.getK()==null) {
				System.out.println("You have exhausted your attempts.PLease try Again!!");
				System.exit(0);
			}else if(p2.getK()!=null) {break;}
			System.out.println(2-i+" more Attempts");
			}

	Date dt = p2.getK();
		//keypairs
		obj2.put(k2, dt);
		
		System.out.println("Done!!");
		
		System.out.println("\nPair 1 details : "+obj1);
		System.out.println("Pair 2 details : "+obj2);
	}
	public static void checkDatePattern(String dt) {
		Pair1<String,Date> p2=new Pair1();
	    try {
	        SimpleDateFormat format = new SimpleDateFormat("dd/MM/yyyy");
	        Date date1 = format.parse(dt);
	        //p2.setK(date1);
	        
	    } catch (ParseException e) {
	    	System.out.println("Please enter date in DD/MM/YYYY format");
	    }
	}
}
```
##### Output
```sh
Enter property key1 : 
1
Enter property value :
Hello
Enter property key2 : 
Today is
Enter date (DD/MM/YYYY): 
11202202
Please enter date in DD/MM/YYYY format
11/02/2022
Done!!

Pair 1 details : {1=Hello}
Pair 2 details : {Today is=Fri Feb 11 00:00:00 IST 2022}
```
