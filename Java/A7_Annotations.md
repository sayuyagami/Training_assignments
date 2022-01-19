# Annotations Concept | Assignment 5
------------------------------------------------------------------------------
> 1.Create a custom annotation called @Test which can be only applied on a method implying that the following method is a test-case. (Is it possible to restrict the annotation to be applied only on a non-static method?)
```sh
import java.lang.annotation.Annotation;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;
import java.lang.reflect.Method;

//multiline annotation

@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
@interface test{
	String txt();
	int num();
}
 
class demo{
	@test(txt="Hello there",num=1)
	public void testcase(){
		
	}
}

public class TestAnnotation {

	public static void main(String[] args) throws Exception {
		// TODO Auto-generated method stub
		demo d = new demo();
		
		Method cm = d.getClass().getMethod("testcase");
		Annotation an = cm.getAnnotation(test.class);
		test t = (test)an;
		System.out.println(t.txt());
		
	}

}
```
#### Output
```sh
Hello there
```
>2 Build a custom annotation called @Info, which can be used by developers on a class, a
property, or a method. The developer can provide the following information when using this
annotation:
a) Authorld: <<Developers ID>> - (Mandatory Input)
b) Author: <<Developers name> - (Optional Input)
c) Supervisor: <<Developers Supervisor>>- (Optional Input)
d) Date: <<String Date" >> - (Mandatory Input)
e) Time: << String Time >> - (Mandatory Input)
f) Version: <<Numerical Version >> - (Mandatory Input)
g) Description: <<Description of the class, method, or property >> - (Optional Input)
```sh
import java.lang.annotation.Annotation;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.reflect.Method;

@Retention(RetentionPolicy.RUNTIME)
@interface info{
	int AuthorID();
	String Authorname();
	String Supervisor();
	String dt();
	String time();
	int version();
	String description();
}

class Author{
	@info(AuthorID=111,Authorname="hima",Supervisor="Adam",dt="18-01-2022",time="10:00 AM",version=5,description="Check out this method")
	public void call() {
		System.out.println("From call Method");
	}
}
public class Developers {

	public static void main(String[] args) throws Exception {
		// Accessing info data annotation
		Author a = new Author();
		Method cm = a.getClass().getMethod("call");
		Annotation an = cm.getAnnotation(info.class);
		info t = (info)an;
		System.out.println("-------Author Details------");
		System.out.println("Author ID :"+t.AuthorID());
		System.out.println("Author Name :"+t.Authorname());
		System.out.println("Author Supervisor :"+t.Supervisor());
		System.out.println("Date :"+t.dt());
		System.out.println("Time :"+t.time());
		System.out.println("Version :"+t.version());
		System.out.println("Description :"+t.description());
	}

}
```
#### Output
```sh
-------Author Details------
Author ID :111
Author Name :hima
Author Supervisor :Adam
Date :18-01-2022
Time :10:00 AM
Version :5
Description :Check out this method
```
>3 Create a custom annotation called @Execute to be applied on methods. Placing the
@Execute method on a method implies that method should be invoked using Reflection API (Invoking the method using Reflection API is out of scope of this assignments). The annotation @Execute should have an optional property "sequence which can be given values such as 1, 2, 3... in the order of priority. In case the sequence property is not used the ADI may invoke methods in random order.
E.g.
Class MyClass
@Execute(Sequence=2)
Public void myMethod10){
}
@Execute(Sequence=1)
Public void myMethod2(){
}
@Execute(Sequence=3)
Public void myMethod30){
}
}
Note: The above annotation tells the system that the invocation should be in the order:
myMethod2 first, followed by myMethodi and finally myMethod3
```sh
import java.lang.annotation.Annotation;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;
import java.lang.reflect.Method;

@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
@interface Execute{
	int sequence();
}

class Myclass{
	
	@Execute(sequence=2)
	public void myMethod1() {System.out.println("From myMethod 1");}
	
	@Execute(sequence=1)
	public void myMethod2() {System.out.println("From myMethod 2");}
	
	@Execute(sequence=3)
	public void myMethod3() {System.out.println("From myMethod 3");}
}
public class ReflectInvoke {

	public static void main(String[] args) throws ReflectiveOperationException {
		// TODO Auto-generated method stub
		Myclass a = new Myclass();
		Method[] cm = a.getClass().getMethods();
		
		for (Method m : cm) {
			Annotation an = m.getAnnotation(Execute.class);
			Execute e = (Execute)an;
			
			if(e!=null) {
				try {
					m.invoke(a);
					m.invoke(e.sequence());
				}catch(Exception err) {
					System.out.println(err.getMessage());
				}
			}
        }
	}

}
```
#### Output
```sh
From myMethod 2
object is not an instance of declaring class
From myMethod 1
object is not an instance of declaring class
From myMethod 3
object is not an instance of declaring class
```