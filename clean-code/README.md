

	-------------------------------------------------------------------
	Bad Smells in Code
	-------------------------------------------------------------------
	
	with PPTs
	
	
	Java Clean-code
	=============================
	
	we have
	2 types of programmers/coders
	
	type-1 : syntax & output programmers
	type-2 : clean , best design & performance programmers
	
	
	"be a 'type-2' programmer"
 	
 	
	
	----------------------------------------------------------------------
	Java-language: complete-syntax	
	----------------------------------------------------------------------
	
	-----------------------------------------------------------
	1. java-project
	-----------------------------------------------------------
	
	 proj
	    |
	    |-----p1 ( .java / .class )
	    |  | 
	    |  |------p11
	    |
	    |-----p2
	    |   
	    |   
	 
	-------------------------------------------------------------
	
		
	-------------------------------------------------------------
	2. java-file
	-------------------------------------------------------------
	
	PublicType.java
	-------------------------------------------------------------
	| a. package declaration ( 1 )
	|
	| b. import statements ( n )
	|
	| c. public type ( class | interface | enum | annotation ) ( 1 )
	|
	| d. default types ( n )
	|
	|------------------------------------------------------------
	
		
	
	-----------------------------------------------------------
	3. package declaration
	-----------------------------------------------------------
	    
	    => grouping related java-files as one-module ( package )
	
	why we need package-declaration ?
	
	    => easy to maintain
	    => we can avoid type-name collisions
	
	syntax:
	
	    package root;
	            root.sub1.sub2;
	
	    general recommendation for packgae names
	
	    e.g Employee.java ==> emp ==> EM ==> wissen ==> com
	
	    syntax : package c-type.c-name.p-name.m-name;
	
	    		 package com.wissen.em.emp;        
	

	
	
	
		
	-----------------------------------------------------------
	4. import statement
	-----------------------------------------------------------
	
	 ==> to refer types from differet packages
	
	 e.g project
	
	    project
	    |
	    |
	    |---- p1 ( A.java , B.java )
	    |
	    |---- p2 ( C.java , D.java )
	    |  |
	    |  |--p21( F.java )
	    |
	    |---- p3 ( C.java , E.java )
	    |  
	    |
	    |
	    
	     e.g

        package p1;
        import p2.C; // option-2
        import p2.D;
        // or
        import p2.*;      // best-practice : avoid this type of import
        import p2.p21.F;
        import p3.E;
        public class A{
            B b;
            p2.C c1; // option-1
            C c2;
            D d;
            E e;
            F f;
        }
			
		
		
	-----------------------------------------------------------
	 Quick OO introduction
	-----------------------------------------------------------
	
	 what is object ?
	
	       - data,info,props,attributes -> State
	       - function,method,work,oprn  -> Behavior
	       - address,reference,location-> Identity
	
	       i.e object  ==> SBI
	
	---------------------------------------------------------
	    class  ==> instance(s)
	---------------------------------------------------------
	
	
	---------------------------------------------------------
	OO concepts
	---------------------------------------------------------

    - Abstraction / Interface
        why we need ?
            => easy to use/learn by dependent-object
            => loose-coupling b/w dependent & dependency

    - Encapsulation / Implementation
        why we need ?
            => real-functionality or Implementation
            => hiding complex Implementation thru Abstraction

    - Inheritance
        why we need?
            => re-using common state & Behavior
               from generalized-type to specialized-type objects

    - polymorphism
        - a object should react in different way based on input-strategy
        why we need?
            => can make more re-usable objects
               i.e object can be closed for modification & open for extension

	------------------------------------------------------------------------
	
		
		
	-----------------------------------------------------------
	 Type : class-syntax 
	-----------------------------------------------------------
	
	
	________ _________ class Name [extends] Super-Type 
	[public][abstract]            [implements] I1,I2,..{
	[      ][final]     // state-definition  ==> variables
	        [strictfp]  // constructor(s)
	                    // behavior(s)
	                    // inner-blocks ( static | instance)
	                    // inner-types
	________ ________
	[public] [static]
	[private]
	[protected]
	[       ]
	                   }
	------------------------------------------------------------
	
	
		
	-----------------------------------------------------------
	 Type : interface-syntax 
	-----------------------------------------------------------
	
	
	==> to abstract our obj's Implementation
	
	________    interface Name [extends] I1,I2,I3,..{
	[public]    // constant-state ==> constant variables 
	               ( public & static & final )
	[      ]    // behavior       ==> abstract 
	                ( public & abstract)
	            // inner type(s)
	
	            in java-8
	            -------------
	            default void m1(){}
	            static void m2(){}
	
	            in java-9
	            ------------
	            private void priMethod(){}
	
	           }
		

	-----------------------------------------------------------

		
	-----------------------------------------------------------
	 Type : enum-syntax  
	-----------------------------------------------------------
	
	==> to group related constants as Type  
	
	syntax
	
	    enum Name [implemnts] I1,I2{
	        // constants ==> 
	        ( instances of this enum-type) ==> public & static
	        // constructor(s)
	        // method(s)
	    }
		    
	-----------------------------------------------------------
		       
	-----------------------------------------------------------
	 Type : annotation-syntax  
	-----------------------------------------------------------
	
	 ==> to describe java programming elements to other programs
	
	
	  syntax:
	
        @interface Name{
            //properties ==> public & abstract
        }
		    
	
		
	-----------------------------------------------------------
	
	   
	-----------------------------------------------------------
	syntax:  variable(s)
	-----------------------------------------------------------

	data-types

    1. simple  / primitives ==> values    i.e 8 primitives
    2. complex / references ==> objects   ==> user defined data-types


    e.g

    class Employee{
        static String tnrName; // class's variable
        int id; // obj's variable
        void m(){
            int loc; // local variables
        }
    }
	
	syntax:
	
	   ________    __________ data-type varName=[value/obj's reference]
	   [public]    [static]
	   [private]   [final ]
	   [protected] [transient]
	   [      ]    [volatile]
	
	     local-variables
	   ------------------------
	    -Nil-       [final]    

  
	----------------------------------------------------------- 
	
		
	-----------------------------------------------------------
	syntax:  constructor(s)
	-----------------------------------------------------------
	in java,
	
	    => object creation is 2-steps process
	
	
	step-1 : dynamic memory allocation   ==> 'new'
	step-2 : initialize that memory with obj's values ==> constructor
	
	
	syntax :
	
	    in any class,
	
	
	        __________  ClassName([args]){
	        [public]     // initialization logic..
	        [private]   
	        [protected]
	        [         ]
	
	                    }   
  
  
  		
	-----------------------------------------------------------
	syntax:  method  ==> behavior
	-----------------------------------------------------------
	    ReturnType
	        - void
	        - primitive/reference
	
	______      ________ ReturnType methodName([args])[throws] Exception{
	[public]    [static]           // A/R/L & assignment operation
	[private]   [final]            // conditional executions
	[protected] [synchronized]     // looping executions
	[      ]    [strictfp]         // invoke other methods
	            [abstract]            [return][result]
	            [native]        }
	-----------------------------------------------------------
		
		
		
		
	Naming conventions ( mus follow )
	-------------------
	
	 keywords      ==> lower-case
	 package-names ==> lower-case
	 type-names    ==> pascal-case  e.g JavaEmployee
	 field/method  ==> camel-case   e.h javaEmployee
	 constants     ==> upper-case
	
	------------------------------------------------------------ 


	Source file basics
	
	----------------------------------------------------------------------			
	- File name  
		=> case-sensitive name of the top-level class with .java extension
	- File encoding
		=> UTF-8
    ----------------------------------------------------------------------
    
	Source file structure

	- A source file consists of, in order:

		1. License or copyright information, if present
		2. Package statement
		3. Import statements
		4. Exactly one top-level class
		
		Exactly one blank line separates each section that is present. 	
		
	----------------------------------------------------------------------
	
	Best Practices:
	----------------------------------------------------------------------
	
	
	1. Prefer returning Empty Collections instead of Null
	
		public class getLocationName {
			return (null==cityName ? "": cityName);
		}
	----------------------------------------------------------------------
			
	2. Use Strings carefully
	
		//Slower Instantiation
		String bad = new String("Yet another string object");
			 
		//Faster Instantiation
		String good = "Yet another string object"
			
	----------------------------------------------------------------------		
	3. Avoid unnecessary Objects
	
		import java.util.ArrayList;
		import java.util.List;
		
		public class Employees {
		
			private List Employees;
		
			public List getEmployees() {
		
				//initialize only when required
				if(null == Employees) {
					Employees = new ArrayList();
				}
				return Employees;
			}
		}
	
	----------------------------------------------------------------------
	
	4. Dilemma between Array and ArrayList
	
	
	import java.util.ArrayList;
	
	public class arrayVsArrayList {
	
		public static void main(String[] args) {
			int[] myArray = new int[6];
			myArray[7]= 10; // ArraysOutOfBoundException
	
			//Declaration of ArrayList. Add and Remove of elements is easy.
			ArrayList<Integer> myArrayList = new ArrayList<>();
			myArrayList.add(1);
			myArrayList.add(2);
			myArrayList.add(3);
			myArrayList.add(4);
			myArrayList.add(5);
			myArrayList.remove(0);
			
			for(int i = 0; i < myArrayList.size(); i++) {
			System.out.println("Element: " + myArrayList.get(i));
			}
			
			//Multi-dimensional Array 
			int[][][] multiArray = new int [3][3][3]; 
		}
	}
	
	
	----------------------------------------------------------------------
	
	5. Check Oddity
	
		public boolean oddOrNot(int num) {
			return num % 2 == 1;
		}
		
		vs.
		
		public boolean oddOrNot(int num) {
			return (num & 1) != 0;
		}
		
	----------------------------------------------------------------------
	
	
	6. Avoiding Memory leaks by simple tricks
		
		Always release database connections when querying is complete.
		Try to use Finally block as often possible.
		Release instances stored in Static Tables.
	
	----------------------------------------------------------------------
	
	7. Reserve memory for Java
	
		export JAVA_OPTS=
		"$JAVA_OPTS -Xms5000m -Xmx6000m -XX:PermSize=1024m 		-XX:MaxPermSize=2048m"
	
	----------------------------------------------------------------------
	
		
			
	
	
	
	
		     					