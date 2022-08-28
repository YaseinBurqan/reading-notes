# API Integration

## Dynamic API Server


An Express/NFCS based server designed to be a "model agnostic" REST API server, which can perform CRUD operations on any data model. The Server must operate as follows:. Support all REST/HTTP methods, with a standard routing structure and output in a standard format.

Updating records with PUT or PATCH requires a route that specifies both the model name and the record ID. The object given to the route is to be either the FULL object in the case of a PUT, or just the fields you wish to modify in a PATCH.

## Authentication Server / Module

An Express/Node.js based server using a custom "authentication" module that will handle user registration and sign in using Basic, Bearer, or OAuth. Custom "authorization" modules that will grant/deny users access to the server based on their role or permissions level.


