# AWS: API, Dynamo and Lambda

## Amazon API Gateway

### What is Amazon API Gateway?

Many Serverless applications use Amazon API Gateway, which replaces the API servers with a managed serverless solution. In this guide, we'll walk you through all the details of API Gateway and show you how it can be used with the Serverless Framework. Also included are resources should you want to learn even more about the service.

### How does API Gateway work?

API Gateway sits between the backend services of your API and your API's users. It handles the HTTP requests to your API endpoints and routing them to the correct backends. The graphical user interface allows you to sketch out the API structure and view the API flows in graphical form.

### Why is API Gateway an essential part of the Serverless ecosystem?

Amazon's API Gateway enables a truly serverless architecture for web applications. When using API Gateway together with other AWS services, it's possible to build a fully functional customer-facing web application. Many AWS services support integration with Amazon API Gateway including Lambda and SNS.

### Benefits of Amazon API Gateway

Using Amazon's API Gateway to create HTTP APIs in AWS offers four main benefits. It makes it easy to have different Serverless functions serving different parts of your API. There are a few caveats, however, that you should be aware of before using it in production. Amazon's API Gateway is designed for building serverless HTTP APIs. It manages the schema of your API and connects each endpoint to the right backend service. The maximum payload size that can be returned by an API endpoint is 10MB, and integration timeouts are 50ms.

Amazon API Gateway makes it easy for developers to create, publish, maintain, monitor, and secure APIs. Using API Gateway, you can create RESTful and WebSocket APIs that enable real-time two-way communication. It handles all the tasks involved in processing up to hundreds of thousands of API calls.

## DynamoDB

DynamoDB is a hosted NoSQL database offered by Amazon Web Services (AWS). DynamoDB is accessible via an HTTP API and performs authentication & authorization via IAM roles. AWS Lambda provides auto-scaling, stateless, ephemeral compute in response to event triggers.

## Amazon DynamoDB

Amazon's DynamoDB database is designed to run high-performance applications at any scale. DynamoDB offers built-in security, continuous backups, automated multi-Region replication, in-memory caching, and data export tools. It is a fully managed, serverless, key-value NoSQL database.

## Dynamoose

Dynamoose is a data modeling tool for Amazon's DynamoDB database.
