# Game of 3 Test

The goal here is to demonstrate the possible implementation of the backend for the Game Of Three adopting
an open source framework to build microservices adopting the DDD, CQRS and EventSourcing patterns.

The framework is called Axon and it is mantained by the OpenIQ company: 

    https://axoniq.io/ 

This is my first attempt to use Axon which I find an extremely interesting technology.

Its main winning points is the approach that the devleloper needs to follow in order to arrive to a solution:

The programmer must think in terms of the business model trying immediately to decide what is the Root Aggregate
of the problem and then in Test First fashion MUST approach the problem in terms of Command that can be sent that
may have an impact on the State of the aggregate and MUST think in terms of the events that MUST be generated.

The framework then offers a rich set of Annotations that drive the developer towards the solution and most importantly
developing starting with a MONOLITH. 

Because Axos adopts the location transarency then it is only after that the business logic has been implemented
that it is possible to fragment the monolith and deploy separately the command component and the query component.

Also it offers a vast choice of technologies that can be used to implement the event sourcing/us (i.e. Kafka, ActiveMQ, RabbitMq)
as well DataSources SQL and/or NO_Sql for the Query model projections and/or the validation side of the CommandModel


# GAME of Three solution

In this example, I have tried to keep the solution to the very minimal focusing on the DDD/CQRS aspects rather than 
actually fullfilling the full game which is quite trivial and not really the real meat of the test.

So I followed the Axon proposed approach:

### AGGREGATE
 
Decide what is the Root Aggregate: in this example it is clearly the Game and then attached to it the players, the current latest number and so on.
  
The Aggregate is implemented in:
    
    GameAggregate.java

This is a clear example of a Non-Anemic model implementation. 

      
### Command/Events as messages.  

Define in one Kotlin  file the command and events that mode the state of the system:
   
    game/coreapi/message.kt 
    
Kotlin is particularly effective to provide in very concise way all the commands and events in the system.    
    
### Command and Query models

    game/commandmodel
    game/querymodel
    
### EventSourcing

I adoped the default embedded EventSource provided by Axon to keep it simple
    
### TEST FIRST

Axon provide test fictures that allow the user to write tests in given()/when()/expect() fashion which is
formidable because allows the programmer to write the tests thinking about commands and events (or error) to 
be expected.

    test/jave/io/axoniq/labs/game/commandmodel/GameAggregateTest.java 






## Installation
This project requires JDK 8 and maven for building and testing it. 

Install Java on linux using this command:

    sudo apt-get install openjdk-8-jdk
    
Install maven    
    
    sudo apt-get install maven
    
This project contains the source code for the Game of 3 Axon test. 


## How to build

    git clone https://github.com/antoniosignore/axon-game-3.git
    cd axon-game-3
    mvn clean package


## How to run

The app is composed of a remote H2 database which needs to be executed in standalone mode
and the Game of 3 server itself.

In order to do these operation the quickest is to start your intellij project:

Open a terminal in the directory: axon-game-3 and import the project:

    idea .

In the Project window navigate to the directory:

    axon-game-3/game/src/main/java/io/axoniq/labs/game


Then run the database:

    From IntelliJ Run the 'Server'
    
If correctly started you will see on console the message:

    Database running on port 9092
    Press any key to shut down

Then start the Game Of Three backend:

    GameOfThreeScalingOutApplication


Solutions
---------








