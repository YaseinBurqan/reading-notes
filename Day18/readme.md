# AWS: Events

AWS — Difference between SQS and SNS

Comparisons: SQS vs SNS in AWS — Simple Notification Service and Simple Queue Service

SQS and SNS are important components for scalable, large scale, distributed, cloud-based applications:

- SNS is a distributed publish-subscribe service.

- SQS is distributed queuing service.

### SNS (Simple Notification Service)

![](https://miro.medium.com/max/628/1*mdUPKzrfJFuXa4d43KhKUQ.png)

Amazon SNS makes it simple and cost effective to send push notifications to mobile device users, email recipients or even send messages to other distributed services. Amazon SNS supports Apple, Google, Fire OS, and Windows devices as well as Android devices in China with Baidu Cloud Push.

SNS : Push Mechanism — SNS pushes messages to consumers.

SNS : No persistence. Whichever consumer is present at the time of message arrival, get the message and the message is deleted. If no consumers available then the message is lost.

SNS : All the consumers are (supposed to be) processing the messages in different ways.

### SQS (Simple Queue Service)

![](https://miro.medium.com/max/875/1*7eL3udb6Cto4I9Ly1sN8oA.jpeg)

SQS is a distributed queuing system. Messages are not pushed to receivers. Receivers have to poll SQS to receive messages. Messages can be stored in SQS for short duration of time (max 14 days). Other receivers do not receive the same message later.

SQS : Pull Mechanism — Consumers poll messages from SQS.

SQS : Messages are persisted for some duration is no consumer available. The retention period value is from 1 minute to 14 days. The default is 4 days.

In SQS the message delivery is guaranteed but in SNS it is not.

SQS : All the consumers are supposed to be identical and hence process the messages in exact same way.
