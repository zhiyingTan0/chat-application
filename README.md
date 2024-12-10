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
* rust-chat-server (https://github.com/CorvinusZY/react-chat-UI) : Backend server implemented with Rust  
* rust-chat-server-client: A front-end user interface as a command-line utility in Rust.
* react-chat-UI: A front-end UI implemented with React framework. Again this repository serves the purpose of front-end user interface, but instead of a CLI client, we implement this UI to make it more user-friendly. As we believe a front-end UI with React framework has well-developed libraries, much mature, organize in terms of practical world application.
  
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

The distribution of responsibilities are equally divided to the each team members. Team Member 1 concentrate on backend server setup, authentication, providing a secure foundation for the project. Team Member 2 focus on real-time messaging, tackling the implementation of WebSockets for efficient communication as well as a basic . Team Member 1 & 2 developed the front-end client interface together and handle the integration of various backend components together, ensuring a seamless user experience. This balanced approach allows the team to work in parallel, optimizing time management and enabling the completion of a fully functional MVP within the designated project timeline.

### Team Roles

- Team Member 1 (Backend Setup & Authentication, CLI & Integration)
    - Set up the Web server with sqlite database, implement required end points such as user authentication, login and friend request etc.
    - Build CLI, handle command parsing as well as  front-end UI and integrate with backend endpoints.
- Team Member 2 (WebSockets & Messaging, CLI & Integration)
    - Develop WebSocket connections and enable message broadcasting within chat rooms.
    - Build CLI, handle command parsing as well as front-end UI and integrate with backend endpoints.

<br/><br/>


