# BambangShop Receiver App
Tutorial and Example for Advanced Programming 2024 - Faculty of Computer Science, Universitas Indonesia

---

## About this Project
In this repository, we have provided you a REST (REpresentational State Transfer) API project using Rocket web framework.

This project consists of four modules:
1.  `controller`: this module contains handler functions used to receive request and send responses.
    In Model-View-Controller (MVC) pattern, this is the Controller part.
2.  `model`: this module contains structs that serve as data containers.
    In MVC pattern, this is the Model part.
3.  `service`: this module contains structs with business logic methods.
    In MVC pattern, this is also the Model part.
4.  `repository`: this module contains structs that serve as databases.
    You can use methods of the struct to get list of objects, or operating an object (create, read, update, delete).

This repository provides a Rocket web framework skeleton that you can work with.

As this is an Observer Design Pattern tutorial repository, you need to implement a feature: `Notification`.
This feature will receive notifications of creation, promotion, and deletion of a product, when this receiver instance is subscribed to a certain product type.
The notification will be sent using HTTP POST request, so you need to make the receiver endpoint in this project.

## API Documentations

You can download the Postman Collection JSON here: https://ristek.link/AdvProgWeek7Postman

After you download the Postman Collection, you can try the endpoints inside "BambangShop Receiver" folder.

Postman is an installable client that you can use to test web endpoints using HTTP request.
You can also make automated functional testing scripts for REST API projects using this client.
You can install Postman via this website: https://www.postman.com/downloads/

## How to Run in Development Environment
1.  Set up environment variables first by creating `.env` file.
    Here is the example of `.env` file:
    ```bash
    ROCKET_PORT=8001
    APP_INSTANCE_ROOT_URL=http://localhost:${ROCKET_PORT}
    APP_PUBLISHER_ROOT_URL=http://localhost:8000
    APP_INSTANCE_NAME=Safira Sudrajat
    ```
    Here are the details of each environment variable:
    | variable                | type   | description                                                     |
    |-------------------------|--------|-----------------------------------------------------------------|
    | ROCKET_PORT             | string | Port number that will be listened by this receiver instance.    |
    | APP_INSTANCE_ROOT_URL   | string | URL address where this receiver instance can be accessed.       |
    | APP_PUUBLISHER_ROOT_URL | string | URL address where the publisher instance can be accessed.       |
    | APP_INSTANCE_NAME       | string | Name of this receiver instance, will be shown on notifications. |
2.  Use `cargo run` to run this app.
    (You might want to use `cargo check` if you only need to verify your work without running the app.)
3.  To simulate multiple instances of BambangShop Receiver (as the tutorial mandates you to do so),
    you can open new terminal, then edit `ROCKET_PORT` in `.env` file, then execute another `cargo run`.

    For example, if you want to run 3 (three) instances of BambangShop Receiver at port `8001`, `8002`, and `8003`, you can do these steps:
    -   Edit `ROCKET_PORT` in `.env` to `8001`, then execute `cargo run`.
    -   Open new terminal, edit `ROCKET_PORT` in `.env` to `8002`, then execute `cargo run`.
    -   Open another new terminal, edit `ROCKET_PORT` in `.env` to `8003`, then execute `cargo run`.

## Mandatory Checklists (Subscriber)
-   [:D] Clone https://gitlab.com/ichlaffterlalu/bambangshop-receiver to a new repository.
-   **STAGE 1: Implement models and repositories**
    -   [:D] Commit: `Create Notification model struct.`
    -   [:D] Commit: `Create SubscriberRequest model struct.`
    -   [:D] Commit: `Create Notification database and Notification repository struct skeleton.`
    -   [:D] Commit: `Implement add function in Notification repository.`
    -   [:D] Commit: `Implement list_all_as_string function in Notification repository.`
    -   [:D] Write answers of your learning module's "Reflection Subscriber-1" questions in this README.
-   **STAGE 2: Implement services and controllers**
    -   [:D] Commit: `Create Notification service struct skeleton.`
    -   [:D] Commit: `Implement subscribe function in Notification service.`
    -   [:D] Commit: `Implement subscribe function in Notification controller.`
    -   [:D] Commit: `Implement unsubscribe function in Notification service.`
    -   [:D] Commit: `Implement unsubscribe function in Notification controller.`
    -   [:D] Commit: `Implement receive_notification function in Notification service.`
    -   [:D] Commit: `Implement receive function in Notification controller.`
    -   [:D] Commit: `Implement list_messages function in Notification service.`
    -   [:D] Commit: `Implement list function in Notification controller.`
    -   [ ] Write answers of your learning module's "Reflection Subscriber-2" questions in this README.

## Your Reflections
This is the place for you to write reflections:

### Mandatory (Subscriber) Reflections

#### Reflection Subscriber-1
1.  RwLock prevents data to be updated at the same time but allows them to be read at the same time. This is important because if data is updated at the same time then the result would be indeterminate. With RwLock, this can be prevented. As for mutex, it prevents both reading and writing at the same time. So if there were multiple users trying to access the same data at the same time, they would have to take turns. RwLock allows simultaneous reading, and so it will be better to use RwLock instead of mutex.

2. Because by doing that, rust prevents a race condition for example where both increments a counter at the same time. by preventing this, it would prevent bugs that could appear further down the line. 

#### Reflection Subscriber-2
1. Before reading this question, no. Because i was mostly focused on getting this done while trying to understand some 20 pages of a language i never encountered. After reading it, i looked at src/lib.rs and i don't undertand anything. The only thing i managed to somewhat get was that the compose_error_response was defined here. I'd seen this function used several times but thought it was one of the built-in functions.

2. Well, to plug in subscribers, as in, adding more subscribers, you could just add a subscriber to the repository. I haven't tried spawning multiple instances of the main application yet, i don't think it would be much different? i'm not sure how it would dubdcribe if the two instances have two types of the same name though.

3. No, i haven't. Well i don't think failed attempts count. That was before i saw all the ones provided. But i found them before succeeding so i ended up not completing them. But i don't think i can say much from that experience alone.