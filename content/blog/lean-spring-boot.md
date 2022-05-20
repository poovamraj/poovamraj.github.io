---
author: "Poovamraj T T"
title: "Make Spring Boot Lean And Mean - Throwing Away Hibernate and Java from Spring Boot"
date: "2021-05-17"
description: 
tags: ["spring boot", "jooq", "kotlin"]
ShowToc: false
---
Developing a backend application requires huge stability and data modeling is one of the pieces of software that is toughest to migrate hence choosing a reliable and stable technology is a necessity.

Spring Boot is one of the most reliable frameworks in the Java ecosystem. There are great efforts in developing leaner and better frameworks but Spring Boot seems to have great examples and solutions to many common problems faced in backend development. But it is hard to overlook the aged development methodology and impact on productivity.

I recently started writing an application and I have overhauled my Spring Boot boilerplate to ensure the latest development productivity improvements can be ensured where ever possible

## Data Layer Improvements - Irritating parts of Hibernate

1) I realized OneToOne mapping can have multiple entities on the child table unless we mark it with unique=true. This is one such example where we have to understand the nook and cranny of Hibernate just to avoid severe issues.

2) Bidirectional mapping to join from child to parent

3) Writing complex queries are sometimes impossible due to the domain structure we design

4) Defining your SQL tables with Java POJOs might feel all good initially until the reality of complex DB migrations comes into the workflow.

Initially, to overcome writing the complex queries issues which were impossible with Hibernate, I started looking for replacements that were strongly typed. I stumbled upon jOOQ which I fell in love with instantly. But to be on the cautious side I integrated it and used it just for complex queries. After all, jOOQ itself mentions Hibernate is good for CREATE, UPDATE, and DELETE operations.

jOOQ has the coolest features that no other ORM I have seen has. It generates the Object representation of your Tables using a code-gen module.

This can be done by connecting it to a Database but I felt this was an unwanted dependency at build/dev time.

I overcame this by integrating Liquibase using which jOOQ can generate the Object representation. Initially, this felt like overkill but understanding the uses of DB Migration libraries like Flyway/Liquibase made me realize how important such a tool is for DB migration.

Now that I had my DB definitions in Liquibase and Object definitions generated by jOOQ it felt obsolete to use Hibernate which I was only using for CREATE, UPDATE, DELETE operations and it started to feel more and more obsolete.

Finally, I took the big leap of removing the spring-data-jpa dependency as a whole.

## Improving Service Layer

Many shy away from Spring Boot because of it being a Java framework. After all, just after hearing the word Java, It is impossible for a developer to not be scared of some pattern like AbstractFactoryBuilderAdapter. But what we have to understand is that it is a JVM-based framework and languages like Scala and Kotlin integrate nicely with Spring Boot. Moving my application from Java to Kotlin felt like a breath of fresh air since I got all the following features along with it

1) Nullability checks
2) Type inference
3) Data classes
4) Concise code

The above efforts made my personal boilerplate feel very similar to Nodejs/Typescript/TypeORM combo that I use at my work.

Java/JVM is a great piece of software overlooked by many developers for shiny new frameworks. I have seen many startups and recently even a unicorn moving from languages like Go to Java due to many reasons. Some of the most complex features required for enterprise development are built into Java-based frameworks like Spring (For example - I was not able to find Access Control List feature in any other framework but in Spring)

[Originally Published in Dev.to](https://dev.to/poovamraj/make-spring-boot-lean-and-mean-throwing-away-hibernate-and-java-from-spring-boot-e77)