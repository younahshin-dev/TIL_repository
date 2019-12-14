<h2> Chater10. date, time and formatting </h2>

Calendar.getInstance() 
 - returns different Calendar by locale, nation of Systems
   ex) Thailland -> BuddistCalendar, Japan -> Japanese Calendar the others GregorianCalendar
   
Why I can't use constuctor of the Calendar Class but use getInstance() 
 - Make the development process simple. You can implement the behavior with minimal changes.

What does static mean at getInstance()
 - there is no instance value in getInstance and It doensn't call instance method.
 - What if it's not static getInstance() can be used after creating Calendar object
   but you can't create beaouse it's an abstract class.
   
