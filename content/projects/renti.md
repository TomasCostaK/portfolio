---
title: "Renti - A Renting Marketplace (University Project)"
date: 2024-07-20T00:07:37+01:00
tags: ["Frontend", "Docker"]
author: "TomasCostaK"
description: "Renti was a product developed during university, where I got to learn quite a lot about Frontend (React) and Docker"
cover:
    image: "covers/renti.png"
    relative: true
showtoc: true
---
We all have more equipment that we don’t use than we actually think. Equipment that we don’t want to sell for fear of needing it in the future, which leads to the equipment deteriorating and losing its value. On the other hand, we have a lot of equipment that we probably only need to use once or twice a year, so we need to keep it, but we can rent it out for the rest of the time.

From a buyer's perspective, we often need equipment for a short duration. Whether it’s a good camera, DJ equipment, a fishing rod, or even a game console for a weekend with friends.

Given this problem, the idea arises to create an online marketplace platform for equipment rental. Instead of selling the equipment to the customer, the user loans it out for a set period.
This way, we can: spend less, help the environment, and make money!

On this project, I worked mostly on the **Frontend** and **Docker**. Below is a description of the work and the architecture for this project

## Project Backlog
For backlog management we are using GitLab Boards and Milestones, assigning each task to a specific developer.  
We are experiencing GitLab instead of Jira, to expand our technology stack, and see how well it works.
![](../images/gitlab_boards.png)

## Related Repositories
This [group](https://gitlab.com/renti-software) is subdivided in 6 repositories:  

* Renti (Serves as main repository, for backlog management and reporting)  
* Backend  
* External API  
* Frontend-Mobile  
* Frontend-Web  
* Compose  

## Static Analysis
We are making use of static code analysis engines to evaluate our code quality and prevent errors.
As of the specific code quality metrics, we opted by using GitLab Code Quality.  

This set of tests use Code Climate Engines. This reports code errors, security problems,
vulnerabilities, code smells, and other errors based on common standards, and easily integrates it with
each commit and merge request in GitLab.  

This code analysis is then integrated with the Gitlab CI pipeline for the project, as explained ahead.
Having access to this tool allows us to identify errors we probably would miss otherwise, and to learn
how to write better code.

## CI/CD Environment
As in previous projects, we implemented a CI/CD workflow using Gitlab.  

On each commit made to the code repository, a pipeline is triggered. This pipeline is responsible for
conducting the previously mentioned code quality static analysis, and produce the respective report,
as well as conducting tests, building the source code into packages, and continuously deploying
the services.

## Architecture + Technologies

![Arch](../images/arch.png)

Everything was containerized using **Docker**, managed by **Docker Compose**.  

