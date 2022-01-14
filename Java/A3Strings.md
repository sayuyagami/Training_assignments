# Assignment 3
------------------------------------------------------------------------------
### Assignments on String Class 
> 1.Write an application to determine the length of the String str = "Hello World". (Hint: Use
String method)
```sh
import java.util.Scanner;
public class StrLength{
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		System.out.print("Enter a string : ");
        Scanner scanner = new Scanner(System. in);
        String str = scanner.nextLine();
        System.out.println("Length of string : \n"+str.length());
	}
}
```
#### Output
```sh
Enter a string : Hello World
Length of string : 
11
```
> 2.Write an application to join the two Strings "Hello," & "How are you?" (Hint: Use String
method)
```sh
import java.util.Scanner;
public class StrConcat {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
        Scanner scanner = new Scanner(System. in);
        System.out.println("Enter first String : ");
        String str1 = scanner.nextLine();
        System.out.print("Enter second string : ");
        String str2 = scanner.nextLine();
        String str=str1.concat(str2);
        System.out.println("Display Concatenated String: \n "+str);
	}
}
```
```sh
Enter first String : 
Hello 
Enter second string : How are you ??
Display Concatenated String: 
 Hello How are you ??
 ```
> 3.Given a String "Java String pool refers to collection of Strings which are stored in heap
memory", perform the following operations (Hint: all operation can be performed using
String methods)
a.Print the string to console in lowercase
b. Print the string to console in uppercase
c. Replace all 'a' character in the string with $ sign
d. Check if the original String contains the word "collection"
e. Check if the following String"java string pool refers to collection of strings which
are stored in heap memory matches the original
f.If the string does not match check if there is another method which can be used to check if the strings are equal
 ```sh
 import java.util.Scanner;
public class Strmethods {
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Scanner scanner = new Scanner(System. in);
        String checkstr="Java string pool refers to collection of strings which are stored in heap memory";
        System.out.println("Enter String : ");
        String str = scanner.nextLine();
        System.out.println("LowerCase of String: \n "+str.toLowerCase());
        System.out.println("UpperCase of String: \n "+str.toUpperCase());
        System.out.println("Replace all 'a' characters in String with $ sign: \n "+str.replace('a', '$'));
        System.out.println("Contains Collection word in String: \n "+str.contains("collection"));
        System.out.println("Match method of String: \n "+str.matches(checkstr));
        System.out.println("Matches the String: \n "+str.equalsIgnoreCase(checkstr));
	}
}
```
#### Output
```sh
Enter String : 
Java String pool refers to collection of Strings which are stored in heap memory
LowerCase of String: 
 java string pool refers to collection of strings which are stored in heap memory
UpperCase of String: 
 JAVA STRING POOL REFERS TO COLLECTION OF STRINGS WHICH ARE STORED IN HEAP MEMORY
Replace all 'a' characters in String with $ sign: 
 J$v$ String pool refers to collection of Strings which $re stored in he$p memory
Contains Collection word in String: 
 true
Match method of String: 
 false
Matches the String: 
 true
```
#### Assignments on StringBuffer Class
> 4.Write an application to append the following strings "StringBuffer", "is a peer class of String", "that provides much of “, “the functionality of strings using a StringBuffer.
```sh
class Strbuffer{  
public static void main(String args[]){  
StringBuffer sb=new StringBuffer();  
sb.append("StringBuffer ");
sb.append("is a peer class of string ");
sb.append("that provides much of ");
sb.append("the functionality of strings");
System.out.println(sb);
}  
}  
```
#### Output
```sh
StringBuffer is a peer class of string that provides much of the functionality of strings
```
> 5.Insert the following string 'insert text" into the string "It is used to _ at the specified index position at the location denoted by the sign -
```sh
class Strbuffer{  
public static void main(String args[]){  
StringBuffer sb=new StringBuffer("It is used to  at the specified index position");  
sb.insert(14, "insert text");
System.out.println(sb);
}  
}  
```
#### Output
```sh
It is used to insert text at the specified index position
```
> 6.Reverse the following string 'This method returns the reversed object on which it was called using String Buffer Class
```sh
class Strbuffer{  
public static void main(String args[]){  
StringBuffer sb=new StringBuffer("This method returns the reversed object on which it was called");  
sb.reverse();
System.out.println(sb);
}  
}  
```
#### Output
```sh
dellac saw ti hcihw no tcejbo desrever eht snruter dohtem sihT
```
#### Assignments on StringBuilder Class
> 7.Provide solution for "Assignments on StringBuffer Class“ using StringBuilder class
```sh
class Strbuilder{  
public static void main(String args[]){  
StringBuilder s1=new StringBuilder();  
s1.append("StringBuilder ");
s1.append("is a peer class of string ");
s1.append("that provides much of ");
s1.append("the functionality of strings");
System.out.println(s1);
StringBuilder s2=new StringBuilder("It is used to  at the specified index position using stringbuilder");  
s2.insert(14, "insert text");
System.out.println(s2);
StringBuilder s3=new StringBuilder("This method returns the reversed object on which it was called");  
s3.reverse();
System.out.println(s3);
}  
}  
```
#### Output
```sh
StringBuilder is a peer class of string that provides much of the functionality of strings
It is used to insert text at the specified index position using stringbuilder
dellac saw ti hcihw no tcejbo desrever eht snruter dohtem sihT
```
