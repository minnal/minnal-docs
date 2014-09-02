Introduction
============
Overview
--------
Minnal is a Tamil noun, meaning **“lightning”**. It allows developers to build RESTful services at a faster pace through its powerful instrumentation engine. Minnal generates APIs for the resources at run time and allows you to only focus on **enriching your domain**. 

It comes with *out-of-the-box* support for **persistence**, **configuration**, **logging**, **metrics**, **API documentation**, **authentication** and is extremely powerful for services that are CRUD centric.

A typical REST service consist of a *controller* layer that handles the incoming request, optionally delegates them to the *application* layer which in turn call the *domain* layer and *repository* layer. Most of these are boilerplate code and the real work happens in the domain layer and application layer. However good the REST framework is, you may end up writing the boilerplate code will have spend effort in testing and managing these code. Minnal eliminates the *DAL* and *Controller* from your application, so you can focus on enriching your domain.

Minnal uses `Netty <http://netty.io/>`_, a NIO client-server framework, underneath to achieve high scalability. `Jersey <https://jersey.java.net>`_ is used as the REST framework. `Jackson <http://jackson.codehaus.org/>`_ is used for serialization. `Pac4j <https://github.com/leleuj/pac4j>`_ for supporting variety of authentication protocols. Minnal recommends JPA for all DB access and uses `FlywayDB <http://flywaydb.org/>`_ for running db migrations.

Domain Modelling
----------------
Minnal leverages some of the constructs from `Domain Driven Design <http://dddcommunity.org/>`_ (DDD) to empower developers to come up with elegant domain models. Domain modelling is a way to describe and model real world entities and relationship between them, which collectively describe the problem domain space. DDD is an approach that applies primary focus on the core domain and domain logic to come up with a better domain modelling. The key constructs of modelling are entities, value objects, aggregates and repositories. Entity is a mutable object that has attributes and an identity. Value object is an immutable object that has attributes but no identity. Aggregate is a collection of objects that are bound together by a root entity called as an aggregate root. Aggregate root guarantees the consistency of changes made within the aggregate by ensuring external objects don't have references to its members. Let us see a car model to understand these constructs better. *A Car has an engine, wheels and doors. When you drive a car, you do not have to worry about moving the wheels forward, making the engine combust with spark and fuel, etc.; you are simply driving the car. In this context, the car is an aggregate of several other entities (engine, wheels etc..) and serves as the aggregate root to all of the other systems. You instruct the car and not the wheels to stop*. Repository mediates between the domain and data mapping layers, acting like an in-memory domain object collection.

Minnal uses these DDD constructs to auto-generate the APIs. The aggregate root becomes the root resource and the collections in aggregate roots become the sub-resources. The operations in the car domain (like start, stop) are actions that can be performed on the resources via the root resource.

.. code-block:: bash
   GET /cars/:id                           -- Get the car identified by :id
   PUT /cars/:id/start                     -- Start the car identified by :id
   PUT /cars/:id/stop                      -- Stop the car identified by :id
   PUT /cars/:id/doors/:door_id/open       -- Open the car door identified by :door_id
   PUT /cars/:id/doors/:door_id/close      -- Close the car door identified by :door_id
