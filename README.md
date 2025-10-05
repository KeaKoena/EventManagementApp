# EventManagementApp

**EventManagementApp** is a Java Swing desktop application for managing events, venues and attendees.  
Built as a NetBeans Ant project (JDK 20). Uses MySQL for persistence.

## Features
- Create and manage events
- Create and manage venues
- Add / view attendees for events
- Simple Swing-based GUI

## Tech stack
- Java (target: JDK 20)
- Swing (GUI)
- MySQL (database)
- NetBeans (project structure / Ant build)

## Prerequisites
1. Java JDK 20 (or matching your NetBeans `javac.source`/`target`) installed and `JAVA_HOME` set.  
2. MySQL server running locally (or accessible DB).  
3. MySQL Connector/J (JDBC driver) — add the connector JAR to the project's libraries.  
4. NetBeans (recommended) or Ant if you want to build from CLI.

## Database setup (example)
Run this SQL to create a minimal schema:

```sql
CREATE DATABASE IF NOT EXISTS event_management;
USE event_management;

CREATE TABLE venues (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  address VARCHAR(255),
  capacity INT
);

CREATE TABLE events (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(150) NOT NULL,
  date DATE,
  venue_id INT,
  FOREIGN KEY (venue_id) REFERENCES venues(id)
);

CREATE TABLE attendees (
  id INT AUTO_INCREMENT PRIMARY KEY,
  event_id INT,
  name VARCHAR(100),
  email VARCHAR(150),
  FOREIGN KEY (event_id) REFERENCES events(id)
);
