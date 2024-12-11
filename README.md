---
# ECE1724H F1 Final Report



**Project Title :** Real-time Chat Application

**Authors** : Zhiying Tan [student ID: 1002929049] [zhiying.tan@mail.utoronto.ca](mailto:zhiying.tan@mail.utoronto.ca)  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Corvinus Zhang [student ID: 1002935229] [corvinus.zhang@mail.utoronto.ca](mailto:corvinus.zhang@mail.utoronto.ca)

**Institution:** Electrical and Computer Engineering, University of Toronto

**Date :** December 2024

# Video Demo
Please find the video demo link in here:
https://youtu.be/wlSNHgB19pU
https://www.youtube.com/watch?v=wlSNHgB19pU


<br/><br/>                
                                  

# Project Overview

Our group chose to develop a real-time chat application as our project. This lightweight software application is built with Rust and emphasizes four key aspects: Motivation & Objectives, Features, Reproducibility, and Individual Contributions.

To organize our work, the project was divided into three separate repositories, each serving a specific purpose. These repositories were later combined using git submodule, enabling centralized access while maintaining the original commit histories within their respective repositories. You can view the commit histories by navigating to the code folders or using the provided links below.

* rust-chat-server: Backend server implemented in Rust. (Commit history: https://github.com/CorvinusZY/rust-chat-server/commits/main/)
* rust-chat-server-client: Command-line interface (CLI) client for front-end interaction, built in Rust. (Commit history: https://github.com/CorvinusZY/rust-chat-server-client/commits/main/)
* react-chat-UI: Front-end user interface implemented with the React framework. Unlike the CLI client, this UI provides a more user-friendly experience leveraging React’s mature ecosystem and practical-world applicability. (Commit history: https://github.com/CorvinusZY/react-chat-UI/commits/main/)
  
<br/><br/>



# Motivation

### **Practical Usage**

Our project initiative involves designing and implementing a real time chat application, an essential in everyday communication across various setting, from workplace collaboration and school interactions to personal conversations with friends and family.Given the widespread demand for such applications, we believe this project aligns strongly with real-world needs and can serve as a foundation for even broader uses across industries.

### **Technical Skills Development**

While many chat applications exist (such as iMessage, WhatsApp, and WeChat), they rely on different infrastructures, frameworks, and languages. However, Rust, as a newer programming language, is rarely used in chat applications but well handles the challenges of real time chat, making this project unique. Leveraging Rust’s strengths, such as its low-latency capabilities, we aim to deliver a real-time chat experience with minimal response times. Rust’s memory and thread safety, supported by its ownership and borrowing system, make it a highly reliable choice for handling concurrent messages safely.

An additional initiative could focus on potentially filling the gap in mature WebSocket libraries for Rust. The Rust ecosystem currently offers limited support for managing scalable WebSocket connections for large user bases. Many features, such as advanced reconnection strategies and message prioritization, would require significant customization. Addressing these gaps could enhance Rust's utility for real-time, high-traffic applications by simplifying implementation and improving scalability

### **Foundation of future projects**

Real-time chat applications are foundational to many collaborative tools and can be further extended into diverse areas, such as chat-based AI models, healthcare communication systems, and customer support services. This project not only allows for immediate real-world application but also establishes a platform for future innovation and integration across sectors.
<br/><br/>

# Objective
The primary objective of this project is to develop a chat server capable of receiving and propagating messages to users in near real-time. It features robust user authentication, chat room joining, and real-time messaging using WebSockets. This minimal viable product (MVP) addresses a significant gap in the Rust ecosystem by delivering a lightweight, high-performance solution that is both scalable and easy to deploy.

By demonstrating the use of Rust in constructing scalable and reliable real-time communication platforms, the project seeks to showcase how Rust can be effectively leveraged for modern web applications. To further enhance the user experience, we developed a React-based front-end application, supporting features like login, friend information retrieval, and message propagation.

Initially, our proposal focused on integrating a Rust back-end server with a CLI front-end (also built in Rust). While this was successfully implemented, we expanded the project to include a React-based UI. This decision stemmed from React’s mature ecosystem, extensive libraries, and its ability to deliver a more user-friendly interface, making it better suited for practical, real-world applications.

<br/><br/>


# Features

The proposed chat application include several key features to ensure a complete and functional MVP. 


### **Authentication**
This system allows users to log in, retrieve their friend list, and access user-specific information. On the front end, a login page sends encrypted user credentials to the backend. On the backend, SQLite, a lightweight in-memory database, is used to manage user credentials and session data.This feature addresses the critical need for secure access in real-time applications and enriches the Rust ecosystem by showcasing a straightforward yet effective approach to authentication.Our original design proposed embedding authentication within WebSocket requests upon connection to enhance security. However, during implementation, we found that this approach resulted in delays of 3 seconds on average, which did not meet our performance expectations. To resolve this, we implemented encrypted password transmission in the WebSocket authentication header. This adjustment significantly reduced latency, achieving near real-time performance while maintaining a high level of security. If a user enters an invalid username or incorrect password, an error message will appear, prompting them to reenter their credentials. Once valid login details are provided, the user is seamlessly redirected to the chat page.


### WebSockets

A critical feature of the project is the integration of WebSockets for real-time messaging. This component is essential to ensuring low-latency communication between users within the same chat room. By implementing WebSocket functionality, the project  highlight Rust’s capabilities for handling real-time data transmission efficiently. 

### Chatroom 

The primary purpose of a chat application is to facilitate timely communication between users. Therefore, a critical functional requirement is ensuring messages are delivered reliably and displayed seamlessly through the user interface (UI). Upon login, users are presented with a friend list displayed on the left panel, showcasing dialog windows and profile avatars, which are retrieved from the database. When a user opens a chat with a friend, incoming messages from the friend will appear instantly in the chat window. For conversations not currently open, a notification badge (e.g., a red alert with an unread message count) is displayed next to the friend’s profile photo, ensuring users are aware of unread messages. If a recipient is offline, they can view the messages once they log in, as all messages are persisted in the database to prevent data loss due to connection errors or user logout. By leveraging WebSocket technology, our system ensures real-time communication, achieving an average message latency of less than a second. This design guarantees a smooth user experience while maintaining the integrity and availability of message data.



### CLI framework

A simple yet user-friendly command-line interface (CLI) that allows users to log in and message friend are developed which serves as one of the front-end interface for the MVP. By focusing on a CLI front-end component, it is still demonstrating Rust’s suitability for creating practical, user-interactive tools. The development of this CLI will also illustrate the flexibility of Rust in building non-web-based user interfaces.

### React framework
The React framework is widely recognized for its maturity and extensive use in real-world applications, making it an ideal choice for building complex graphical user interfaces. Leveraging React’s streamlined structure, we can create an elegant and highly interactive chat window that delivers a seamless user experience. A chat application heavily relies on a responsive and intuitive front-end, and React excels in providing a user-friendly interface that meets these demands effectively.

<br/><br/>


# Reproducibility
To reproduce all of our 3 components, please refer to the Run section of each component below

## Client

### rust-chat-server-client
https://github.com/CorvinusZY/rust-chat-server-client/tree/main

#### Run
Make sure the server is running before connecting the clients

* run `cargo build`
* run `./target/debug/chatRustClient {username} {password}` to start the client. For testing purpose, one could pick any one of the below below 3 users. 
  *  `./target/debug/chatRustClient winnie 456`
  *  `./target/debug/chatRustClient corvinus 123`
  *  `./target/debug/chatRustClient john 789`
* enter `{receiver_username} {your_message}` to send msg to receiver_username if the person is online.
  * For example, sending a message to winnie: `winnie hi`

<br/><br/>

### react-chat-UI
https://github.com/CorvinusZY/react-chat-UI

#### Run

First install dependencies by running:

`npm install`

In the project directory, you can run:

`npm start`

Runs the app in the development mode.
Open http://localhost:3000 to view it in your browser. 
(To test the functionality, plase use the below 3 pairs of username/password to message each other: `corvinus/123` and `winnie/456` and `john/789`)
<br/><br/>


## Server

### rust-chat-server
https://github.com/CorvinusZY/rust-chat-server

#### Run

Simply run `cargo build` and then `cargo run`

#### DB Inspection

See test client for more info
run `sqlite3 my_database.db` to inspect DB
<br/><br/>




# Individual Contributions

Responsibilities were evenly distributed among team members to ensure balanced collaboration. Winnie focused on backend server setup and authentication, establishing a secure and robust foundation for the project. Corvinus concentrated on real-time messaging, implementing WebSockets for efficient communication and seamless message broadcasting. Both Zhiying and Corvinus collaborated on developing the front-end client interface and integrating backend components to ensure a smooth user experience. This well-coordinated approach allowed the team to work in parallel, maximizing efficiency and enabling the delivery of a fully functional MVP within the project timeline.

### Team Roles

- Zhiying (Backend Setup & Authentication, CLI & Integration)
    - Set up the Web server with an SQLite database, implement required end points such as user authentication, login and friend request etc.
    - Worked on the CLI for command parsing, contributed to front-end UI development, and integrated it with backend systems.
- Corvinus (WebSockets & Messaging, CLI & Integration)
    - Develop WebSocket connections and enable message broadcasting within chat rooms.
    - Worked on the CLI for command parsing, contributed to front-end UI development, and integrated it with backend systems.


<br/><br/>


