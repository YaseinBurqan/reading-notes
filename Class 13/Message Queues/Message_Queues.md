# Message Queues

## Get started

In this guide we’ll create a basic chat application. It requires almost no basic prior knowledge of Node.JS or Socket.IO, so it’s ideal for users of all knowledge levels.

## Introduction

Most real-time chat systems are architected around sockets. This means that the server can push messages to clients. Whenever you write a chat message, the server will get it and push it to all other connected clients.

## The web framework

In this tutorial we'll be using the Node.JS web framework express to develop a chat app. The main goal is to set up a simple HTML page that serves out a list of messages and an address bar for users to send in their logins and passwords.

    {
    "name": "socket-chat-example",
    "version": "0.0.1",
    "description": "my first socket.io app",
    "dependencies": {}
    }

## Emitting events

The main idea behind Socket.IO is that you can send and receive any events you want, with any data you want. Any objects that can be encoded as JSON will do, and binary data is supported too.

Let’s make it so that when the user types in a message, the server gets it as a chat message event.

## Broadcasting

The next goal is for us to emit the event from the server to the rest of the users.

In order to send an event to everyone, Socket.IO gives us the io.emit() method.

If you want to send a message to everyone except for a certain emitting socket, we have the broadcast flag for emitting from that socket

And on the client side when we capture a chat message event we’ll include it in the page. The total client-side JavaScript code now amounts

## Namespaces

A Namespace is a communication channel that allows you to split the logic of your application over a single shared connection (also called "multiplexing").

![Namespaces](https://socket.io/assets/images/namespaces-088745a8a8882118740f50b6b1232588.png)

## Rooms

A room is an arbitrary channel that sockets can join and leave. It can be used to broadcast events to a subset of clients:

![Rooms](https://socket.io/images/rooms.png)

### every socket in the room excluding the sender will get the event

![socket](https://socket.io/images/rooms2.png)

## Default room

Each Socket in Socket.IO is identified by a random, unguessable, unique identifier Socket#id. For your convenience, each socket automatically joins a room identified by its own id.

### With multiple Socket.IO servers

![](https://socket.io/images/rooms-redis.png)

### Implementation details

The "room" feature is implemented by what we call an Adapter. This Adapter is a server-side component which is responsible for:

- storing the relationships between the Socket instances and the rooms
- broadcasting events to all (or a subset of) clients

## Room events

Starting with socket.io@3.1.0, the underlying Adapter will emit the following events:

- create-room (argument: room)
- delete-room (argument: room)
- join-room (argument: room, id)
- leave-room (argument: room, id)
