---
title: "Blog 1"
date: 2026-06-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is a summary of the blog I read and posted during my internship. It is not an official replacement for the original AWS article.
{{% /notice %}}

# USER AUTHENTICATION AND SESSION MANAGEMENT WITH AMAZON AURORA DSQL

In modern backend systems, user authentication and session management are common features, but they can become challenging when the system grows. When users register, log in, create sessions, or log out, the data must be recorded correctly and reflected almost immediately. If the system has synchronization delay or inconsistent data, both user experience and security can be affected.

The original article from AWS Database Blog introduces how to build a user authentication and session management service with **Amazon Aurora DSQL**. The solution combines Aurora DSQL with **Amazon ECS**, **AWS Fargate**, and **AWS IAM** to create an authentication backend that is scalable, more secure, and requires less manual database infrastructure management.

━━━━━━━━━━━━━━━

## Problem Context

An authentication service usually needs to handle features such as:

- Registering new users.
- Logging in and verifying user credentials.
- Creating session tokens.
- Checking whether a session is still valid.
- Revoking sessions when users log out.
- Storing user and session information securely.

These operations require high accuracy. For example, after a successful login, the new session should be available for validation immediately. When a user logs out or a session is revoked, the system also needs to reflect that state quickly to avoid security risks.

━━━━━━━━━━━━━━━

## Solution Architecture

The solution in the blog uses a container-based backend architecture connected to Aurora DSQL:

- The client sends requests to the backend through HTTPS.
- The backend application runs on Amazon ECS with AWS Fargate.
- The application connects to Amazon Aurora DSQL.
- AWS IAM is used to support a more secure authentication mechanism.
- User and session data are stored in tables such as `users` and `sessions`.

A key point is that the backend does not need to manage database instances in the traditional way. Aurora DSQL provides a PostgreSQL-compatible SQL model and supports strong consistency, which is suitable for workloads that require accurate data visibility after writes.

━━━━━━━━━━━━━━━

## Key Highlights

- **Amazon Aurora DSQL is suitable for authentication workloads:**  
  Authentication systems require strong consistency, especially for login, session creation, session validation, and session revocation.

- **Strong read-after-write consistency:**  
  After data is written, the system can read the updated state consistently, reducing risks caused by replication lag.

- **Less database instance management:**  
  With Aurora DSQL, developers can focus more on application logic instead of manually operating database instances.

- **IAM authentication:**  
  Instead of relying only on fixed database passwords, the system can use IAM to improve the security of application-to-database connections.

- **Session tokens are not stored in plaintext:**  
  Session tokens should be hashed before being stored in the database. This helps reduce risk if data is exposed.

- **User passwords are hashed:**  
  Passwords should be hashed with a suitable algorithm such as bcrypt before storage.

- **Avoiding user enumeration:**  
  When login fails, the system should return a generic error instead of revealing whether an email or account exists.

━━━━━━━━━━━━━━━

## Main Processing Flow

### User Registration

When a user registers, the backend receives information such as email and password. The password is not stored directly. It must be hashed before being written to the `users` table. This reduces risk if the database is accessed without authorization.

### Login

When a user logs in, the backend verifies the credentials, compares the hashed password, and creates a session token if authentication succeeds. The actual session token is sent to the client, while only the hash of the token is stored in the database.

### Session Validation

When the client sends a request with a session token, the backend hashes that token and compares it with the data in the `sessions` table. If the session is not expired and has not been revoked, the request is considered valid.

### Logout

When the user logs out, the system updates the session state, for example by setting `revoked_at`. This prevents the session from being used for later requests.

━━━━━━━━━━━━━━━

## What I Learned

Through this blog, I understood that an authentication service is not only a simple login/logout feature. It is an important part of the backend, directly related to security, data consistency, and user experience.

I also learned how AWS combines multiple services to solve a real-world problem:

- **Amazon Aurora DSQL** for a strongly consistent SQL database layer.
- **Amazon ECS and AWS Fargate** for the containerized backend.
- **AWS IAM** to support more secure authentication between the application and database.
- Best practices such as password hashing, session token hashing, and generic login errors to avoid leaking user information.

This article gave me a better perspective on designing backend authentication for personal projects. If I build a system with login, session management, or user authorization in the future, I need to care not only about whether the API works, but also about how sensitive data is stored, how sessions are revoked, and how to ensure consistent reads and writes.

━━━━━━━━━━━━━━━

## Original Article

AWS Database Blog:  
https://aws.amazon.com/vi/blogs/database/user-authentication-and-session-management-with-amazon-aurora-dsql/

AWS Study Group:  
https://www.facebook.com/groups/awsstudygroupfcj/permalink/2205379233560370/

## Image

![user authenticattion](/images/3-BlogsPosted/DBBLOG-5625-1.png)