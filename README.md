# Game of Three

## How to run the program
* This is a maven project, use any IDE and import as Maven project
* Execute `mvn clean install`
* Under **targer** folder, two jars would be created - **client.jar** & **server.jar**
* Run both the jars in two different terminals using command:<br>
`java -jar server.jar` <br>`java -jar client.jar`
* Results would be printed on console



## Documentation

This application simulates the Game of Three. It is played between two players talking over a network. It is like a client-server interaction. One players starts the game and waits till another player joins. The program exits when a player receives 1 as the message and is declared winner. Details on how to play the game can be read [here](https://github.com/vaibhav1/GameOfThree/blob/master/Game%20of%20Three%20-%20Coding%20Challenge%20JAVA.pdf)


The tool receives as input:
* There is no user input. The game starts automatically when two player join. 


The tool provides as output:
* It prints the desired messages onto console.


The application is modularize into number of classes having specific methods and business logic. The details about classes are as below:

### Client.java

This class acts as a player which when started listens for server and connects with a handshake. If server is not present, it waits. This class extends `WebSocketClient` and joins a websocket connection of the server.

### Server.java

This class acts as a player which when started waits for other player(client). As soon as the client joins, it sends a random number to client and starts the game. This extends `WebSocketServer` and opens a websocket connection for client to join.

### ApplicationUtils.java

Contains utility method used in the application.

### Constants.java

Contains application constants.


### NOTE: 
Currently, no test cases are written for the application because of time shortage. But we can test Client and Server separately. Following are the test cases:

* Message Authenticity. If the message is anything apart from **DONE**,**SUCCESS**,**FAILURE** or a number, it should fail.
* Client can connect to the Server
* Server can connect to the Client
* Client can send message
* Client can receive message
* Server can send message
* Server can receive message


