# DevOps Class Assigments CA3-Part1

## Introduction

This is a technical report for Class Assignment CA3 - Part 1 of the DevOps course offered by "Switch Dev," authored by Wagner Paiva, student number 1231863.

This report outlines the steps taken to complete the assignment, including the commands used, challenges faced, and solutions implemented. The tutorial section provides a step-by-step guide to the assignment tasks.

After installing the Ubuntu 20.04.3 LTS on the Virtual Box, the following steps were taken to complete the assignment:

### 1. install git
```bash
sudo apt update
sudo apt install git
```

### 2. install maven
```bash
sudo apt install maven
```
### 3. install java 17
```bash
sudo apt install openjdk-17-jdk openjdk-17-jre
```
verify version:
```bash
java -version
```
### 4. Build and execute spring boot tutorial basic project.
```bash
cd ca1/basic
```
Install Maven
```bash
  sudo apt install maven
```


Execute the project

```bash
  mvn spring-boot:run
```
  Open the web browser in:
  http://192.168.56.5:8080/

### 5. clone the repository
create folder and clone project
```bash
mkdir CA3
cd CA3

git clone https://github.com/WagnerPaivaDev/devops-21-22-JPE-1231863.git

```

### 7. Install Gradle

```bash
sudo apt remove gradle
wget htpps://services.gradle.org/distributions/gradle-8.6-bin.zip
sudo mkdir /opt/gradle
sudo unzip -d /opt/gradle gradle-8.6-bin.zip
```

**If unzip function does not work, install it with this commands:**

```bash
sudo apt update
sudo apt install unzip
```

    * Set the environment variables
```bash
echo "export GRADLE_HOME=/opt/gradle/gradle-8.6" >> ~/.bashrc
echo "export PATH=$PATH:$GRADLE_HOME/bin" >> ~/.bashrc
source ~/.bashrc
gradle -v
cd ca2/part1
```
    * Run the server inside the VM
```bash
gradle runServer
```
    * Run the client in the host machine

```bash
 gradle runClient --args="192.168.56.5 59001"
```
    * Execute the client


### 8. run the project

#### * 7.1. run CA1 project
```bash
./mvnw spring-boot:run
```

to open project frontEnd on browser, get VM IP:
```bash
ip addr
```
put the IP and the port 8080 on the browser address.

#### * 7.2. run CA2 part1 project
```bash
./gradlew build
./gradlew runServer
```

To run the client in the same folder but on the computer terminal, on two different terminals:
```bash
./gradlew runClient --args="192.168.56.5 59001" 
```

#### * 7.3 run CA2 part2 project

on the basic folder:
```bash
./gradlew build
./gradlew bootRun
```
to open project frontEnd on browser:
get the VM IP:
```bash
ip addr
```
put the IP and the port 8080 on the browser address.


