Game of 3 Application
============================


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

    /home/antonio/pippo/axon-game-3/game/src/main/java/io/axoniq/labs/game


Solutions
---------
