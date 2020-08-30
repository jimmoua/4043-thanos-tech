# Agile Quick Tutorial (Jira)
Jira is how we are going to be managing our project.

## Sprints
Sprints are essentially a small time frame in which we will compile a list of things that we want to accomplish for the project into a backlog and commit to that backlog. Our sprints are going to be 1 week sprints since Dr. S will have us do weekly reports anyways.

Below is a pretty good image on the cycle we will be trying to mimic (*except we will modify it bit*).

![](https://www.c-sharpcorner.com/article/scrum-framework-5-events-in-scrum-framework/Images/agile-software-development-700x469.gif)


1. **Sprint Planning and Meeting**: Sometimes, planning takes long. Other times, it can be very short. It depends on what needs to be implemented. We will be creating backlog of stories and tasks during this phase.
2. **Daily Scrum**: As already discussed, we will be having weekly scrum meetings instead of daily.
3. **Retrospective**: This is done at the end of the sprint. Usually, you talk about what went good and what went bad. For this, we will just talk about what went bad (if any) since our scrum meetings and retrospective will happen once weekly.
4. **back to step 1**

**What happens if we don't complete a backlog item for the sprint?** In this case, we will mark it in the Jira as a **carry over** into the next sprint, denoting that the story is, well, a carry over from the previous sprint. **It's really bad to have a lot of carry overs**, so please try to get your stories finished.

## Story Pointing
I hear that everyone does story pointing a little differently depending on the organization, but below is what I have used.

When we create a backlog of stories, we will be assigning story points to these. Story points follow a Fibonacci sequence of `1, 2, 3, 5, 8` and so forth with 1 being the least time consuming. **I have never seen a story that had any points greater than 8**. If something is greater than an 8, we will probably have to break it down. I'm going to assume that the majority of our stories will be between 1 and 5. I have seen a 0.5 story point, but these usually belong to stories that just require us to upgrade a package or something really small.

Here is a table on how I've interpreted story points:

| Points | Complexity Estimation                                          |
| :----: | :------------------------------------------------------------- |
|  0.5   | Extremely minute                                               |
|   1    | Should not be too complex                                      |
|   2    | Does not take a lot of effort, but it isn't too complex either |
|   3    | A moderate and standard amount of work put in                  |
|   5    | Could be time consuming                                        |
|   8    | Very time consuming                                            |

**Story points can be deceiving**, since they are just estimates to how complex a story might be. A 1-pointer may actually become a 3-pointer vice-versa. During our weekly meeting, we can re-point a story if needs be.

## Story Cycle
Here is how our typical story cycle is going to go.

### 1 - Backlog
We will meet weekly and develop a backlog of stories, point them, and then assign them to team members. These backlogs will be moved into the sprint for that week.

### 2 - Tech Design
This is the technical design phase for a story. Usually, these will just be words on how to will do something. Sometimes, you might have to submit a flowchart of something (we'll be using these for the documentation that will have to be submitted via BlackBoard). This is usually a pretty high-level and abstract view of model that is going to be implemented.

**Example**:

|             Story             | Tech Design                                                                                         |
| :---------------------------: | :-------------------------------------------------------------------------------------------------- |
|      Display Login Error      | Redirect the user back to the login page with errors with appropriate HTTP status code and message. |
| Save the user to the database | Save user credentials to database. (requires diagram on how to encrypt and save to DB)              |

### 3 - In Progress
This one is pretty straightforward. It is the implementation phase of our stories.

When creating a new branch to implement on, name it after the Jira key and tag. For example, [**`SAD-3`**](https://thanostech.atlassian.net/browse/SAD-3) is setting up the backend for this project. **`SAD`** is the key and the tag is **`3`**.

You can quickly access a full-view of a story if you provide the key and tag number at the end of this URL:

```
https://thanostech.atlassian.net/browse/KEY-TAG
```

### 4 - In Review
After you finished implementing, you will have to submit a pull request (PR) on GitHub. **Notice how every Jira story has a key and a number tag associated with it**? For example, ours is **`SAD-#`**. When labeling your PR, please label it the same name as the Jira key and tag number.

When creating a PR, fill out the template.

I always find code reviews super helpful. You can learn a lot from it and give suggestions to improve other's code. **You must receive two approvals in your PR to have it able to be merged to master**.

After that, rebase your PR and perform a squash of commits into a single commit. At the top of that commit, make sure you name it the Jira key and tag number.

### 5 - Done
Once you've merged to master, move your story into the **Done** panel of the Kanban board.