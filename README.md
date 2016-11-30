Brain Academy
============= 
#Java Core Course

##Laboratory Work 2.10
###Theme: Wrapper classes

####Laboratory Work 2.10.1.
Create new project called WrapperDemo.  
Add package “com.brainacad.oop.testwrapper”.  
Create class Main with method main(). In main() method declare few xN local variable of
Integer class and initialize it with same value (lower then 128), but in different manner.  
For example:  
Integer x1 = 10;  
Integer x2 = new Integer(10);  
Integer x4 = Integer.valueOf(10);  
Integer x5 = Integer.parseInt(“10”);  
Compare it to each other using “==” and equals(), print result to console.  
Do the same, but for value higher than 128.  
Solution:
```java
private static void baJavaCoreLabWork_2_10_1() {

        Integer x1 = 10; //*
        Integer x2 = new Integer(10); //**
        Integer x4 = Integer.valueOf(10); //***
        Integer x5 = Integer.parseInt("10"); //****

        System.out.println(x1 == x4 && x4 == x5); //Same object references: based on CIO
        System.out.println(x2 == x5); //Different object references: CIO wasn't launched
        /*
         *     * - initialized by integer number primitive literal
         *         in range of byte type (from -128 to 127), which
         *         launch Caching Integer Objects (CIO) mechanism
         *         for Wrapper class Integer.
          *        CIO creates Integer object's pool - number of
          *        Integer type variables, which references to
          *        the same object in Heap in case, if its values
          *        are equals.
          *        For example:
          *            Integer i1 = 127;
          *            Integer i2 = 127;
          *            //i1 and i2 references to the same object in heap
          *
          *            Integer i3 = 128;
          *            Integer i4 = 128;
          *            //i1 and i2 references to the different objects in heap,
          *            //because of its values, which are out of CIO range
          *
          *        ** - Integer instance created with Constructor produces
          *             new object in Heap.
          *
          *        *** - Integer.valueOf() implicitly invokes Integer.parseInt()
          *              method, which does not create new Integer object in Heap,
          *              returning primitive (value) int type
          *
          *        **** - Integer.parseInt() return a primitive (value) int type.
          *               So it does not create new Integer object in Heap
          */

        Integer y1 = 128; //*
        Integer y2 = new Integer(128); //*
        Integer y4 = Integer.valueOf(128); //*
        Integer y5 = Integer.parseInt("128"); //*

        System.out.println(y1 == x4 && y4 == y5); //Out of CIO range: different objects
        System.out.println(y2 == y5); //Constructor used: different objects

        /*
         *    * - any Integer class instantiating with
         *        primitive value out of byte type
         *        range (from -128 to 127) will result
         *        creating new object with no CIO launching
         */
    }
```