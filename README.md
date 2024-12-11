---
# ECE1724H F1 Final Report



**Project Title :** Real-time Chat Application

**Authors** : Zhiying Tan [student ID: 1002929049] [zhiying.tan@mail.utoronto.ca](mailto:zhiying.tan@mail.utoronto.ca)  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Corvinus Zhang [student ID: 1002935229] [corvinus.zhang@mail.utoronto.ca](mailto:corvinus.zhang@mail.utoronto.ca)

**Institution:** Electrical and Computer Engineering, University of Toronto

**Date :** December 2024

## Video Demo
Please find the video demo link in here:
https://youtu.be/wlSNHgB19pU
https://www.youtube.com/watch?v=wlSNHgB19pU


<br/><br/>                
                                  

# Project Overview
In this project, our group select real-time chat application as our topic. It is a light-weighted software application built by Rust. For this deliverable, four main points are explored: **Motivation & Objectives**, **Feature**, **Reproducibility** and **Individual Contributions**. At the beginning, We initialized this project into  3 different repositories to serve different purpose as per below. Finally we use `git submodule` to includes all 3 repositories into one, all the commits history of this project will only be visible under each original repos if you get into the code folders or clicking the link  provided below. 

* rust-chat-server: Backend server implemented with Rust  (Commit history: https://github.com/CorvinusZY/react-chat-UI/commits/main/)
* rust-chat-server-client: A front-end user interface as a command-line utility in Rust. (Commit history: https://github.com/CorvinusZY/rust-chat-server-client/commits/main/)
* react-chat-UI: A front-end UI implemented with React framework. Again this repository serves the purpose of front-end user interface, but instead of a CLI client, we implement this UI to make it more user-friendly. As we believe a front-end UI with React framework has well-developed libraries, much mature, organize in terms of practical world application. (Commit history: https://github.com/CorvinusZY/rust-chat-server/commits/main/)
  
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
The main objective for this project is to build a chat server that can receive and propagate messages to users’ in near real time. 
It offers robust user authentication, supports chat room creation, and enables real-time messaging through WebSockets. This minimal variable product (MVP) aims to fill a notable gap within the current Rust ecosystem by providing a lightweight, high-performance solution that is straightforward to deploy, specifically the WebSocket section below. By demonstrating the use of Rust in constructing scalable and reliable real-time communication platforms, the project seeks to showcase how Rust can be effectively leveraged for modern web applications. To test and emulate user experience, we also build a frontend react app that will support login, friend information retrieval, and message propagation.
Our original proposal was integrating a Rust back-end server with CLI front-end again implemented in Rust, which are completed. However, we then come up with an idea of the integration of Rust back-end server with React framework implemented UI, as React framework is much more mature and have a user-friendly 

<br/><br/>


# Features

The overall design as per below


### **Authentication**

The proposed chat application will include several key features to ensure a complete and functional MVP. The first feature is a secure user authentication system that allows users to log in. Therefore, it is imperative to build a login page that sends user credentials to the backend and retrieve friend list and user information accordingly. From the backend side, this user credentials and information will be implemented using an in-memory database, SQLite, to manage user credentials and session data. The inclusion of this feature addresses the foundational need for secure access in real-time applications and contributes to the Rust ecosystem by providing an example of a lightweight, easy-to-implement authentication system. The original proposal was embedding the authentication into websocket request once it is open, we thought this would be much more safety for the credentials. However, we found out that it took on average 3 to 5 second to entitle a user which is slower than our expectation. As a result, we came up with an idea of encrypted the password into websocket authenticaiton header, which improved the waiting time to almost in real-time.


### WebSockets

A critical feature of the project is the integration of WebSockets for real-time messaging. This component is essential to ensuring low-latency communication between users within the same chat room. By implementing WebSocket functionality, the project  highlight Rust’s capabilities for handling real-time data transmission efficiently. By utilizing WebSockets, We measures the latency of receiving a message of around millisecond.

### Chatroom 
Besides, the fundamental reason for using the chat application is to communicate with friends in a timely fashion, and thus the most essential functional requirement is to be able to deliver the message to the friend through the UI. Once the user login, a list of friends dialog window are presented as a list on left side. The friend's avater is again stored in database. If an user open the dialogue with friend and a message is sent from friend's side the message will pop up right away in chat window. However, If the user doesn’t have the associated dialogue open, they should have a red alert with a count of unread messages beside their friend’s profile photo. Lastly, if the user you send the message doesn't login, then he or she could only be able to view the messages once he login. Our design is basically persist messages in the database to make sure that connection error or logout won’t cause any data loss.

### CLI framework

A simple yet user-friendly command-line interface (CLI) that allows users to log in and message friend are developed which serves as one of the front-end interface for the MVP. By focusing on a CLI front-end component, it is still demonstrating Rust’s suitability for creating practical, user-interactive tools. The development of this CLI will also illustrate the flexibility of Rust in building non-web-based user interfaces.

### React framework
A much more complex graphical user interface is built with React framework due to the maturity and wide-spread usage in real-world application. With this streamline framework, we create a delicate and user-friendly chat window.

<br/><br/>


# Reproducibility
To reproduce all of our  3 components, please refer to the Run section of each component below

## rust-chat-server-client
https://github.com/CorvinusZY/rust-chat-server-client/tree/main

### Run
Make sure the server is running before connecting the clients

* run `cargo build`
* run `./target/debug/chatRustClient {username} {password}` to start the client.(For testing purpose, one could use below 2 users)
  *  `./target/debug/chatRustClient winnie 456`
  *  `./target/debug/chatRustClient corvinus 123`
* enter `{receiver_username} {your_message}` to send msg to receiver_username if the person is online.
  * For example, sending a message to winnie: `winnie hi`

<br/><br/>

## react-chat-UI
https://github.com/CorvinusZY/react-chat-UI

### Run

First install dependencies by running:

`npm install`

In the project directory, you can run:

`npm start`

Runs the app in the development mode.
Open http://localhost:3000 to view it in your browser.
<br/><br/>


## rust-chat-server
https://github.com/CorvinusZY/rust-chat-server

### Run

Simply run `cargo build` and then `cargo run`

### DB Inspection

See test client for more info
run `sqlite3 my_database.db` to inspect DB
<br/><br/>




# Individual Contributions

The distribution of responsibilities are equally divided to the each team members. Winnie is concentrating on backend server setup, authentication, providing a secure foundation for the project. Corvinus is focuing  on real-time messaging, tackling the implementation of WebSockets for efficient communication as well as a basic . Both Zhiying and Corvinus developed the front-end client interface together and handle the integration of various backend components together, ensuring a seamless user experience. This balanced approach allows the team to work in parallel, optimizing time management and enabling the completion of a fully functional MVP within the designated project timeline.

### Team Roles

- Zhiying (Backend Setup & Authentication, CLI & Integration)
    - Set up the Web server with sqlite database, implement required end points such as user authentication, login and friend request etc.
    - Build CLI, handle command parsing as well as  front-end UI and integrate with backend endpoints.
- Corvinus (WebSockets & Messaging, CLI & Integration)
    - Develop WebSocket connections and enable message broadcasting within chat rooms.
    - Build CLI, handle command parsing as well as front-end UI and integrate with backend endpoints.

<br/><br/>


