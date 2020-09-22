<div align="center">

## A look at Arrays and Pointers


</div>

### Description

This is simply a tutorial that will teach you the basics of arrays and, especially, pointers. Additionally, it'll also show you how arrays and pointers are related to each other.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Abdel Jabbar Baig](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/abdel-jabbar-baig.md)
**Level**          |Beginner
**User Rating**    |4.0 (32 globes from 8 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__3-1.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/abdel-jabbar-baig-a-look-at-arrays-and-pointers__3-4512/archive/master.zip)





### Source Code

<font size=4 face=”verdana”>Purpose</font><br>
<font size=3 face=”verdana”>
The purpose of this tutorial is to show you some relationship(s) between an <b>array</b> and a <b>pointer</b>. I have read some tutorials on C/C++ and the only thing they talk about is what pointers are and what they are used for. They don’t provide any insight about how they are related to arrays. If you know that then it’ll becomes a little easier for you to use pointers in your application.</font>
<font size=4 face=”verdana”>Starting up...</font><br>
<font size=3 face=”verdana”>
First off, your computer memory is divided into a bunch of “boxes” and each “box” has a size of 1 byte. You must know about, at least, the basic model of memory in order to use or understand pointers. Yes! It’ll make your learning curve easier!
Let’s first look at a simple variable...<br>
<i>
int x;
</i>
<br>
In the above line, we are declaring a variable called <b>x</b> which is of an integer type. A computer must somehow store this variable in order to use it in the future. So it stores this variable in the memory. But where? This type of simple variable is stored somewhere in your program’s memory space. An integer has a size of 4 bytes so it’ll occupy 4 “boxes” of your memory. Nothing else can use this memory space because it holds your variable unless your program exists. Yes! You can’t “empty” this memory space after you have put your variable <b>x </b> in there. A memory model containing <b>x</b> would like this:
<br>
| | | | |
<br>
Right now there’s nothing in those 4 “boxes” but as you assign some number to <b>x</b>, some or all of these boxes will be filled up according to the size of your number.
<br>
<i>
x = 4;
</i>
<br>
Now you have assigned a value of 4 to <b>x</b>. You can retrieve the value by writing <b>x</b> like this:
<br>
cout<<x; //This will print 4
<br>
So we can conclude that a value is some sort of data that is held in the memory space reserved for your variable.
<br>
<font size=1>[You:]Hmmm...ya, but the title of this tutorial says that you’ll tell about arrays and pointers so why just a variable?</font><br>
I started with a variable to just show you what a variable contains a value and how it’s organized in the memory. Now we’ll talk about a simple array....<br>
<i>
int x[4];
</i><br>
The above line declares an array of 4 integer. How much memory do you think is reserved for this variable (for now)? It’s not 4 bytes but 16 bytes! I am pretty sure you know about this.;) Now at the same time I’ll start talking about pointers...<br>
A <b>pointer</b> is a variable, as usual, but it’s VALUE is an address of some other variable. You declare a pointer with prefix of * like this:<br>
<i>
int *p;
</i>
<br>
Now if we want to access the value of <b>p</b>, we simply use the name “p”. But as I said before, the pointer’s value will holds some memory address. It is usually the address of another variable but not always! Try this first:
<br>
<i>
int x; //Declare a variable <br>
int *p; //Declare a pointer <br>
p = &x; //p now holds the memory address of x <br>
cout<<p;<br>
</i>
<br>
You use the “&” symbol to access the memory address of a variable - NOT THE VALUE! The above code will print a hexadecimal address of <b>x</b>. See! The actual value of our pointer <b> p</b> holds an address. Now try this:
<br>
<i>
int x = 3; //Declare a variable <br>
int *p; //Declare a pointer <br>
p = &x; //p now holds the memory address of x <br>
cout<<*p;<br>
</i>
<br>
This one will print the actual value of <b>x</b>. But we didn’t really use the variable <b>x</b> to get the value. Because <b>p</b> already holds the address of <b>x</b>, you can use the prefix * to retrieve whatever is on the address that <b>p</b> holds. When we used ,<b>*p</b>, it actually looks at the value of <b>p</b>. The value of <b>p</b> is actually an address of some place in the memory so <b>*p</b> returns the value on that address. I guess now you’re pretty much set with a simple pointer.<br>
Now lets get on our way to the original topic...
Oh forgot to tell you another thing about a pointer. A pointer has 3 “things” compared to a variable which only has 2 “things”. A variable has a value and an address where a pointer has a value (address of some variable), its own memory address (we can get it using <b>&p</b>), and a pointed value which it gets by looking at its value (again, the memory address of another variable). We get the value using <b>*p</b> as I wrote above.<br>
Let’s declare an array now:<br>
<i>
int x[4];
</i>
<br>
It’s 16 bytes long in memory. The start of this array is x[0] so we can get the starting address of this array by using <b>&x[0]</b> (remember you use the “&” sign to get the address of a variable). Now remember this equation for an array (<b>x</b> is an array in this example):
<br>
<i>
x = &x[0];
</i>
<br>
Try it yourself and you’ll see the above equation is true! So if we have an array x, we can simply use <b>x</b> to retrieve the starting address of the array in the memory. We can now simply declare a pointer that points to the start of the array thus the value of our pointer will be the starting address of the array in the memory.
<br>
<i>
int x[4] = {1,2,3,4};<br>
int *p;<br>
p = x;<br>
cout<<&x[0]<<endl;<br>
cout<<p<<endl;<br>
</i>
<br>
You’ll see that both line of outputs will be same. Why? Because, as I said before that <i>x = &x[0]</i>, so
<br>
<i>
<b>
p = x ~ p = &x[0];
</b>
</i><br>
(~ means “is same as”)
<br>
We are just assigning an address to <b>p</b> which is completely legal.:)
Now try outputting the value of <b>*p</b>. You’ll see “1" which is exactly the value of first item in our array! You can also increase the value of the pointer so that it points to next integer in the array. It’ll simply look at the type of the pointer. Because we declared it as an integer, it’ll increase the value of the pointer by 4 bytes (it’ll add 4 bytes to the memory address). Let’s try it:<br>
<i>
#include <iostream.h><br>
void main()<br>
{<br>
	int x[4] = {1,2,3,4};<br>
	int *p = x;<br>
	for(int i=0;i<4;i++)<br>
	{<br>
	cout<<*p<<endl;<br>
	p++;<br>
	}<br>
}<br>
</i>
<br>
The output will look this:<br>
1 <br>
2 <br>
3 <br>
4 <br>
<br>
Exactly what we expected! The statement <i>p++</i> is completely legal. It increases the value of <b>p</b> by 4 bytes so that its address is now pointing to the next item in the array. You’ll get the same output as above by using the following code:<br>
<i>
#include <iostream.h><br>
void main()<br>
{<br>
	int x[4] = {1,2,3,4};<br>
	int *p;<br>
	for(int i=0;i<4;i++)<br>
	{<br>
	p = &x[i];<br>
		cout<<*p<<endl;<br>
	}<br>
}<br>
</i>
<br>
We are using <i>p=&x[i]</i> to point to the next element in the array. Very similar (in this case same) to <i>p++</i> (which is same as<i> p=p+1</i> in case you’re wondering).<br>
</font>
<font size=5>Dynamic Memory Allocation</font><br>
<font size=3 face=”verdana”>
Now we shall look at how you dynamically allocate memory. It’s very useful to use pointers instead of using A LOT of variables (especially of large types like double). As I said before that the memory of a simple variable is never freed unless your program ends. But you can ask the operating system to reserve a certain amount of memory for you at runtime and then you can free the memory whenever needed. You use pointers and some functions to do this job. We’ll use <i>malloc()</i> to allocate a certain amount of memory and then we’ll use <i>free()</i> to free this memory so the operating system or our own program can use it for other purposes. Here is an example of allocating memory:<br>
<i>
int p = (int*)malloc(4); //Make sure you include <stdlib.h>
</i>
<br>
Because <i>malloc()</i> returns a <b>void</b> pointer, we have to cast it as an integer pointer. As you can see that <i>malloc()</i> only takes a parameter that tells the size of the memory to allocate (in bytes). In this case, we’re only allocating 4 bytes so we have allocated memory for only 1 integer (remember that 1 integer is 4 bytes). In this case, we have actually created an array that can only have one element (1 integer). Try this yourself:
<br>
<i>
#include <iostream.h><br>
#include <stdlib.h><br>
void main()<br>
{<br>
	int *p = (int*)malloc(4);<br>
	*p = 5;<br>
	cout<<*p<<endl;<br>
	free(p); //Always do this after the allocation!!!!!<br>
}<br>
</i>
<br>
The output of the above code will be 5.<br>
We allocated 4 bytes (1 integer) and then we set it to 5...you’ll see something amazing in a moment!
Now try this code:<br>
<i>
#include <iostream.h><br>
#include <stdlib.h><br>
void main()<br>
{<br>
	int *p = (int*)malloc(4);<br>
	p[0] = 5;<br>
	cout<<p[0]<< endl;<br>
	free(p);<br>
}<br>
</i>
<br>
Same output! As I said before that we have actually created an array that can have one element. You should also recall that simple equation for an array:
<br>
<i>p = &p[0];</i>
<br>
So we can also say this:
<br>
<i>*p = *(&p[0]);</i>
<br>
Exactly same! If you look closely at the above two complete examples, we are simply following these equations. Now let’s do something with more than 1 element:<br>
<i>
#include <iostream.h><br>
#include <stdlib.h><br>
void main()<br>
{<br>
	int *p = (int*)malloc(8);<br>
	*p = 5;<br>
	cout<<*p<<endl;<br>
	p++;<br>
	*p = 6;<br>
	cout<<*p<<endl;<br>
	p--; //We have to return back to the start of the array or free() will give an error!<br>
	free(p); //Always do this after the allocation!!!!!<br>
}<br>
</i>
<br>
The out will be <br>
5 <br>
6 <br>
We simply allocated 8 bytes (2 integers) and then we assigned 5 to the first element of the array (look up the above 2 equations I wrote). Then we increased the value of <b>p</b> so that it adds 4 more bytes to the memory address that it’s holding thus it holds the next element in the array. I had to use <i>p- -</i> or it’ll give you an error when freeing the memory. I think it wants us the make the pointer hold the starting address of the array? Guess so!
This following code will give the same output as above:
<br>
<i>
#include <iostream.h><br>
#include <stdlib.h><br>
void main()<br>
{<br>
	int *p = (int*)malloc(8);<br>
	p[0] = 5;<br>
	p[1] = 6;<br>
	cout<<p[0]<<endl;<br>
	cout<<p[1]<<endl;<br>
	free(p); //Always do this after the allocation!!!!!<br>
}<br>
</i><br>
Again, we are just using the pointer as an array. We don’t have to increase its value so that it points to next memory address, next one, next one, and so on.<br>
<i><b>NOTE: Statements like “int *p = (int*)malloc(3);” will crash your program because you’re only allocating 3 bytes but an integer requires a minimum of 4 bytes in order to be created!</b></i>
</font><br>
<font size=5>Conclusion...</font><br>
<font size=3 face=”verdana”>
I guess by now you should have a basic understanding of what pointers are and how they’re related to arrays. Happy “pointers” and “arrays”!:D <br>
<i>Please post any errors in the feedback section if there are any in this tutorial. Comments, suggestions, and improvements are welcome.:)</i>
</font>

