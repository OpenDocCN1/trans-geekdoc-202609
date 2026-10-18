

# Chapter 2: Model-Driven DevOps

## Why Model-Driven DevOps?

## Network Infrastructure Is Different

## What Is Model-Driven DevOps?

## What Is a Data Model?

## Source of Truth

## DevOps as a Framework

## DevSecOps: Baked-In Security

## Summary

# Chapter 3: Consumable Infrastructure

## APIs

### Why API over CLI?

## Platforms

### Physical Hardware Provisioning

### Consolidated Control Point

### Northbound vs. Southbound APIs

### API and Feature Normalization

### Fabricwide Services

### Scalability

## Summary

# Chapter 4: Infrastructure as Code

## Why Infrastructure as Code?

## Source of Truth

### Data Models

### Common IaC Tools

### Organization

### Types of Source of Truth

## Code

### Data Flow

## Summary

# Chapter 5: Continuous Integration/Continuous Deployment

## CI/CD Overview

### Applications vs. Infrastructure

### CI/CD in Action

## Source Code Management

### Core Features

### Collaboration Features

### SCM Summary

## Continuous Integration Tools

### CI Engines

### How They Work

### Sample Workflow

## Infrastructure Simulation Tools

### Cisco Modeling Labs

## Test and Validation

### Linting

### Schema/Model Validation

### Functional Testing

### Test and Validation Summary

## Continuous Deployment

## Continuous Monitoring

## Summary

# Chapter 6: Implementation

## Model-Driven DevOps Reference Implementation

## The Goal

## DevOps Roadmap

## Architecture

### Network as an Application

### Consistency

## Simulation

## Automation

### Creating a Source of Truth

### Moving Data

### MDD Source of Truth

### Automation Tooling

### MDD Data

### Automation Runner

### Cisco Network Services Orchestrator

## Testing

### Linting

### Snapshotting the Test Network

### Data Validation and State Checking

#### Data Validation

#### Pushing Data to the Devices

#### State Checking

#### Restore

## Continuous Integration Workflow Summary

## Deployment

### Scale

### Starting Workflows

## Summary

# Chapter 7: Human Factors

## Culture and the Need for Change

## Start with the Why

## Organization

### Leadership

### Role Models

### Building a Team

### Break Down the Silos

### Community

### New Tools

### Summary of Organization-Level Changes

## Individual

### Programming vs. Automation

### Version Control Tools

### Data Formats

### APIs

### Templating

### Linux/UNIX

### Wait! Where Do I Fit In?

## Summary

# Index

## Preface

The Internet is built on network infrastructure. Many technologies, and by extension many economies and societies, are built on the Internet. Unfortunately, the way organizations deploy and maintain these critical networks has not changed meaningfully in 30 years. Network infrastructure operations is often a very human-intensive and manual process, making it prone to error and slow to react to business needs. The DevOps model promises to dramatically improve infrastructure operations using automation, tools, and processes designed to increase agility, scale, security, compliance, and reliability. Although DevOps has been used to great effect in applications development and management of cloud infrastructure, there has been no comprehensive, structured approach for applying DevOps to network infrastructure.

One primary way in which DevOps applied to network infrastructure differs from application DevOps is the number of elements managed and the amount of data on each of those elements. Essentially, this makes network infrastructure DevOps a data management problem. Networking vendors use data models to organize the data within each individual network element and to regularize their APIs, yet these data models are different between vendors and even between device families from the same vendor. Model-driven DevOps seeks to normalize the data models used to organize the data across the entire infrastructure as well as to normalize the code. In a sense, model-driven DevOps is intended to provide a repeatable, deterministic way to apply DevOps to network infrastructure and achieve the same benefits as DevOps applied to cloud infrastructure.

### Vision

This book represents a journey that the authors have taken over the last couple of decades. We all started our careers with our hands on a keyboard, running large networks and even supercomputers. Driven partly by the demands of the organizations that we have worked for and partly by laziness, we have leveraged some form of automation through it all. As we progressed throughout our careers, some of us went into consultancy, some development, and some management. We have been privileged to work with, and for, many amazing companies with many talented people. It was our vision that this book contains the distillation of what we have learned over the years and how we apply it to solving customer challenges today. Using this experience, we seek to provide a holistic approach to applying DevOps to infrastructure operations organizations. This book lays down an extensive foundation that helps developers and operators apply and tailor the detailed, prescriptive approach laid out for infrastructure DevOps. Furthermore, it addresses the human and organizational factors that, left unaddressed, cause many organizations to fail.

