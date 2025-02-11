Lesson 5.02 — Object State & Behavior
====================================================================================================

Overview
--------

### Objectives - Students will be able to

- **Describe** classes, objects, and client code.
- **Predict** the output of the code that uses objects.

### Assessments —_Students will

- **Complete** WS 5.2 individually or in pairs.

### Homework — Students will…_

- **Read** BJP 8.1 up to “Mutators and Accessors”
- **Complete** self-check questions #9-11, 13-16

### Lesson Theme Considerations - 2 Options

1. Standard Radio  
2. Pokemon Game

Materials & Prep
----------------

- **Projector and computer**
- **Whiteboard and** **markers**
- **Option 1 Worksheet** - classroom copies of [Book Tracker][]
- **Option 2 Worksheet** - Classroom copies of [WS 5.2][]
- Teacher access to CS Awesome **[Lesson 5.6: Writing Methods Class Lesson Plan][]** Sign up at [CS Awesome AP CSA Java Curriculum][]
- Access to Dr. Nguyen **[Writing Methods][]** slide deck
- Access to CS Awesome **[5.6. Writing Methods][]**

You should read the introduction on the Bulbepedia website so you understand the main ideas behind
the Pokémon game. If you search YouTube, you can find recorded games to see how a Pokémon battle
starts, progresses, and ends.

Pacing Guide
------------

| Section                                 | Total Time |
|-----------------------------------------|-----------:|
| Bell-work and attendance                |       5min |
| Introduction                            |   15-30min |
| Student practice: WS 5.2                |      25min |
| Students trade work, check, and turn in |      10min |

Procedure
---------

Yesterday you asked students to do some research on what fields, constructors, and methods would be
appropriate for building a custom-made Pokémon class. Solicit students’ input before you work
through a Pokémon class example.

Ask students what they think a Pokémon class should include, and why. Encourage students to argue
for or against certain design features in the Pokémon class. Should the class include all Pokémon
stats? Are there any behaviors (methods) you think all instance objects should have? What are some
examples of instances of the Pokémon class? (Any individual Pokémon is an instance of the Pokémon
class, for example Pikachu, Bulbasaur.)

### Bell-work and Attendance `[5 minutes]`

## Option 1 - Standard Radio

### Introduction/Recap `[10 minutes]`

Ask students in the following discussion to review from the reading.

- What is a field?
- What is an  method?
- What are two ways that we can write a translate instance method?

```java
public void translate(int dx, int dy) {
    x += dx;
    y += dy;
}
```

```java
public void translate(int dx, int dy) {
    this.x += dx;
    this.y += dy;
}
```

### Lecture `[15 minutes]`

#### Mutator Explanation

Explain to students that the translate method is an example of a **mutator**.
Define Mutator: A **method** that modifies the object's internal state.
Generally, a mutator assigns a new value to one of the object’s fields.

In a radio, the mutators would be things like:

- On/Off switch
- Volume knob
- Tuning dial
- Preset station selection switches

#### Mutator Conventions

It is common for a mutator method’s name to begin with “set”

- setVolume
- setStation

What was the return type of our translate instance method?

- Usually mutators methods have a void return type; they change the state of the object but have nothing to return

What were the formal parameters of our translate instance method?

- Mutator methods often accept parameters that specify the new state of the object, or how to modify the object’s current state

#### Accessor Explanation

**Accessors** form a second important category of methods. **Accessor** is a  method that provides information about the state of an object without modifying it.

- Generally, an accessor returns the value of one of the objects fields
- In a radio, the accessors might:
  - Tell us the current station
  - Tell us the current volume
  - Tell us whether the radio is turned on

What are some accessor methods you have used on other classes?

#### Accessor Conventions

It is common for an accessor method’s name to begin with “get” or “is”

- getVolume
- getStation
- isTurnedOn

Accessor methods usually do not have a void return type

- What might the return type be for each of the above three methods?
- Accessor methods don’t usually have any formal parameters

### Discussion `[10 minutes]`

Ask students if they have any questions about **mutators** or **accessors**?

Remind students that we’ve created fields in our classes that state what data will be stored in all instance objects.

- What would be a good method to include in all instances of the Student class?
- What would be a good method for all instances of the Dog class to have?
- What method should all forecasts have, no matter what area you’re forecasting for?

## Option 2 - Pokemon Game Approach

### Introduction `[15-30 minutes]`

1. Ask students to review their notes from the day before, reminding you what the main components of
   a class are. (Fields, methods, constructors, and encapsulation.)

   - The syntax for declaring a field is the same as the syntax for declaring normal variables (type
     followed by semicolon). If your students are feeling confident, invite a volunteer up to
     declare a field on the whiteboard for your Pokémon class.

   - Remind students that fields signify that EVERY instance object of the class should have that
     variable inside it, so as their example, they should declare a trait that every instance of
     Pokémon will have.

   - Your example should look something like this:

     ``` Java
     public class Pokemon {
         private int hp;       // Pokémon stats include hit points, or "HP"
         private int attack;
     ```

   - Students will probably start volunteering additional examples once they realize that stats make
     for good fields. Some other fields include:

     ``` Java
         private int defense;
         private int specialAttack;
         private int specialDefense;
         private int speed;
     ```

   - For the sake of simplicity, try to keep students to 2 or 3 fields for now. Don’t just
     arbitrarily declare this; encourage students to think about how we use classes and objects as
     models. Ask them to criticize your current model.

     - Does it need to be complex yet?

     - If we opt for simplicity, what are we yielding in sufficiency/robustness?

     - If students agree to keep it simple for now, remind them that they can make a design choice
       to increase complexity later. Most programmers start with a simpler model and build up as
       they flesh out their program.

     If students need additional examples for appropriate fields, lead students through the
     following examples (having them add as much of the code as possible). Make sure that students
     can justify their choices in fields and explain why they would include some data and not
     others. At every opportunity, repeat the fact that they are **using data to model the real
     world**:

     ``` Java
     public class Student {
         private String name;
         private int    gradeLevel;
         private double gpa;

     public class Dog {
         private String breed;
         private double weightInKg;

     public class Forecast {
         private double  windSpeed;
         private String  windDirection;
         private boolean tornadoWarning;
     ```

2. Remind students that in the previous class they learned that objects combine both state (data)
   and behavior (methods). So far we’ve created fields in our classes that state what data will be
   stored in all instance objects.

   - What would be a good method to include in all instances of the Student class?
   - What would be a good method for all instances of the Dog class to have?
   - What method should all forecasts have, no matter what area you’re forecasting for?

3. Let’s add a method inside the object that will report information about the data stored in our
   Pokémon objects. Because this method is being written within the object, we refer to it as an
   instance method (it is not in client code).

   - Pokémon get an effort ribbon if their combined stats exceed a certain value. What would the
     method sumStats look like?

     ``` Java
     public int sumStats() {
         return hp + attack + defense + specialAttack + specialDefense + speed;
     }
     ```

   - Since this method gets information about your Pokémon instance, but doesn’t change any of the
     values, what do you call this type of method? (_Accessor_)

   - Is this client code? (_No, it is part of the Pokémon class, which is why we call it an instance
     method._)

4. Let’s write another instance method that will let us change the state (data values) stored in our
   Pokémon instance objects. In the game, what can you do to cause your stats to change? (Win
   battles, consume vitamins)

   - Pokémon can use vitamins to boost their stats. Here are some example vitamins for you to use at
     the board:

     - **hpUp:** + points to HP
     - **protein:** + points to attack
     - **iron:** + points to defense
     - **zinc:** + points to specialDefense

   - In keeping with our earlier example, a method to update stats with vitamins would look
     something like this:

     ``` Java
     public void consumeVitamin (int hpUp, int protein) {
         hp += hpUp;
         attack += protein;
     }
     ```

     _Students may want to add other vitamins._

5. Ask students if they can deduce the syntax rules for instance methods based on the two methods
   we’ve written so far:

   ``` Java
   public <type> <name> (<type <name>, <type> <name> …) {
       <statement>
       <statement>
       …
   }
   ```

   - See CS Awesome [Lesson 5.6: Writing Methods Class Lesson Plan]
   - The slide deck for this lesson and Using the enhanced for and array algorithms are located on [Dr. Long Nguyen] GitHub at [Writing Methods] and can be used to review this topic
   - Have students navigate to CS Awesome [5.6. Writing Methods] and complete Activity 1-4

6. Since we know that all instances of our Pokémon class will have initial values to their stats, we
   could create a constructor to initialize all of our values.

   - It often doesn’t make sense to have Java auto initialize our stats to 0, so we build our own
     constructor that requires us to pass initial parameters.

   - Have students point out to you the class, fields, and constructor:

     ``` Java
     public class Pokemon {
         private int hp;
         private int attack;

         public Pokemon (int hitpoints, int a) {           // In a complete version you
             hp = hitpoints;                               // would include all stats.
             attack = a;
         }
     }
     ```

7. Now that you used the constructor, it’s very easy to create objects! What would an instance of
   the class Pokémon be? (Any Pokémon type; Pikachu, Bulbasaur, Squirtle, etc.)

   ``` Java
   Pokemon pikachu = new Pokemon(70, 120);
   ```

   If students are getting excited about this example, ask them to look up types and their typical
   initial values (IVs) for hit points and attack. Let them practice constructing new instances of
   the Pokémon class.

   - Ask students how you would add the Pokémon type (electric, ground, rock, etc.) to the
     constructor.

   - Point out that it is incorrect to construct a Pokémon object without passing initial hitPoints
     and attack parameters. Since you wrote a custom-made constructor for your class, Java won’t let
     you call new Pokémon() anymore. Instead, your code just won’t compile.

## Student Practice: WS 5.2 `[25 minutes]`

---

#### Emphasize with students...

#### Big Ideas - Personal design interests require the evaluation and refinement of skills

This activity helps you develop specific classes and methods that will implement parts of a pokemon game. As you progress through the remainder of the course, you will learn more about the components required to create a full game.

As you complete these tasks, think carefully about the skills you are developing. What components of the pokemon game implementation have been difficult for you to implement? What components seem easy? What can you do to improve your skills so that you can add extensions and additions to the program that go beyond the basic instructions?

Constantly evaluating and refining your skills will allow you to create more complex programs and will allow you to be creative when it’s time to implement your final project in the course.

---

1. Remind students to use their textbooks, notes, classroom resources, and online aids to help them
   answer the questions on WS 5.2.

2. Encourage students to work independently until the last 10 minutes of class.

### Students trade work, check, and turn in `[10 minutes]`

Have students trade and error-check each other’s papers. Error-checking partners should write their
name on the sheets to share credit for the work.

College Board Topic Questions
---------------------------------

After this lesson, students will be able to answer questions from the College Board Unit 2 Topic Questions 2.1 Objects - Instances of Classes and Unit 5 5.1 Anatomy of a Class and 5.9 this Keyword

Accommodation and Differentiation
---------------------------------

In classes where reading comprehension is an issue, have students work in pairs today. If you have
already created the small group assignments for the next class (see LP 5.3), you can assign pairs
that will be in the same group tomorrow.

If you have students who are speeding through this lesson, invite them to create a diagram showing
the different parts of a class and instance object that we introduced today. If the diagram is
correct and thorough, give the student materials to turn the diagram into a large-format poster for
the classroom.

Teacher Prior CS Knowledge
--------------------------

- In _Novice Java Programmers’ Conceptions of `Object` and `Class`, and Variation Theory_ by
  Eckerdal and Thuné, novice students view objects at three levels:

  Objects:

  + Object is experienced as a piece of code
  + As above, and in addition object is experienced as something that is active in the program
  + As above, and in addition object is experienced as a model of some real world phenomenon

  Class:
  + Class is experienced as an entity in the program, contributing to the structure of the code
  + As above, and in addition class is experienced as a description of properties and behavior of
    the object
  + As above, and in addition class is experienced as a description of properties and behavior of
    the object, as a model of some real world phenomenon

  Software developers are adept at seeing objects and classes as models for both real and abstract
  constructs.

- For the purposes of the AP test, all fields are private. This ensures good programming practice
  for beginning students because it forces the use of accessors methods: accessors and mutators. The
  default access for fields when no access modifier is specified is package private. This means all
  classes in the same package where the variable is defined can access the field.

Misconceptions
--------------

Students add static to class method definitions. Now that Classes have been introduced, static
methods that are tied to the class are often confused with non static methods. Students can call
static methods without creating an object, however, an object must be created first and the
non-static method can be called.

Videos
------

- BJP 8-2: _Defining a Class_
  <http://media.pearsoncmg.com/aw/aw_reges_bjp_2/videoPlayer.php?id=c8-2>

- CSE 142, _Object Oriented Programming State_ (19:54–26:25)
  <https://www.youtube.com/watch?v=0IGWknpGPhM&start=1194>

- CSE 142, _Object Oriented Programming Behavior_ (31:44–42:44)
  <https://www.youtube.com/watch?v=0IGWknpGPhM&start=1905>

- CSE 142, _Object methods_ (45:32–49:41)
  <https://www.youtube.com/watch?v=0IGWknpGPhM&start=2732>

Forum discussion
----------------

[Lesson 5.02 Object State & Behavior (TEALS Discourse account required)](http://forums.tealsk12.org/c/unit-5/5-02-object-state-behavior)

[Dr. Long Nguyen]: https://longbaonguyen.github.io/courses/apcsa/apjava.html
[Teaching CSAwesome google group]: https://groups.google.com/forum/#!forum/teaching-csawesome
[CS Awesome AP CSA Java Curriculum]: https://sites.google.com/css.edu/csawesome/teacher-materials

[WS 5.2]:   https://raw.githubusercontent.com/TEALSK12/apcsa-public/master/curriculum/Unit5/WS%205.2.docx
[book tracker]:   https://raw.githubusercontent.com/TEALSK12/apcsa-public/master/curriculum/Unit5/WS%205.2.1.docx

[Lesson 5.6: Writing Methods Class Lesson Plan]: https://docs.google.com/document/d/1cjzzkbT6Y6zrUxqdw0QOiIzTu-AlHplEVZnlVH_wxcE/edit?usp=drive_web
[Writing Methods]: https://longbaonguyen.github.io/courses/apcsa/lecture14.ppt
[5.6. Writing Methods]: https://runestone.academy/runestone/books/published/csawesome/Unit5-Writing-Classes/topic-5-6-writing-methods.html
