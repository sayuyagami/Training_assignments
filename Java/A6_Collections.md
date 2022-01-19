# Collections Concept | Assignment 5
------------------------------------------------------------------------------
> 1.Given a TreeMap<Long, Contact> which has phone numbers for keys and contact objects for
values.
Write solutions to
a. Fetch all the keys and print them,
b. Fetch all the values and print them
c. Print all key-value pairs
Note:
a) Contacts should be stored in descending order of phone number
b) Contact Class:
PhoneNumer: <long>
Name: <String>
Email: <String>
Gender: <Enum>
##### Contacts Class
```sh
package tree;
public class Contacts {
	long phnum;
	String name,email;
	gender g;
	public enum gender
    {
        F,M;
    }
	public Contacts(long phnum, String name, String email,gender g) {
		super();
		this.phnum = phnum;
		this.name = name;
		this.email = email;
		this.g = g;
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
	public String getEmail() {
		return email;
	}
	public void setEmail(String email) {
		this.email = email;
	}
	public gender getG() {
		return g;
	}
	public void setG(gender g) {
		this.g = g;
	}
}
```
#### Mainclass(Treemap)
```sh
import java.util.Collections;
import java.util.Map;
import java.util.TreeMap;
import tree.Contacts;
import tree.Contacts.gender;

public class Treemap {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Map<Long,Contacts> tmap = new TreeMap<Long,Contacts>();
		Contacts ct1 = new Contacts(3456169010L, "Hima", "hima@gmail.com",gender.F);
		Contacts ct2 = new Contacts(5678901119L, "kazu", "kazu@gmail.com",gender.M);
		Contacts ct3 = new Contacts(7890021673L, "John", "john@gmail.com",gender.M);
		Contacts ct4 = new Contacts(9000345262L, "Radha", "radha@gmail.com",gender.F);
		Contacts ct5 = new Contacts(7990113458L, "Cherry", "cherry@gmail.com",gender.F);
		
		tmap.put((long) 3456169010L, ct1);
		tmap.put((long) 5678901119L, ct2);
		tmap.put((long) 7890021673L, ct3);
		tmap.put((long) 9000345262L, ct4);
		tmap.put((long) 7990113458L, ct5);
		
		System.out.println("------Fetch all the keys and print-------- ");
		for(Map.Entry<Long,Contacts>entry:tmap.entrySet()) {
			Long key = entry.getKey();
			Contacts c = entry.getValue();
			System.out.println("Keys :"+key);
		}
		
		System.out.println("------Fetch all the keys and print in descending order-------- ");
		//Fetch all the keys and print in descending order
		Map<Long,Contacts> sorttmap = new TreeMap<Long,Contacts>(Collections.reverseOrder());
		sorttmap.putAll(tmap);
				for(Map.Entry<Long,Contacts>entry:sorttmap.entrySet()) {
					
					Long key = entry.getKey();
					Contacts c = entry.getValue();
					System.out.println("Keys :"+key);
				}
		
		System.out.println("------Fetch all the values and print-------- ");
		//fetch all the values and print
			for(Map.Entry<Long,Contacts>entry:sorttmap.entrySet()) {
			Long key = entry.getKey();
			Contacts c = entry.getValue();
			System.out.println("Name : "+c.getName()+"\nEmailID :"+c.getEmail()+"\nGender :"+c.getG()+"\nMobile no. :"+c.getPhnum());
		}
		
		System.out.println("------print all key and values-------- ");
		//fetch all the values and print
			for(Map.Entry<Long,Contacts>entry:sorttmap.entrySet()) {
			Long key = entry.getKey();
			Contacts c = entry.getValue();
			System.out.println("Keys :"+key);
			System.out.println("Name : "+c.getName()+" EmailID :"+c.getEmail()+" Gender :"+c.getG());
		}
			
		//print all key-value pairs
		System.out.println("--------print all key-value pairs-------- ");
		System.out.println("Key-Value pairs : "+sorttmap);
	}

}
```
##### Output
```sh
------Fetch all the keys and print-------- 
Keys :3456169010
Keys :5678901119
Keys :7890021673
Keys :7990113458
Keys :9000345262
------Fetch all the keys and print in descending order-------- 
Keys :9000345262
Keys :7990113458
Keys :7890021673
Keys :5678901119
Keys :3456169010
------Fetch all the values and print-------- 
Name : Radha
EmailID :radha@gmail.com
Gender :F
Mobile no. :9000345262
Name : Cherry
EmailID :cherry@gmail.com
Gender :F
Mobile no. :7990113458
Name : John
EmailID :john@gmail.com
Gender :M
Mobile no. :7890021673
Name : kazu
EmailID :kazu@gmail.com
Gender :M
Mobile no. :5678901119
Name : Hima
EmailID :hima@gmail.com
Gender :F
Mobile no. :3456169010
------print all key and values-------- 
Keys :9000345262
Name : Radha EmailID :radha@gmail.com Gender :F
Keys :7990113458
Name : Cherry EmailID :cherry@gmail.com Gender :F
Keys :7890021673
Name : John EmailID :john@gmail.com Gender :M
Keys :5678901119
Name : kazu EmailID :kazu@gmail.com Gender :M
Keys :3456169010
Name : Hima EmailID :hima@gmail.com Gender :F
--------print all key-value pairs-------- 
Key-Value pairs : {9000345262=tree.Contacts@53bd815b, 7990113458=tree.Contacts@2401f4c3, 7890021673=tree.Contacts@7637f22, 5678901119=tree.Contacts@4926097b, 3456169010=tree.Contacts@762efe5d}
```
> 2.Write an application to store 10 unique product objects. In case there is an attempt to add a duplicate product, it should be silently rejected. Hint: Use HasSet or TreeSet Extra(optional): Use ArrayList in the above solution. (This is optional)
```sh
import java.util.Scanner;
import java.util.TreeSet;

public class Mainproducts {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int n=10;
		TreeSet<String> hs = new TreeSet<String>();
		String products[]= new String[10];
		
		System.out.println("Please enter unique product names : ");
		for(int i=0;i<n;i++) {
			System.out.println("Product "+(i+1)+":");
			Scanner sc = new Scanner(System.in);
			products[i]=sc.next();
			hs.add(products[i]);
			}
		System.out.println("Your unique products : ");
		System.out.println(hs);
	}
}
```
##### Output
```sh
Please enter unique product names : 
Product 1:
Honey

Product 2:
Pizza

Product 3:
Burger

Product 4:
Chocolate

Product 5:
Cake

Product 6:
Popcorn

Product 7:
Pizza

Product 8:
Sandwich

Product 9:
Juice

Product 10:
Cake

Your unique products : 
[Burger, Cake, Chocolate, Honey, Juice, Pizza, Popcorn, Sandwich]
```
> 3.Store at least 10 Employee Objects in an TreeSet<Employee>. When the application runs the user should be asked to select one of the options upon which you will print the employee details in a sorted manner.
For E.g.
Run Application:
a) ID
b) Name
c) Department
d) Salary
Your choice: b
<Should print all the employee's details sorted by name>
```sh
package data;

public class Employee {

	Integer id,salary;
	
	String name,department;
	public Employee(Integer id, Integer salary, String name, String department) {
		super();
		this.id = id;
		this.salary = salary;
		this.name = name;
		this.department = department;
	}
	public Integer getId() {
		return id;
	}
	public void setId(Integer id) {
		this.id = id;
	}
	public Integer getSalary() {
		return salary;
	}
	public void setSalary(Integer salary) {
		this.salary = salary;
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
	
}
```
```sh
package data;

import java.util.Comparator;

public class SortbyID implements Comparator<Employee>{

	@Override
	public int compare(Employee e1, Employee e2) {
		// TODO Auto-generated method stub
		return e1.getId().compareTo(e2.getId());
	}

}
```
```sh
package data;

import java.util.Comparator;

public class SortbyName implements Comparator<Employee>{

	@Override
	public int compare(Employee e1, Employee e2) {
		// TODO Auto-generated method stub
		return e1.getName().compareTo(e2.getName());
	}

}
```
```sh
package data;

import java.util.Comparator;

public class SortbyDept implements Comparator<Employee>{

	@Override
	public int compare(Employee e1, Employee e2) {
		// TODO Auto-generated method stub
		return e1.getDepartment().compareTo(e2.getDepartment());
	}

}
```
```sh
package data;

import java.util.Comparator;

public class SortbySalary implements Comparator<Employee>{

	@Override
	public int compare(Employee e1, Employee e2) {
		// TODO Auto-generated method stub
		return e1.getSalary().compareTo(e2.getSalary());
	}

}
```
```sh
import java.util.Scanner;
import java.util.TreeSet;
import data.Employee;
import data.SortbyDept;
import data.SortbyID;
import data.SortbyName;
import data.SortbySalary;

public class Sortbyorder {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Employee emp1 = new Employee(111,25000,"Yagami","IT");
		Employee emp2 = new Employee(122,450000,"Naruto","IT");
		Employee emp3 = new Employee(131,20000,"Hiroshima","CSE");
		Employee emp4 = new Employee(137,30000,"Kazuma","CSE");
		Employee emp5 = new Employee(155,40000,"Hima","ECE");
		Employee emp6 = new Employee(995,65000,"Ayato","IT");
		Employee emp7 = new Employee(677,450000,"Chihaya","IT");
		Employee emp8 = new Employee(453,29000,"Erika","CSE");
		Employee emp9 = new Employee(825,35000,"Miki","CSE");
		Employee emp10 = new Employee(610,41000,"Sana","ECE");
		
		Scanner sc = new Scanner(System.in); 
		 char ch;
		    do {  
	            System.out.println("\n ***Employees details sort by : ***");  
	            System.out.println("a. ID \nb. Name \nc. Department \nd. Salary \ne.exit");  
	            System.out.println("Enter your choice: ");  
	            ch = sc.next().charAt(0);  
	                switch (ch) {  
	                    case 'a':  
	                    	//sort by id
	                		TreeSet<Employee> sortid = new TreeSet<>(new SortbyID());
	                		sortid.add(emp1);
	                		sortid.add(emp2);
	                		sortid.add(emp3);
	                		sortid.add(emp4);
	                		sortid.add(emp5);
	                		sortid.add(emp6);
	                		sortid.add(emp7);
	                		sortid.add(emp8);
	                		sortid.add(emp9);
	                		sortid.add(emp10);
	                		
	                		System.out.println("Sorted details by ID");
	                		for(Employee e:sortid) {
	                			System.out.println(e.getId()+","+e.getName()+","+e.getDepartment()+","+e.getSalary());
	                		}
	                		break;
	                    case 'b':
	                    	//sort by name
	                		TreeSet<Employee> sortnm = new TreeSet<>(new SortbyName());
	                		sortnm.add(emp1);
	                		sortnm.add(emp2);
	                		sortnm.add(emp3);
	                		sortnm.add(emp4);
	                		sortnm.add(emp5);
	                		sortnm.add(emp6);
	                		sortnm.add(emp7);
	                		sortnm.add(emp8);
	                		sortnm.add(emp9);
	                		sortnm.add(emp10);
	                		
	                		System.out.println("Sorted details by Name");
	                		for(Employee e:sortnm) {
	                			System.out.println(e.getId()+","+e.getName()+","+e.getDepartment()+","+e.getSalary());
	                		}
	                		break;
	                    case 'c': 
	                    	//sort by department
	                		TreeSet<Employee> sortdept = new TreeSet<>(new SortbyDept());
	                		sortdept.add(emp1);
	                		sortdept.add(emp2);
	                		sortdept.add(emp3);
	                		sortdept.add(emp4);
	                		sortdept.add(emp5);
	                		sortdept.add(emp6);
	                		sortdept.add(emp7);
	                		sortdept.add(emp8);
	                		sortdept.add(emp9);
	                		sortdept.add(emp10);
	                		
	                		System.out.println("Sorted details by Department");
	                		for(Employee e:sortdept) {
	                			System.out.println(e.getId()+","+e.getName()+","+e.getDepartment()+","+e.getSalary());
	                		}
	                		break;
	                    case 'd':
	                    	//sort by salary
	                		TreeSet<Employee> sortsal = new TreeSet<>(new SortbySalary());
	                		sortsal.add(emp1);
	                		sortsal.add(emp2);
	                		sortsal.add(emp3);
	                		sortsal.add(emp4);
	                		sortsal.add(emp5);
	                		sortsal.add(emp6);
	                		sortsal.add(emp7);
	                		sortsal.add(emp8);
	                		sortsal.add(emp9);
	                		sortsal.add(emp10);
	                		
	                		System.out.println("Sorted details by Salary");
	                		for(Employee e:sortsal) {
	                			System.out.println(e.getId()+","+e.getName()+","+e.getDepartment()+","+e.getSalary());
	                		}
	                		break;
	                    case 'e':
	                    	 System.out.println("See you soon...Have a great day!!");  
		                     break;
	                }
	        }
	        while (ch != (int)'e');  
	}
		
}
```
##### Output
```sh
 ***Employees details sort by : ***
a. ID 
b. Name 
c. Department 
d. Salary 
e.exit
Enter your choice: 
a
Sorted details by ID
111,Yagami,IT,25000
122,Naruto,IT,450000
131,Hiroshima,CSE,20000
137,Kazuma,CSE,30000
155,Hima,ECE,40000
453,Erika,CSE,29000
610,Sana,ECE,41000
677,Chihaya,IT,450000
825,Miki,CSE,35000
995,Ayato,IT,65000

 ***Employees details sort by : ***
a. ID 
b. Name 
c. Department 
d. Salary 
e.exit
Enter your choice: 
b
Sorted details by Name
995,Ayato,IT,65000
677,Chihaya,IT,450000
453,Erika,CSE,29000
155,Hima,ECE,40000
131,Hiroshima,CSE,20000
137,Kazuma,CSE,30000
825,Miki,CSE,35000
122,Naruto,IT,450000
610,Sana,ECE,41000
111,Yagami,IT,25000

 ***Employees details sort by : ***
a. ID 
b. Name 
c. Department 
d. Salary 
e.exit
Enter your choice: 
c
Sorted details by Department
131,Hiroshima,CSE,20000
155,Hima,ECE,40000
111,Yagami,IT,25000

 ***Employees details sort by : ***
a. ID 
b. Name 
c. Department 
d. Salary 
e.exit
Enter your choice: 
e
See you soon...Have a great day!!

```
> 4.Given a LinkedList of Objects representing date of birth's (use any inbuild java class to
represent date), print the date's along with the message: Your date of Birth is DD-MM-YYYY,
and it (was or was not) a leap year.
E.g.
a) For the date 23-12-2000
Your date of birth is 23-12-2000 and it was a leap year
c) For the date 23-12-2001
Your date of birth is 23-12-2000 and it was not a leap year
Note: You need to access the Dates in the reverse order. I.e. start from the last object and
move towards the first object
```sh
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;
import java.util.LinkedList;
import java.util.ListIterator;

public class LeapyrCheck {

	public static void main(String[] args) {
		
		LocalDate date1 = LocalDate.of(2000, 12, 23);
		LocalDate date2 = LocalDate.of(1999, 8, 10);
		LocalDate date3 = LocalDate.of(2001, 12, 23);
		
		LinkedList<LocalDate> doblist = new LinkedList<LocalDate>();
		
		doblist.add(date1);
		doblist.add(date2);
		doblist.add(date3);
		
		ListIterator<LocalDate> list_Iter = doblist.listIterator();
		while(list_Iter.hasNext()) {
			 LocalDate db = (LocalDate) list_Iter.next();
		}
		
		System.out.println("Reading list in Reverse Order");
		while(list_Iter.hasPrevious()) {
			 LocalDate db = (LocalDate) list_Iter.previous();
			 String printDate = db.format(DateTimeFormatter.ofPattern("dd-MM-YYYY"));
			 if(db.isLeapYear())
				{

					System.out.println("Your Date of Birth is " + printDate + " and it was a leap year");
				}
				else
				{
					System.out.println("Your Date of Birth is " + printDate + " and it was not a leap year");
				}
		}
			 
	}

}
```
##### Output
```sh
Reading list in Reverse Order
Your Date of Birth is 23-12-2001 and it was not a leap year
Your Date of Birth is 10-08-1999 and it was not a leap year
Your Date of Birth is 23-12-2000 and it was a leap year
```