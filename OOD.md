
## How to appeoach OOD questions
### 1. Handle ambiguity
   - Ask clarifying questions, such as who is going to use it aqnd how they are going to use it (six Ws, who, what, where, when, how, why).
### 2. Define the core objects
   - We should consider what are the "core objects" in a system. For example, as a restaurant, the core object should be **Table, Guest, Party, Meal, Employee, Server, Host**.
### 3. Analyze relationships
   - Need to analyze the relationship between the objects. Which object is the **members** of which other objects? Do any objects **inherit** from any others? Are relationship **many-to-many** or **one-to-many**?
   - For example, with the restaurant question, we may have following design:
     - Party have an array of Guests.
     - Server and Host are inherit from Employee.
     - Each table has one party, but each party may have multiple Tables.
     - There are only one host for the restaurant.
   - The assumption sometimes may be wrong or unproper, discuss with interviewee to confirm that.
### 4. Investigate actions
   - Should have basic outline of your OOD. 
   - Consider the key actions that the objects will take and how they relate to each other.
   - May find out you forget some objects and need to update your design.
   - With the restaurant example, we may have following actions:
     - a Party walks into the restaurant and a Guest requests a Table from the Host.
     - The Host looks up the Reservation and if it exists, assigns the Party to a Table. Otherwisr, the Party is added to the end of the list.
     - When a party leaves, the Table is freed and assigned to a new Party in the list.
         
         
      
      
## Desing pattern
### 1. Singleton Class
   - This pattern ensures that a class has only one instance and ensure access to the instance through the application.
   - It can be useful in cases where you have a "global" object with exactly one instance.
   - For example, we may want to implement Restaurant such that it has exactly one instance of Restaurant.
   ```
   public class Restaurant {
      private static Restaurant _instance = null;   //The global object
      protected Restaurant() { ... }
      public static Restaurant getInstance() {
          if (_instance == null) {
              _instance = new Restaurant();
          }
          return _instance;
      }
   }
   ```
### 2. Factory Method
   - The Factory Method offers an interface for creating an instance of a class, with its subclasses deciding which class to instantiate.
   - You may implement it with the creator class being abstract and not providing an implementation for the Factory method.
   - You may have the Creator class be a concrete class that provids an implementation for the Factory method.
   ```
   package com.in28minutes.patterns;
      /*
       * instantiate an object from one among a set of classes based on some logic
       */
      public class FactoryPattern {
        public static class PersonFactory {
          public static Person getPerson(String name,
              String gender) {
            if(gender.equalsIgnoreCase("M")){
              return new Male(name);
            }else if(gender.equalsIgnoreCase("F")){
              return new Female(name);
            } //So on..
            return null;
          }
        }

        static abstract class Person {
          Person(String name){
            this.name = name;
          }
          private String name;
          abstract String getSalutation();
          String getNameAndSalutation(){
            return getSalutation() + " " + name;
          }
        }

        static class Male extends Person{
          public Male(String name) {
            super(name);
          }

          @Override
          String getSalutation() {
            return "Mr";
          }

        }

        static class Female extends Person{
          public Female(String name) {
            super(name);
          }

          @Override
          String getSalutation() {
            return "Miss/Mrs";
          }

        }

        public static void main(String[] args) {
          Person male = PersonFactory.getPerson("Robinhood","M");
          System.out.println(male.getNameAndSalutation());
          Person female = PersonFactory.getPerson("Mary","F");
          System.out.println(female.getNameAndSalutation());
        }
      }
   ```
