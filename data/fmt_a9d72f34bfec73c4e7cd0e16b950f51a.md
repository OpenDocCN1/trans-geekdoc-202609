
# Go 后端编程

## 序言

您已抵达“使用 Go 编程后端”。嗨！我是 Julian Braun，我迫不及待地想向您展示 Go 后端开发的所有酷炫内容。多年来使用 Go 的经验让我看到了它在构建可扩展、高性能后端系统方面的有效性和高效性。无论您是经验丰富的开发者还是刚刚涉足后端编程的世界，我希望这本书对您都有用。

Google Go 语言，也称为 Golang，以其简洁、高效和可靠性而闻名。当速度和可扩展性至关重要时，它在后端开发中表现出色。在整本书中，我们将探索如何发挥 Go 的全部潜力，通过构建能够满足现代 Web 环境需求的真实应用程序和服务。

为了开始，我们将设置开发环境并确保您拥有完成所需的一切。我将向您展示如何设置 Visual Studio Code、安装 Go，并使用 `Go modules` 管理依赖项。良好的配置环境可以极大地提高您的生产力和开发便利性，因此对于任何有兴趣深入 Go 编程的人来说，这一步都是必不可少的。

一切准备就绪后，我们将学习使用 Go 的 `net/http` 包构建 Web 服务器。本书将教您提供静态文件、响应请求以及将各种 URL 路由到其各自处理程序的来龙去脉。作为更高级主题的基础，这些技能是 Web 开发的基石。

在后续章节中，我们将学习 `gorilla/mux` 包中实现的更复杂的路由方法。有了这个强大的库，您可以轻松构建具有更具表现力和灵活的 URL 处理功能的复杂 Web 应用程序。此外，我们还将讨论错误处理、自定义处理程序和中间件，以确保您的应用程序坚固且易于维护。

安全是后端开发的重要组成部分，我们将对此进行广泛的介绍。您将了解如何构建保护用户和数据信息的应用程序，从使用 `OAuth2` 和 `JWT` 集成用户身份验证，到保护您的应用程序免受 SQL 注入和 XSS 攻击等常见漏洞的侵害。

Go 因其顶级的并发和并行支持而脱颖而出。我们将充分利用这一点，通过创建和实现微服务。您将了解如何使用 `Gin` 和 `Kubernetes` 等工具创建、启动和监督可扩展的微服务。此外，我们还将介绍 `REST` 和 `gRPC` 用于服务间通信，这将使您能够构建高效且凝聚的面向服务架构。

高效管理数据是许多应用程序的基础，而 `GORM` 将教您做到这一点。我们将涵盖 CRUD 操作的基础知识以及更复杂的功能，如事务、迁移和并发控制。此外，您还将了解使用 `Apache Kafka` 和 `NSQ` 进行消息代理，这将使您能够创建能够以高吞吐量处理异步工作负载的应用程序。

我们将学习 `Delve`、`Testify` 和 `GoMock` 等工具，这些工具对任何开发者都至关重要，以帮助进行测试和调试。您将学习如何编写全面的测试、模拟依赖项以及调试应用程序以确保可靠性和无错误。

最后，我们将讨论部署策略，例如蓝绿部署、金丝雀部署和滚动部署。通过学习如何使用 `AWS CodeDeploy` 自动化部署流程，您可以随时保持应用程序平稳运行和最新状态。

“使用 Go 编程后端”不仅仅是一本书，它是让您成为专家级 Go 后端开发者的全方位手册。无论您开发的系统是简单的 Web 应用程序还是复杂的分布式系统，您在这里获得的知识和技能都将非常有用。因此，让我们直接开始，开始创造魔法吧。

![](img/image-0-0.jpg)

### Go Web 应用结构

项目结构概述 目录概述 示例程序：在 gitforgits.com 中采用结构

总结

## 第 3 章：使用 gorilla/mux 进行高级路由

章节概述

### gorilla/mux 介绍

为什么选择 Gorilla Mux？ 使用 Gorilla Mux 入门

## 高级路由技术

正则表达式约束 子域路由 查询参数路由

## 路径变量

定义路径变量 访问路径变量 管理路径变量

### 基于正则的路由

理解正则 基于正则路由的优势 实现基于正则的路由 测试基于正则的路由

### 自定义处理程序和中间件

自定义处理程序和中间件的目的 在 Gorilla Mux 中创建自定义处理程序和中间件 自定义处理程序 中间件 示例程序：使用自定义处理程序管理路由

## 错误处理和 HTTP 状态码

理解 HTTP 状态码 实现错误处理 自定义错误处理程序 使用中间件进行错误处理 示例程序：处理特定错误

### 执行 RESTful 路由

理解 RESTful 路由 使用 Gorilla Mux 实现 RESTful 路由 设置 Gorilla Mux 路由器 定义处理函数

## 构建 CRUD 操作

设置环境 定义 Book 模型 构建处理程序 创建 (POST) 读取 (GET) 更新 (PUT) 删除 (DELETE) 组装路由器并启动服务器

总结

## 第 4 章：使用 Oauth2 和 JWT 进行用户身份验证

章节概述

## 用户身份验证基础

什么是用户身份验证？ 用户身份验证的工作原理 凭证验证 会话创建和管理 使用身份验证保护路由

### 使用 Go 使用 OAuth2

设置 OAuth2 注册应用程序 设置 OAuth2 客户端 OAuth2 中的流程

## 与社交媒体登录集成

与 Google 登录集成 与 Facebook 登录集成 设置 Facebook OAuth 配置 处理 Facebook 回调 与电子邮件登录集成

### 实现 JWT 以保护 API

JWT 用于保护 API 的优势 实现 JWT 安装 JWT Go 包 创建 JWT 令牌 设置 HTTP 端点使用 JWT 创建中间件保护路由

### 会话和 Cookie 管理

理解会话和 Cookie 管理基于 Cookie 的用户会话 安全会话管理技术

### 用户注册和密码管理

创建用户注册和密码管理

## 内容

前言 GitforGits 致谢

## 第 1 章：理解 Go 后端开发

章节概述 Go 及其生态系统 核心特性 标准库 Go Modules 和包管理 后端开发的流行库 消息传递和流处理 安全与身份验证 容器化和虚拟化 网络和协议 测试和部署

## 安装 Go

准备和下载 安装 设置环境 验证

## 设置 Visual Studio Code

安装 VS Code 和 Go 扩展 配置 Go 扩展 设置工作区 调试设置 测试集成

## Go Modules for Package Management

What are Go Modules? Setting up New Module Adding Dependencies Understanding go.mod File Using go.sum File Managing Upgrades and Downgrades

## Basics of a Go program

Basic Structure of a Go Program Variables and Types Control Structures If statement For loop Switch statement Arrays, Slices, and Maps Arrays Slices Maps Functions Concurrency with Goroutines

### Introduction to ‘gitforgits.com’ Project

Project Overview Functional Requirements Technical Requirements Design Considerations Quick Project Code Structure

### Git for Version Control

Why use Git? Basic Git Commands Adding Files and Committing Changes Branching Viewing Changes and Logs Merging Branches Handling Merge Conflicts Using Git with Remote Repositories

### Docker Basics

What are Docker Containers? Images and Containers Dockerfile Building and Running Docker Containers Docker Compose Starting and Managing Project Containers Volumes and Networks

Summary

## Chapter 2: Building a Basic Web Server with net/http

Chapter Overview

### Introduction to ‘net/http’ Package

Core Components of net/http Working with HTTP Servers Deep Dive into HTTP Handlers Understanding Request and Response

### Creating your first web server

Setup Basic HTTP Server Handling Different Routes Handling HTTP Methods Query Parameters and URL Fragments Running and Testing Server

### Understanding Request and Response Structures

HTTP Request Structure HTTP Response Structure Flow of Request and Response Client Request Server Handling Server Response Client Receives Handling of Requests and Responses

### Basics of Routing with http.ServeMux

Understanding Routing Introduction to http.ServeMux Features of http.ServeMux Sample Program: Routing with http.ServeMux

### Handling Different HTTP Methods

HTTP Methods GET POST PUT DELETE PATCH HEAD OPTIONS TRACE CONNECT Sample Program: Implementing Handlers

### Query Parameters and URL Fragments

Importance of Query Parameters and URL Fragments Query Parameters URL Fragments Sample Program: Utilizing Query Parameters and URL Fragments Handling Query Parameters URL Fragments for Client-Side Handling Testing Implementation

### Serving Static Files and Assets

Types of Static Files and Assets Serving Static Files Structuring Static Directory Testing Static File Serving

### Structuring Go Web Application

Project Structure Overview Directories Overview Sample Program: Adopting Structure in gitforgits.com

Summary

## Chapter 3: Advanced Routing with gorilla/mux

Chapter Overview

### Introduction to gorilla/mux

Why Gorilla Mux? Up and Running with Gorilla Mux

### Advanced Routing Techniques

Regular Expression Constraints Subdomain Routing Query Parameter Routing

### Path Variables

Defining Path Variables Accessing Path Variables Managing Path Variables

### Regex-based Routing

Understanding Regex Advantages of Regex-Based Routing Implementing Regex-Based Routing Testing Regex-Based Routing

### Custom Handlers and Middleware

Purpose of Custom Handlers and Middleware Creating Custom Handlers and Middleware in Gorilla Mux Custom Handlers Middleware Sample Program: Manage Routing with Custom Handlers

### Error Handling and HTTP Status Codes

Understanding HTTP Status Codes Implementing Error Handling Custom Error Handler Using Middleware for Error Handling Sample Program: Handling Specific Errors

### Perform RESTful Routing

Understanding RESTful Routing Implementing RESTful Routing using Gorilla Mux Setting up Gorilla Mux Router Defining Handler Functions

### Building CRUD Operations

Setting up the Environment Defining Book Model Building Handlers Create (POST) Read (GET) Update (PUT) Delete (DELETE) Assembling the Router and Starting the Server

Summary

## Chapter 4: User Authentication with Oauth2 and JWT

Chapter Overview

### Basics of User Authentication

What is User Authentication? Working of User Authentication Credential Verification Session Creation and Management Using Authentication to Protect Routes

### Using OAuth2 with Go

Setting up OAuth2 Register the Application Setting up OAuth2 Client Flows in OAuth2

### Integration with Social Media Logins

Integration with Google Login Integration with Facebook Login Setting up Facebook OAuth Configuration Handling Facebook Callback Integration with Email Login

### Implementing JWT for Secure APIs

Advantages of JWT for Secure APIs Implementing JWT Install the JWT Go Package Create the JWT Token Setup HTTP Endpoint to use JWT Create Middleware to Protect Routes

### Sessions and Cookie Management

Understanding Sessions and Cookies Managing Cookie-Based User Sessions Secure Session Management Techniques

### User registration and Password Management

Creating System for User Registration and Password Mgmt User Registration API Managing and Protecting Passwords Defining Password Policies

### Rate Limiting and Abuse Prevention

Understanding Rate Limiting Implementing Custom Rate Limiting Define Rate Limiter Structure Integrating Rate Limiting Protecting against DDoS Attacks

Summary

## Chapter 5: Integrating Databases with GORM

Chapter Overview

### Setting up GORM for ORM
