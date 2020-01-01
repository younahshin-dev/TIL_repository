# Collection FrameWork 

**1. Synchronized Collection**
In multi-thread programming, shared Object is needed Synchronization for remain consistency 
because many threads can approach an Object at the same time.
  
  >ex) static Collection synchronizedCollection(Collection c)
  
**2. Unmodifiable Collection**
Unmodifiable Collection is Used for protecting data which is saved at collection
  
>ex) static Collection unmodifiableCollection(Collection c)
  
**3. Singleton Collection**
  When you wanna make a collection which can save only one object. you can use Singleton Collection
  
>ex) static List singletonList(Object o)
  
**4. Making Collection that can save only one kind of object**
  
>ex) 
List list = new ArrayList();
List checkedList = checkedList(list ,String.class); //only String object can be saved

      
      
      
      
