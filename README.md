# Spring Auth Server

This is a Spring Boot--based **Authorization Server**
that handles user authentication and issues OAuth2 access tokens for
clients.\
As the project name suggests, it authorizes requests for viewing a
customer's details using standard OAuth2 flows.

This Authorization Server supports two roles/authorities:

-   USER
-   ADMIN

------------------------------------------------------------------------
   
## Overview

This project implements an OAuth2 Authorization Server using **Spring
Authorization Server**, built on top of Spring Security. It can:

-   Authenticate users
-   Issue JWT access tokens
-   Manage user roles (USER, ADMIN)
-   Be extended to secure REST APIs (e.g., customer details) by
    validating tokens

------------------------------------------------------------------------

## Features

-   OAuth2 / OIDC compliant authorization server
-   JWT token issuance
-   Role‑based authorization (USER, ADMIN)
-   Easily integrable with client and resource servers

------------------------------------------------------------------------

## Prerequisites

-   Java 17+
-   Maven

------------------------------------------------------------------------

## Running the Application

1.  Clone the repository:

        git clone https://github.com/ritujane78/spring_auth_server.git

2.  Navigate into the project directory:

        cd spring_auth_server

3.  Run the application:

        mvn spring-boot:run

The Authorization Server will start on **http://localhost:9000** by
default.

## OAuth2 Endpoints

Typical endpoints exposed by the Authorization Server:

-   `/oauth2/authorize` -- Authorization endpoint
-   `/oauth2/token` -- Token endpoint
-   `/oauth2/jwks` -- JSON Web Key Set
-   `/.well-known/openid-configuration` -- Server metadata

------------------------------------------------------------------------

## Example In‑Memory Users

``` java
@Bean
public InMemoryUserDetailsManager users() {
    UserDetails user = User.withUsername("user")
        .password("{noop}password")
        .roles("USER")
        .build();

    UserDetails admin = User.withUsername("admin")
        .password("{noop}password")
        .roles("ADMIN")
        .build();

    return new InMemoryUserDetailsManager(user, admin);
}
```

------------------------------------------------------------------------

## Customization

You can enhance this project by:

-   Persisting users and clients using JPA
-   Adding custom JWT claims
-   Integrating with a Resource Server for customer APIs

------------------------------------------------------------------------
