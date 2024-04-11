# GamerQuest

## Overview

GamerQuest is a Python-based game development project aimed at creating an immersive gaming experience. The project incorporates various features such as quest creation, avatar customization, multiplayer functionality, achievements, etc. It provides a platform for game enthusiasts to explore, create, and share their gaming experiences.

## Purpose

The purpose of GamerQuest is to provide a flexible and extensible framework for developing and playing games. It aims to offer a user-friendly interface for both game developers and players, allowing them to create, customize, and enjoy gaming content seamlessly.

## Features

- Quest Creation: Users can create their own quests with custom objectives and rewards.
- Avatar Customization: Players can personalize their avatars with different skins, outfits, and accessories.
- Multiplayer Functionality: Support for multiplayer gaming sessions, enabling users to play together online.
- Achievements: Players can earn achievements by completing various in-game challenges.

## External Libraries and Dependencies

- Pygame: Python library for game development.
- mysql-connector-python: Python library for connecting to MySQL databases.
- discord.py: Python library for interacting with the Discord API

## Design Patterns

- Model-View-Controller (MVC): Used to separate the game logic (Model), user interface (View), and user input handling (Controller). This separation enhances code organization and maintainability by isolating concerns and promoting modularity.
- Singleton: Used to ensure a single instance of certain classes, such as the database connection manager, throughout the application. This pattern helps manage resources efficiently and promotes reusability.

## Scenario Viewpoint

The scenario viewpoint illustrates the typical user journey within the GamerQuest application, showcasing the sequence of actions performed by users, including quest creation, avatar customization, multiplayer quests, achievement unlocking, and task tracking. It depicts the step-by-step process that users follow when using GamerQuest, starting from creating custom quests and avatars to participating in multiplayer quests, unlocking achievements, and tracking tasks within the game interface.

## Physical Viewpoint

The physical viewpoint outlines the deployment architecture of GamerQuest, illustrating the physical components and their interactions. It showcases the utilization of Python with Pygame for game development, MySQL for cloud database storage, and integration with Discord API for multiplayer functionality. The diagram highlights the technological components involved in the development and deployment of GamerQuest, showcasing the role of Python with Pygame in driving game development, MySQL as the cloud database for storing user data and quest information, and integration with Discord API for enabling multiplayer functionality and real-time communication among players.

## Development Viewpoint

In the development viewpoint, the focus is on the organization of modules and components, as well as the development environment of GamerQuest. Below is a UML Component diagram illustrating the modular structure of the system. This diagram showcases the various components of GamerQuest, such as quest creation, avatar creation, multiplayer quests, achievement system, and task tracking. Each component encapsulates related functionality, promoting modularity and ease of maintenance during the development process.

## Logical Viewpoint

The logical viewpoint describes the system from a functional perspective, emphasizing the organization of functionality without concern for implementation details. Below is a UML Class diagram illustrating the logical structure of GamerQuest. In this diagram, each class represents a logical entity within the system, such as quests, avatars, achievements, and tasks. Associations between classes depict relationships and dependencies between different entities, facilitating a clear understanding of the system's functionality.

## Process Viewpoint

The process viewpoint focuses on the runtime behavior of GamerQuest, including concurrency and synchronization aspects. Below is a UML Activity diagram illustrating the process flow of a typical user interaction with the system. This diagram outlines the sequence of activities performed by users within GamerQuest, including quest creation, avatar customization, multiplayer quest participation, achievement tracking, and task management. Decision points depict conditional behavior based on user actions, ensuring a smooth and intuitive user experience.

## Database Integration

GamerQuest utilizes a MySQL database for storing user data, quest information, achievements, etc. The database schema includes tables for users, quests, achievements, etc. The application interacts with the database through data access methods implemented in Python, using the mysql-connector-python library.

Database Schema:

- Users: Stores user information such as username, password, email, etc.
- Quests: Stores quest details including title, description, objectives, rewards, etc.
- Achievements: Stores information about achievements earned by users.

Database Connection:
The application establishes a connection to the MySQL database using the mysql-connector-python library. This connection is managed by a DatabaseManager class, ensuring a single connection instance throughout the application. Comments in the code explain the functionality of database-related code blocks.

# database_manager.py

import mysql.connector

class DatabaseManager:
\_instance = None

    def __new__(cls):
        if cls._instance is None:
            cls._instance = super(DatabaseManager, cls).__new__(cls)
            cls._instance.connect()  # Establish database connection upon instantiation
        return cls._instance

    def connect(self):
        # Establish connection to MySQL database
        self.connection = mysql.connector.connect(
            host="localhost",
            user="username",
            password="password",
            database="gamerquest"
        )
        self.cursor = self.connection.cursor()

    def disconnect(self):
        # Close database connection
        self.cursor.close()
        self.connection.close()

# Other database-related functions and classes go here

## Dependencies

- Pygame
