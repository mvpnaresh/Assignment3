# Simply Ads

# Architecture Diagram

![SimplyAdsHighLevelDesign](https://user-images.githubusercontent.com/12168162/120890907-4f359a00-c623-11eb-8d14-254005a872db.png)

# Class Diagram for Place An Advertisement functionality

![PlaceAdClassDiagram](https://user-images.githubusercontent.com/12168162/120890938-78562a80-c623-11eb-988e-1a66a9bdf5cb.png)

The front end is a Web Application which can be implemented in any of the popular or javascript frameworks

The flows are mentioned in numbers :-

1. The first flow is for getting an Auth Token and is retrieved from the Azure AD.

2. The requested Auth Token is returned.

3. Sell Advertisement command is created and is added to the event bus.

All Api and service communication is through Azure API Gateway

(The event bus implementation is through Message Broker like (Mass Transit) and RabbitMq event bus

4. Sell Advertisement command is consumed by a Micro service acting as a hosted service which validates the advertisement.

This service also has a connection to the replicated nosql db for validation.

5. The Advertisement Validated event is raised once validation is completed.

6. Advertisement Validated event is consumed by the AdvertisementValidatedEventConsumer.


The rest of the flow is self explanatory by applying the above mentioned analogy

Each of the service has one functionality as a micro service should be.

Each service call is through a Api Gateway as a single point of entry for authentication and authorization to the different services.

The Asynchronous communication between services is established through message bus and Event Hub implementation which is achieved using RabbitMq


UI Notifications are sent back to user using a SignalR implementation


