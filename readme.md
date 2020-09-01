<h1>4043 Systems Analysis II - Thanos Tech</h1>
This is the repository for general documentation.

<h1>Developer Links</h1>

You will be visiting these links quite frequently, so it's a good idea to bookmark them.

|     Description     |                            Link                             |
| :-----------------: | :---------------------------------------------------------: |
| Backend Repository  |         https://github.com/jimmoua/bams_barber_shop         |
| Frontend Repository |         https://github.com/jimmoua/bams-barber-shop         |
|        Jira         |              https://thanostech.atlassian.net/              |
|       Jenkins       | http://ec2-3-16-27-37.us-east-2.compute.amazonaws.com:8080/ |

<h1>Table of Contents</h1>

- [SDLC Tools](#sdlc-tools)
  - [Team Communication Software](#team-communication-software)
  - [Source Control](#source-control)
  - [Software Methodology](#software-methodology)
  - [Continuous Integration and Continuous Delivery](#continuous-integration-and-continuous-delivery)
- [Project Details](#project-details)
- [Tech Stack](#tech-stack)
- [Roles](#roles)

# SDLC Tools
Below are the tools that are going to be used to aide us in the SDLC.

## Team Communication Software
Just like COMS 4033, we will be using [Discord](https://www.discord.com/), since we should be most familiar with it.

## Source Control
For source control, We'll be using [Git](https://git-scm.com/) and hosting the project on [GitHub](https://github.com).

## Software Methodology
We are going to use the agile scrum methodology. The agile software that we will be using is called [**Jira**](https://www.jira.com). In Jira, we can a backlog as well as the status of stories in a Kanban board. I have a Jira set up for our team already [here](https://thanostech.atlassian.net/).

We will be having scrum meetings **every week** on Thursday from 2:30pm - 3:50pm (CST), although this may be subject to change if there is a class meeting that day.

## Continuous Integration and Continuous Delivery
We are going to be using **Jenkins** for CI/CD. Our Jenkins server can be found [here](http://ec2-3-16-27-37.us-east-2.compute.amazonaws.com:8080/).

What is Jenkins? Here is a small excerpt from Wikipedia.

> Jenkins is a free and open source automation server. It helps automate the parts of software development related to building, testing, and deploying, facilitating continuous integration and continuous delivery.

To keep it short, we will all be commiting code to the code repository. **We need to make sure that every time we make a push, our code is able to merge with the master branch and that all unit tests pass**. This helps with merge conflicts and making sure nothing breaks when pushing new code commits. Every time we make a push to the GitHub repository, I will have Jenkins set up so that it will do these steps in the following order:

1. Builds the project for a specific branch
2. Runs unit tests to see if they pass
3. Deploy to a server (if needed)

If any of these steps fail, **the developer responsible for the commits that broke the Jenkins build needs to go back and fix their code so that it may merge with master without any major issues**.


# Project Details
> We'll be developing a web-based application that allows customers to create accounts and schedule appointments with selection of various styles or services. We’ll also allow people to reschedule. This will also allow the Owner to view all appointments and provide customer contact information.

1. A calender view that displays a list of free time slots in which users may schedule appointment.

# Tech Stack
We will be going with the MERN stack, but replace MongoDB with MySQL.

+ **(M)** ySQL for database
+ **(E)** xpress for our web application framework
+ **(R)** eact for our frontend client
+ **(N)** odeJs for our JavaScript environment (runs our backend server)

# Roles

|  Member   |                      Role                      |
| :-------: | :--------------------------------------------: |
| Shiddarth |               Frontend developer               |
|   Fahim   |               Backend developer                |
|   Cade    | Systems/API Designer & Dev + Solutions Analyst |
|    Jim    |               Fullstack + DevOps               |
