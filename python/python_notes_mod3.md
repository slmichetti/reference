Python Module 3

## Types of Storage

* Persistent storage - things on disk; permanent
* ephemeral - things in memory; temporary

Variables are internal; specific to one program
* maximum size is limited by the computer memory

Files are global; usable by more than one program

Files:
* have a name
* located inside a directory or folder (which has a name)
* has a full path name that includes the dir name and the file name

## Sorting Files

Example: sorting photos file on your computer and moving them into their own directory
	write a piece of code that moves them around

Steps the program will have to do to organize:
* look at what files exist
* make a list of place names
* make a directory for each place name
* move files into the right directories

With a program that uses more than one loop
	for each file in the directory:
		extract place name
		put each place name in the list

	for each place name 
		create a directory for it

	for each file in the new directory:
		move it to the new directory

## OS

The OS module in Python provides a way of using operating system dependent functionality. The functions that the OS module provides allows you to interface with the underlying operating system that Python is running on

**import os** to access the functions

**os.mkdir** = Make a new directory
* takes a path as an argument 
	* os.mkdir("Organized")

**os.rename** = Changing the name or directory of a file
* takes two arguments called src and dest (source -current orig name and dest is the new name)
	* use rename to move because the real name of a file is its whole name, so moving is just changing part of its name

**os.listdir** = List files in a directory
	os.listdir("Pathname")
	list of the file names in that dir
	to move - when you specify a file name to the os fx, its specific to the current working directory

**absolute path**
* starts with a slash(/) ex. /Users/sheri
* good idea to refer to files and directories that are part of the operating system

**Change your working directory**
os.getcwd() - lets you find out your current working directory
	answer is a string, which can be put in a variable and used
os.chdir() lets you change it
os.listdir - lists files in a directory
	default to looking at the working directory but can list another dir if told in a function
os.mkdir - make a new directory
os.rename - move or rename a file (works like mv command in the shell)
	must say the name you wnt the file to have
	os.rename("filename", "directory/filename")

File paths differ between windows, macs/linux
	windows directories and file names separated backslashes
	mac/linux separated by forward slashes
	so cant use simple string appending for directories and file parts

os.path.join("name", "name.py")
	contains functions for working with directory functions
	important for writing code that works on both types of computers

portable code - Python allows you to write code that works on different operating systems 

**Extract Place**
takes filename string and returns a part of the string
extracts the place name out of a file name

filename.split - breaks up a sting based on the character you select


## Script Footer

when you import a module, python runs all the code in that module
	if you want there to be a difference between importing a file and running it
	use the if statement 
```
if __name == '__main__':
robot_move()
```

**"dunder variables"** for double underscore
dunder name variable contains name for the current module
__name__ = '__main__' when robot.py is run on the command line, so that if statement will evaluate to True and robot_move() is called, but will not return true when its being imported, so code doesn't run

## Py Codestyle

Checking your code against rules in the Python style guide for "good code style"

**install pycodestyle**
	pip3 install pycodestyle

run
    pycodestyle stylish.py and it evaluates the code
    no problems, nothing will print

## Filtering
Create a solution to have your contents read by placing it in a string and work on it from there

One approach
* read the file contents into a string variable
* for words in your filter list
	* is the word int he file-contents string?
		* if yes, alert
	* at the end, return message it does not contain any items from filter list

Another approach
* read file contents into a string
* split string into a list of words (using the spaces between words; returns a list of words instead of one big string)
* for word in the file-contents list:
	* is the word in the filter list?:
		* if so, alert
	* if no, run

Goal is to create the most efficient process to address the problem

## Opening and Reading a File

Telling python to open a file and python gives a file object
```
	my_story = open("my_story.txt")
```
tells the system you want to work with this file and puts a file object into the variable my_story
will only work if this file exists and is in the current working directory. if its somewhere else, you'll need to use the longer file/path name

Creates an open file object
* put it in a variable
* pass to a function
* call methods on it
* put it in a list
* etc

The file object needs to be closed when you're done.

Open file object - lets us use the data in the file
	* another piece of data that ca
* Several dif ways to read the contents of a file:
	* Using read method on the file object (this is the simplest)
		* contents = my_story.read() creates a new string variable and puts all the contents into the string
		* file size should be considered with this option.

## Closing a File

Tells your operating system you're done with the file and it can be closed
Once its closed you can no longer read from that file
```
	my_story.close()
		file.close()
```

with open("filename") as filename:
```
	print(filename.read())
```

inside this compound statement, filename can be used as a variable
when the with block ends, the file will automatically be closed (even if kept in a list)

## Improving efficiencies on functions

Split contents into a list of words and use split on the string using the space character

consumes input from the file one line at a time instead of all at once
	use another feature of open file object
	for line in filename: use an open file object in a for loop, the loop variable gets assigned to each line of the file. Loop will exit when you run out of lines in the file

## Refactoring for Improving Efficiency

When a piece of code or a function gets so long that its hard to describe exactly what it does in a simple sentence, its a good time to extract some of it out and put into another function - esp if it can be used for another purpose somewhere else 

Examine your code, can it be put into a function.

Debug by adding print statements for you to see what the code is doing

**Strip Function**
if you pass string.punctuation into the strip function on a string, all punctuation will be removed from that string
	**import string / in a variable called string.punctuation**
	this passes in all the punctuation that needs to be considered for removal

**Lower()**
The method lower() returns a copy of the string in which all case-based characters have been lowercased.

Syntax
Following is the syntax for lower() method −
```
str.lower()
```

## Writing Output to a File

* Open a file in write mode
* Additional option to the open function. By default, open fx takes the name of the file, and returns to you an open file object that is in read-only mode.
* Add an extra argument in the open fx call "w" to write
	* open("filename", "w")
		When you open in write, you are telling os that you are going to replace the existing file
		Use a new filename that doesn't exist yet. Open fx will create the filename if it doesn't exist

* Use write method on that file
	* Write to a file using the write method
		* write("filename")
			* takes an argument, which is the string you want to write to the file
			* repeatedly write to a file by calling the write method several times
				* can write in a loop
```
	f = open("output.txt", "w")
	for num in range(100):
	    f.write(str(num))
	    f.write("\n")

	f.close()
```
			* the only things that you can write to a file is strings
				* if you have numbers or another value, you have to convert to a string with the string function or format it into a string using the f function

* close the file when you're done writing to it
	* Closing the file to tell the system you are done with it
		* call the close method or close it using the with compound statement (similar to the open statement)
	* close on each file you open; or you can use a with statement such as with open("myfile.txt") as myfile: which will automatically close the file when the statement is finished.

Readfile vs writefile
'read-only mode allows you to read, not write to the file'

```
	readfile = open("filename.txt") 
	
	writefile = open("newfile.txt", "w") 

	writefile.write("writing on my file, writing on my file\n")
```

## Class Definitions

Objects belong to a class

Check what class an object belongs to
* isinstance - allows you to check if a particular object belongs to a particular class
	* ex: isinstance(ty, turtlTurtle) - returns True
	* Tells us about the relationship between objects and their classes
		* object is an instance of a class; or that it belongs to the class

**Behavior of the object is defined by its class**

* Type function
	* type("string object") type(integer)
	* class an object belongs to is set when the object is created
		* when the class is called; calling it is a way to create new objects of that class
			* whenever the name of the class is used in a call statement - telling python to construct a new object of that class

**Class**(py) definition: a template or blueprint for creating objects and is used by calling it, when you call it, it returns a new object of that class. After which you can use that object (ex by calling methods on it)

Objects created by the same template, will share common charcterstics

## Defining a New Class
Define with the "Class statement" - a compound statment
	class nameofclass:
		info indented under - need to add a definition for each method you want the class to have
* methods are the behaviors you want that class to have
	* method definitions look like function definitions, they are just written inside a class 
	* first parameter in a method definition - object itself is passed into the parameter
		* where the objects code gets to refer to the object iself
			* the common parameter in the class definition is  (self)
				ex: def speak(self):
					print("woof")

```
class Dog:
	scientific_name = "Canis lupus familiaris"

	def __init__ (self, name):
		self.name = name
		self.woofs = 0  #keeps track of how high the dog is supposed to count

	def speak(self):
		print("Woof!")

	def eat(self, food):
	    if food == "food":
	      print("Yummy food!")
	    else:
	      print("That's not really food.")
	
	def learn_name(self, name):
		self.name = name 
	
	def hear(self, words):
	    if self.name in words:
	    	self.speak()

	def count(self)		
		self.woofs += 1
		for bark in range(self.woofs):
			self.speak()

class Cat:
	def speak(self):
		print(random.chocie(["Meow Meow!", "Purr!"]))

class Pitbull(Dog):
	origin = "England"

	def speak(self):
		print("WOOF!")

***************************
bella = animals.Dog()
bella.learn_name("Bella")
bella.name
bella.count()

```

## Class Level Variables

Classes can have other info besides methods. They can also have variables
* Class level variales
	* created using assignment statements inside the class definition but outside any method definition
* A variable defined inside a class, that variable is available to every object of that class
	* items that can be applied to all items in that class

## Instance Level Variables

Naming of variables doesn't matter, as long as your consistent.
Objects do not know what it was called.
The variable points to the object, but it only goes one way. The variable knows what object it points to, but the object does not know the variable

When you dont want to apply the variable to every object, you create an instance level variable
* Use self. -- self parameter on methods
	inside a method you can write an assignment statement to a variable starting with self. to save informaiton to a single specific object you called the method on 

* dot operator - allows you to access instance level variables

Allows you to have individual objects remember something about itself (vs something in commong for all members of the class)

## Initializers

Create things when you construct a new object and pass it in a call thats constructing it
(ex: naming a dog when its created)

* creating method called dunder init method
	double underscores around names to indicate they have a special code
	* can be defined on any class and will be called whenever a new object of that class is constructed
	* this requires you to pass in a variable when creating the object instead of it being emppty

```
	def __init__(self, name):
		self.name = name
```

## Storing Information on instances

creating objects that remember things
	ex: dog_count
		first time called, dog speaks once, second time, 2x, third time, 3x, etc
		Each dog keeps track of its own count

By creating the code in the initializer, it ensures each seperate dog keeps track of its own count


## Subclass (Inheritance)

Create classes based on other classes
	Ex. pitbull = type of dog

Inheritance (sub-classing) - tells python to create a new class that pulls in all of the behavior for an existing class but can change or override behaviors

class Husky(Dog): 
	inside the new class definition you can add any variables that differ from the parent class
	define the variable and method within the subclass

Inheritance refers to how the subclass gets their behavior from the defined class

isinstance function lets you ask if a particular object belongs to a particular class - when you have an object taht belongs to a subclass, isinstance will also return info on its parent class

issubclass() - asks if an object is a subclass of another class

## Placeholders: Methods that do Nothing

Create placeholder methods that dont do anything but can be replaced in a subclass

**pass** - can be used in class or method definitions to indicate that it's intentional for the definitions to do nothing. In python, you cant have a function or class that contains no statements.

```
	class Dog:
		def do_trick(self)
			pass
	class Pitbull(Dog):
		pass
	class TrainedPitbull(Pitbull):
		def do_trick(self):
			print("The pitbull spins in the air and turns briefly into a chicken")
```

## Is-A vs Has-A relationship

Has to do with the object, but isn't the same as the object.
	Ex Dog park is not in the Dog class. 

IS-A:
	* a Pitbull is a dog

HAS -A
	* a dog park is not a dog, it has dogs in it

class DogPark:
	def __init__ (self, dogs):
		self.dogs = dogs

The dog park class would set up an instance variable setting up a list of dogs that are in a particular dog park
	Can have methods that are specific to the park

```
def rollcall(self):
	print ("Dogs in Park:")
	for dog in self.dogs:
		print(f"{dog.name}")
	print()
```

## Super

```
import turtle

class BigOrangeTurtle(turtle.Turtle)
	def __init__(self):
		self.color("orange")
		self.width(10)
```
subclass replaced the dunder init method and removed all the setup that was done under the parent class.

in the dunder init - need to call the dunder init method for the parent class
	**super().__init__()**

calling the super function and then accessing the dunder init function inside it
	when code inside a method def calls the Super function, it gets back a version of the same object, but connected to its parent class

by using super like this, you're saying you dont want to completely replace the init method

when you're making a subclass of a class that does a complicated setup, you'll want to use this and call them as part of the child class

Ex:
```
class BigBlueTurtle(turtle.Turtle):
   def __init__(self):
     super().__init__()
     self.color("blue")
     self.width(10)
```
