# Socket.io

## What is a Web Socket?

WebSocket is a computer communications protocol, providing full-duplex communication channels over a single TCP connection.

## Describe the Web Socket request/response handshake and what happens once the connection is established

    Within that request response chain, the client asks to open a WebSocket connection, and the server responds (if its able to). If this initial handshake is successful, the client and server have agreed to use the existing TCP/IP connection that was established for the HTTP request as a WebSocket connection

WebSockets provides full-duplex communication channels over a single TCP connection. It is a successor to The WebSocket API from the W3C and maintained by the WHATWG.

WebSocket is designed to work over ports 443 and 80, thus making it compatible with HTTP. To achieve compatibility, the WebSocket handshake uses the HTTP Upgrade header[3] to change from the HTTP protocol to the Web-Stinged one (http-sting).

The WebSocket protocol enables real-time data transfer from and to the server. Most browsers support the protocol, including Google Chrome, Firefox, Microsoft Edge, Internet Explorer, Safari and Opera. The communications are usually done over TCP port number 443 (or 80 in the case of unsecured connections).

## Web Sockets provide a standardized way for the server to send content to a client without first receiving a ____ from that client

    The WebSocket.send() method enqueues the specified data to be transmitted to the server over the WebSocket connection, increasing the value of bufferedAmount by the number of bytes needed to contain the data. If the data can't be sent (for example, because it needs to be buffered but the buffer is full), the socket is closed automatically. The browser will throw an exception if you call send() when the connection is in the CONNECTING state. If you call send() when the connection is in the CLOSING or CLOSED states, the browser will silently discard the data.

## What does the event handler io.on() do?

    Sockets work based on events. There are some reticent events that can be entered using the socket object on the server side. These include connect, message, disconnect, reconnect, ping, join and leave. The client side socket object grants us with some reserved events: connect_error, connect_timeout, reconnect.

## What is the difference between WebSocket and Socket.IO? (think Git and GitHub, or OAuth and Auth0)

### WebSocket

 WebSocket is the communication Protocol that provides bidirectional communication between the Client and the Server. WebSocket remains open all the time, so they allow real-time data transfer. When clients trigger the request to the server, it does not close the connection on receiving the response.

- It is the protocol that is established over the TCP connection
- It provides full-duplex communication on TCP connections.
- Proxy and load balancer is not supported in WebSocket.
- It doesn’t support broadcasting
- It doesn’t have a fallback option

### Socket.IO

Socket.IO is a library that enables real-time and full-duplex communication between the Client and the Web servers. It uses the WebSocket protocol to provide the interface. Generally, it is divided into two parts; both WebSocket vs Socket.io are event-driven libraries.

    Client-Side: it is the library that runs inside the browser
    Server Side: It is the library for Node.js

- It is the library to work with WebSocket
- Provides the event-based communication between browser and server.
- A connection can be established in the presence of proxies and load balancers.
- It supports broadcasting.
- It supports fallback options.

## When would you use WebSockets?

    WebSocket provides a duplex connection. This means that information can be sent and received at the same time. The best use-case of WebSocket is when you need real-time data really quick. If you can afford a delay of a few milliseconds in the information you seek, you must go for HTTP.

- Background - web servers, HTTP, and polling
- Wide Support : WebSockets are supported across every major browser, web-based and mobile. 98% of globally used browsers support the interface. This means WebSockets has more client support than many other HTML5 and ES6 features such as arrow functions.

- Blazing fast speed : WebSockets can take advantage of the TLS layer (known as WSS). There is no security sacrifice when switching from HTTPS to WSS. Because of the overheads advantage, latency is much lower. Low latency is ideal for multiplayer games, collaborative apps and other similar products.

- Easy setup and management : Setting up a WebSockets server won't be too difficult. It's probably best to use the ws library, available on GitHub. The Easybase platform uses this pattern to send messages across tables, users, and external apps. A common practice is to use JSON.stringify() before sending a message and.JFS after receiving one.

- Bi-directionality : In WebSockets, the client initiates a 'request' and the server processes a corresponding response. This means you don't necessarily know when the server's going to send the client something (unlike HTTP). We'll see in the example below how we can safely differentiate between message types.

## When would you use Socket.IO?

Socket.IO is a JavaScript library for communication between web clients and servers in real time. It can be used to make multiplayer games. My chat project, connect 4 game, video conferencing app, and multiplayer pong game all used Socket.IO.

### Content

- Sending a message in client and server
- Recieving a message in client and server
- Socket IDs
- Rooms
- Differe

    Sending/recieving a message in client and server
