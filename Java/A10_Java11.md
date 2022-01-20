# Lambda Expressions | Assignment 10
------------------------------------------------------------------------------
>1.Write a program to calculate the Simple Interest with minimal code using features of Java 11.
Hint: Use the concept of functional interface and Local variable syntax for lambda parameters.
```sh
@FunctionalInterface
interface SI {
    int formula(int x,int y,int z);
}

public class Simpleinterest {

	public static void main(String[] args) {
		int p=1000,r=10,t=2;
		
		 //lambda expression to define the simple interest formula
		 SI s=(x,y,z)->(x*y*z)/100;
		
		 int simp = s.formula(p,r,t);
	     System.out.println("Simple interest : "+simp);
	}
}
```
#### Output
```sh
Simple interest : 200
```
>2.Java 11 supports var keyword for variable declarations. List the scenarios where var keyword cannot be used for such variable declarations. Give reason in support of your answer for each scenario.

*Keyword var can be used for declaring local variables, including index variables of for-loops.var cannot be used for fields, method parameters, and method return types*
**The reasons:**
* Cannot use for method parameters, and method return
* Cannot use for fields
* Suppose a field’s type was declared with var keyword. A change to the field’s initializer could change the field’s type, which might unexpectedly break reflective code.
```sh
public class testvar {
	
	public static void main(String[] args) {
		//without initialization
		var x;
		x=10;
		
		//not allowed as an element type of an array
		var list[]= {1,2,3};
		
		//Lambda expression needs an explicit target
		var obj =(a,b)->(a+b);
		
	}

}
```
#### Output
```sh
Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
	Cannot use 'var' on variable without initializer
	Array initializer needs an explicit target-type
	'var' is not allowed as an element type of an array
	Lambda expression needs an explicit target-type

	at testvar.main(testvar.java:6)
```
>3.“A quick brown fox jumps over the lazy dog". Create an ArrayList from the given String. Such an ArrayList should include each word from the given sentence. Finally convert such List to an array using Java 11 methods and print the output.
```sh
import java.util.ArrayList;
import java.util.Arrays;

public class ToArray {

	public static void main(String[] args) {
	
		ArrayList<String> l = new ArrayList<>();
		l.add("A");
		l.add("quick");
		l.add("brown");
		l.add("fox");
		l.add("jumps");
		l.add("over");
		l.add("the");
		l.add("lazy");
		l.add("dog");
		
		String arr[] = l.toArray(String[]::new);
		System.out.println(Arrays.toString(arr));	
	}
}
```
#### Output
```sh
[A, quick, brown, fox, jumps, over, the, lazy, dog]
```
>4.Using features of Java 11, read the data from a text file (File name: StudentList.txt).Calculate the count of students and print the names as well as the total count of students on the screen. (If any line in file doesn't contain a name, for such a record blank space should not be printed in the output)
Hint: Use java 11 features of files and String methods to reduce the lines of code to be written
```sh
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.util.Arrays;

public class Readfile {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int cnt=0;
		var path = "C:\\Users\\SAIHCHIL\\StudentList.txt";
		try {
			String display = Files.readString(Path.of(path));
			String strArray[] = display.split("\\s");
			//System.out.println(Arrays.toString(strArray));
			
			System.out.println("Names of the Students : ");
			for(int i =0; i<strArray.length;i++) {
				if(!strArray[i].isBlank() && !strArray[i].isEmpty()) {
					cnt=cnt+1;
					System.out.println(strArray[i].stripLeading().stripTrailing());
				}
			}
			System.out.println("Number of the students in the file : "+cnt);
		}catch(IOException e) {
			e.printStackTrace();
		}
	}

}
```
#### Output
```sh
Names of the Students : 
John
Mathew
Sheeren
George
Peeter
Steven
Michel
Andrew
Number of the students in the file : 8
```
>5 Write a program with menu to accept the price of certain items and display their total.When user selects 
Option 1: should accept the prices of different products and insertthese prices into first file (each amount to be inserted in a newline in the file). Next,total of these values should be saved in a new file. 
Option 2: should allow the user toview the total of these prices from the second file.
```sh
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.StandardOpenOption;
import java.util.Scanner;

public class Writetofile {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		var firstfile = "C:\\Users\\SAIHCHIL\\prices.txt";
		var secondfile = "C:\\Users\\SAIHCHIL\\total.txt";
		int val =1,pr,total=0;
		String c="Yes";
		try {
		Scanner sc = new Scanner(System.in); 
		 char ch;
		    do {  
	            System.out.println("\n ***Menu***");  
	            System.out.println("a.Insert new price \nb.View purchase Total \nc.Exit ");  
	            System.out.println("Enter your choice: ");  
	            ch = sc.next().charAt(0);  
	                switch (ch) {  
	                    case 'a': do {
	                    	if(c.equals("Yes")) {
	                    	System.out.println("\nInsert "+val+" item price");
	                    	pr=sc.nextInt();
	                    	total=total+pr;
	                    	Files.writeString(Path.of(firstfile), String.valueOf(pr),StandardOpenOption.APPEND);
	                    	System.out.println("---Price has been saved to the file---");
	                    	System.out.println("***Do u want to enter price for more items?(Yes/No)***");
	                    	c=sc.next();
	                    	val=val+1;
	                    	}else {
	                    		break;
	                    	}
	                    }while(c!="Yes");
	                    break;
	                    case 'b':
	                    	Files.writeString(Path.of(secondfile), String.valueOf(total),StandardOpenOption.APPEND);
	                    	String totprice = Files.readString(Path.of(secondfile));
	                    	System.out.println(totprice);
	                    	break;
	                    case 'c':
	                    	System.out.println("See you soon!!");
	                }
	                
		    } while (ch != (int)'c');  
	                    	
		
		}catch(IOException e) {
			e.printStackTrace();
		}
	}

}
```
#### Output
```sh
 ***Menu***
a.Insert new price 
b.View purchase Total 
c.Exit 
Enter your choice: 
a

Insert 1 item price
100
---Price has been saved to the file---
***Do u want to enter price for more items?(Yes/No)***
Yes

Insert 2 item price
300
---Price has been saved to the file---
***Do u want to enter price for more items?(Yes/No)***
Yes

Insert 3 item price
51
---Price has been saved to the file---
***Do u want to enter price for more items?(Yes/No)***
No

 ***Menu***
a.Insert new price 
b.View purchase Total 
c.Exit 
Enter your choice: 
b
Total price of all items is :451

 ***Menu***
a.Insert new price 
b.View purchase Total 
c.Exit 
Enter your choice: 
c
See you soon!!
```
>6 Write a code using HttpClient API which sends a GET request
to https://httpbin.org/get, and print out the response header, status code, and body for the given URL.
```sh
import java.io.IOException;
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.net.http.HttpClient.Version;
import java.net.http.HttpResponse.BodyHandlers;

public class Httprequest {

	public static void main(String[] args) {
		
		String uri = "https://httpbin.org/get";
		
		HttpRequest req = HttpRequest.newBuilder()
				.uri(URI.create(uri))
				.GET()
				.version(Version.HTTP_2)
				.build();
		
		HttpClient client = HttpClient.newBuilder()
				.build();
		
		try
		{
			HttpResponse<String> resp = client.send(req, BodyHandlers.ofString());
			System.out.println(resp.headers());
			System.out.println(resp.statusCode());
			System.out.println(resp.body());
		}
		catch(IOException | InterruptedException e)
		{
			e.printStackTrace();
		}

	}

}
```
#### Output
```sh
java.net.http.HttpHeaders@6ba7ca03 { {:status=[200], access-control-allow-credentials=[true], access-control-allow-origin=[*], content-length=[245], content-type=[application/json], date=[Thu, 20 Jan 2022 18:31:49 GMT], server=[gunicorn/19.9.0]} }
200
{
  "args": {}, 
  "headers": {
    "Host": "httpbin.org", 
    "User-Agent": "Java-http-client/17.0.1", 
    "X-Amzn-Trace-Id": "Root=1-61e9aa95-1ea592be7298d831202c8763"
  }, 
  "origin": "49.37.148.112", 
  "url": "https://httpbin.org/get"
}
```