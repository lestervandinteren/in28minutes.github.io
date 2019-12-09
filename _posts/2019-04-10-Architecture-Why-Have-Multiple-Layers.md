---
layout:  post
title:  Software Architecture - Why do we use Layered Architectures?
date:    2019-04-09 12:31:19
summary:  In this article, we explore the reasons why we build applications with several layers. We also look at different options for each layer in the Java world.
categories: SwArchitecture
permalink:  /software-architecture-why-should-we-use-layered-architecture
---

In this article, we explore the reasons why we build applications with several layers. We also look at different options for each layer in the Java world.

### You will Learn
- Why Have Multiple Layers?
- What are typical layers and their responsiblities?
- What are the typical frameworks used in each layer in the Java world?

This is the fifth article in the following series of articles on Software Architecture :
- [1 - Quick Introduction To Software Architecture](/introduction-to-software-architecture){:target='_blank'}
- [2 - What Is The Goal Of a Software Architect?](/what-is-the-goal-of-an-software-architect){:target='_blank'}
- [3 - 5 Qualities of a Great Software Architect](/five-important-qualities-of-a-software-architect){:target='_blank'}
- [4 - 5 Important Responsibilities of a Software Architect](/five-important-responsibilities-of-a-software-architect){:target='_blank'}
- [5 - Software Architecture - Why do we use Layered Architectures?](/software-architecture-why-should-we-use-layered-architecture){:target='_blank'}

### Why Have Multiple Layers?

When we build any large application, such as a web application or service, we try to organize it into multiple layers. We could go for layers such as Web, Business, Access, among others:

![image info](/images/Capture-038-02.png)

The reason we go to such lengths is a very important underlying principle : **separation of concerns**. 

Each of the layers above have different responsibilities. Web layer is responsible for presenting information to the user. The Business layer is responsible for application's business logic. The Data layer is responsible for taking care of the data access, and configuring and talking to the data stores. You might also have an additional access layer to talk to external applications, or queueing messages for dispatch.

By defining each layer to have a separate responsibility, you ensure high cohesion with-in each such layer. 

### Layers In Enterprise Java

When it comes to the Java world, the typical organization of enterprise applications follows this schematic:

![image info](/images/Capture-038-03.png)


### Implementing The Web Layer

Earlier, the web layer of a Java EE application is responsible for rendering the final view to the user with technologies like JSPs and variety of templating languages.  With the advent of RESTful web services and evolution of JavaScript SPA frameworks, this has changed drastically. 

Today, we expose a REST API from the Java Web layer, and a front-end framework (such as AngularJS or ReactJS) handles the user presentation.

The main responsibility of a web layer is to talk to business layer and send a proper response to REST API calls.

Another responsibility that a web layer typically handles is authentication and authorizations using a module like Spring Security.

![image info](/images/Capture-038-04.png)
 

A few important decisions when designing your web layer are
- Should the application have state? If yes, you need to store session information about the user. Ideally, you should not.
- Which framework to use? The popular options are Spring Boot (MVC), JAX-RS(REST), JAX-WS(SOAP).

### Implementing The Business Layer

![image info](/images/Capture-038-05.png)

Lets look at the important business layer responsibilities:

#### Transaction Management

This is taken care of by Java Transaction API (JTA) and Spring Transactions. 

### Implementing The Access Layer

![image info](/images/Capture-038-06.png)

The following are the responsibilities of the Access layer:

#### Communicating with Data Store

If your application communicates with an external database, JPA might be a good choice. If very complex database queries are needed, then you might want to use JDBC or MyBatis. 

> Spring Data JPA might be a good starting point for using JPA and Hibernate.

#### Communication With External Interfaces

This layer provides interface with the JMS module. It also communicates with AMQP implementations.

### Other Layers

![image info](/images/Capture-038-07.png)

One of the most important aspects that needs to be handled in any system is Cross Cutting Concerns. This includes tasks such as logging, performance and security. 

Typically these are implemented using Aspect Oriented Programming. AspectJ and Spring AOP are options to consider.

### Unit Testing

Unit testing of the application is another important concern. Typical frameworks that are provided include JUnit, Mockito and Spring Unit.

Do check out our video on this:

[![image info](/images/Capture-038-01.png)](https://www.youtube.com/watch?v=fS2JnypQKWs)

### Summary

In this article, we understood why we need to have multiple layers in an application. We looked at the layers in a typical Java web application, along with framework options available. We then had a look at the makeup of the individual Data, Business and Access layers of a typical Java web application.


### 10 Step Quick Introductions to Frameworks

- [Learn Docker in 5 Steps](https://www.youtube.com/watch?v=Rt5G5Gj7RP0)
- [Spring Framework for Beginners in 10 Steps](https://courses.in28minutes.com/p/spring-framework-for-beginners)
- [Spring Boot for Beginners in 10 Steps](https://courses.in28minutes.com/p/spring-boot-for-beginners-in-10-steps)
- [Spring MVC in 10 Steps](https://www.youtube.com/watch?v=BjNhGaZDr0Y)
- [JPA and Hibernate in 10 Steps](https://courses.in28minutes.com/p/jpa-and-hibernate-tutorial-for-beginners-with-spring-boot)
- [Eclipse Tutorial for Beginners in 5 Steps](https://courses.in28minutes.com/p/eclipse-tutorial-for-beginners)
- [Maven Tutorial for Beginners in 5 Steps](https://courses.in28minutes.com/p/maven-tutorial-for-beginners-in-5-steps)
- [JUnit Tutorial for Beginners in 5 Steps](https://courses.in28minutes.com/p/junit-tutorial-for-beginners)
- [Mockito Tutorial for Beginners in 5 Steps](https://courses.in28minutes.com/p/mockito-for-beginner-in-5-steps)
- [Full Stack with Spring Boot and React](https://www.youtube.com/watch?v=SWXuXhZkNQc)
- [Full Stack with Spring Boot and Angular](https://www.youtube.com/watch?v=8ueiZf988qY)

## Top 5 Recommended in28Minutes Courses
[![Image](/images/Course-Go-Full-Stack-With-Spring-Boot-and-React.png "Go Full Stack with Spring Boot and React")](https://www.udemy.com/course/full-stack-application-with-spring-boot-and-react/?couponCode=NOVEMBER-2019){:target="_blank"}
[![Image](/images/Course-Master-Microservices-with-Spring-Boot-and-Spring-Cloud.png "Master Microservices with Spring Boot and Spring Cloud")](https://www.udemy.com/course/microservices-with-spring-boot-and-spring-cloud/?couponCode=NOVEMBER-2019){:target="_blank"}
[![Image](/images/Course-Spring-Framework-Master-Class---Beginner-to-Expert.png "Spring Master Class - Beginner to Expert")](https://www.udemy.com/course/spring-tutorial-for-beginners/?couponCode=NOVEMBER-2019){:target="_blank"}
[![Image](/images/Course-KubernetesCrashCourse.png "Kubernetes Crash Course for Java Spring Boot Developers")](https://www.udemy.com/course/kubernetes-crash-course-for-java-developers/?couponCode=NOVEMBER-2019){:target="_blank"}
[![Image](/images/Course-DockerCrashCourseForJavaSpringBootDevelopers.png "Docker Crash Course for Java Spring Boot Developers")](https://www.udemy.com/course/docker-course-with-java-and-spring-boot-for-beginners/?couponCode=NOVEMBER-2019){:target="_blank"}

> in28Minutes is creating amazing solutions for you to learn full stack and the cloud - Docker, Kubernetes, AWS, React, Angular etc. [Click here ](https://github.com/in28minutes/learn#aws-and-cloud-courses){:target="_blank"} for the complete catalogue of 30 Courses.

