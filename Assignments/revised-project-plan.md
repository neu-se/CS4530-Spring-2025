---
layout: page
title: Revised Project Plan
permalink: /assignments/revised-project-plan
parent: Assignments
nav_order: 5
---

# Revised Project Plan **Due Wednesday February 26, 12:00pm (noon) ET**{: .label .label-red }
You should use the feedback on your preliminary project plan to revise the scope of your project, and discuss any changes with your assigned TA. The goal of this assignment is to finalize the intended scope of your project based on these discussions and to outline the tasks that you will need to accomplish in order to complete your project.

Your assigned TA mentor will review your project plan and provide you with feedback on the scope and details provided in your preliminary plan.
In this deliverable, you will revise your project plan based on that feedback, and any preliminary research tasks that you have completed.
If there were any deficiencies or concerns noted by your TA mentor on your preliminary plan, you *must* address those concerns in this revised plan.
If you are unsure of how to address any of these concerns or if you have addressed them, please discuss them with your TA mentor before submitting this revised plan.

We list page *maximums* for each section as general guidance of what we are willing to grade. Please do not feel compelled to use all of the pages provided, and remember that a diagram or table can be as expressive (or more) as a comparable amount of text.

## Revised Problem Statement, User Stories and Acceptance Criteria (max 4 pages)
Your project plan should begin with a 1-3 paragraph introductory problem statement: what problem in StackOverflow do your (proposed) features solve?  Provide a clear description of the feature or features you are proposing. For example, if you are proposing a "secure chat" feature, explain what you mean by "secure". 

Given the problem statement, develop exactly 3 user stories that show how a user would interact with the features. User stories are requirements specified in the following format 
"As a < type of user >, I want < some goal > so that < some reason >."
My conditions of satisfaction are < list of common cases and special cases that must work >.

Your user stories should cover the key behavior or qualities that your features will provide.

**EACH USER STORY MUST INCLUDE ONE OR MORE ESSENTIAL, DESIRABLE and EXTENSION CONDITION(S) OF SATISFACTION**. Please make sure that your conditions of satisfaction are complete (i.e., cover all common cases) and can be turned into testable behaviors.

Each user story and condition of satisfaction must have a priority (Essential, Desirable, or Extension). The set of Essential items will constitute the "Minimum Viable Product". 

Some of your proposed projects are primarily about some non-functional quality of the code base and have little or no user impact. For these, you may want to write stories of the form "As a project owner, I want ...".  You still need to offer a reason why a project owner might want the proposed goal to be accomplished.

Do not provide more than three user stories. Your problem statement and description of user stories and conditions of satisfaction should be between 2-4 pages.

The user stories must be numbered (1,2,3) and each the conditions of satisfaction must likewise be numbered (1.1, 1.2, 1.3) and laid out in a table for easy reference.

This revised project plan should be a standalone document (it is OK to copy/paste from the preliminary plan in this case).

## Revised Work Breakdown (max 10 pages)
Given the project concept that you have chosen and the functionality that you expect to implement to satisfy your user stories, define a breakdown of the work that will be necessary to complete the project. This breakdown is required for all essential, desirable and optional tasks. 

A work breakdown includes all of the tasks necessary to accomplish the project, and will be an artifact that we will refer back to throughout the project to evaluate whether you are making satisfactory progress.
Consider all of the kinds of tasks that your team will need to perform, including knowledge acquisition, design, implementation, testing and documentation tasks.
It is hard to say (generically) how many work items are necessary.

Each task on the work breakdown should be assigned to exactly one team member (as primary responsible party), who should provide a "T-Shirt" estimate for how long it will take (along with a justification for that estimate). Feel free to assign a second person as secondary responsible party (if you plan to use pair programming) but make clear who has primary responsibility.

Consider the dependencies between tests: perhaps an API needs to be designed and specified before implementation can begin; perhaps your development environment needs to be configured before anything else can proceed.
Assign tasks to sprints considering these dependencies.

Given the preliminary nature of your plan, we do not expect that you will know all of the details about precisely how to implement your feature such that you could break it down into tasks that you feel could be implemented in a day or two. Large tasks (those which you can not provide a responsible estimate for) must be accompanied by smaller “research” tasks that can be performed early on in the project. You may wish to provide deadlines by which the task must either be refined into smaller tasks (based on new knowledge gathered), or reworked/abandoned.

In keeping with the agile philosophy, you should plan on spending these two weeks of the project in a "Sprint 0" in which you will undertake tasks you previously planned including those that help you improve your project plan.

For example: Consider if you were proposing the "job advertisement" feature, without the experience of having completed it. It might be difficult to consider how to break down a task like "Implement the frontend components for ad video playback" into something that you could commit to doing within a day or two. Given that this is a task that can be delayed until the end of the project (no other tasks depend on it), it would be wise to consider having some tasks early on in the project, such as: "Find react components that embed video ads," and "Implement simple video player that does not synchronize playback." Completing these smaller tasks early would let you both demonstrate that some forward progress is being made, and also allow you to create a much more responsible estimate for how that last, otherwise insurmountably large task would take.

**Do not wait for your TA feedback to begin this work.** You probably know more about the details of your project then they do. It will be helpful for all concerned if your Project Plan lists the major unknowns or things that you expect to need help with-- this will help the TA provide more useful feedback for you

Be realistic, and leave time for contingencies (including the time around the midterm exam).
Remember that you will need to have a demo prepared of your feature by project deadline - just 5 weeks from the due date of this assignment (not counting spring break).

If you are uncertain that some tasks will be feasible, then be sure to include evaluation tasks earlier-on in the project that will allow for "go/no-go" decisions to move forward on a task or drop it.

We understand that it is quite difficult to estimate the technical complexity of a new project (as you are doing in the case of this course).

Throughout the project period, teams will meet regularly with their dedicated TA Mentor, who will help track progress on a week-to-week basis and help to determine when adjustments to the project scope are needed.

Each work item should contain the following information:
* Task to be performed
* User story (or stories) that this task relates to
* Team member responsible for completing the task
* T-shirt size estimate of how long will be needed to complete the task, using the following buckets:
    * Small: Can likely be completed by one team member in one sitting of less than 3-4 hours
    * Medium: Likely to require involvement of multiple team members, over the course of 1-2 days
    * Large: Currently unable to provide a responsible estimate. 
* A brief (1-2 sentence max) justification of how you reached the size estimate of the task 
* Milestone for delivering the task, chosen from one of the following:
  * Sprint 0: Feb 12-Feb 25
  * Sprint 1: Feb 26-Mar 11 (Sprint 1 is just a single week, not counting the spring break)
  * Sprint 2: Mar 12-Mar 25
  * Sprint 3: Mar 26-Apr 9

Your work breakdown may take the format of a simple textual list.

**Mandatory update for all teams:** Even if your work breakdown is entirely unchanged compared to the preliminary plan, please be certain to include updates on all "sprint 0" tasks (those which were scheduled to be completed before the due date of this revised plan). Many teams included research/learning tasks in the first week to help inform the rest of the work breakdown: you should be certain to revise your work breakdown based on what you have learned so far.

**Please note that in order to receive full credit for the final delivered product, each team is expected to deliver Minimum Viable Product (marked as essential) as well as additional feature(s) proposed in the project plan (marked as desirables). Please plan your work accordingly.**

## Submission 
Your revised project plan should be submitted as a single PDF on Canvas under the assignment "Revised Project Plan."
Each team submits a single document. Make sure that your team number is added to the title of the document.

## Grading
The revised project plan will account for 10% of your project grade, and will be graded out of 100 points. The grading of the revised project plan is further broken down as follows:

### Introductory problem statement (5 points): 
* Receive full marks if there is a narrative consisting of 1-3 paragraphs that describes the specific problems that your project aims to solve, and provides a clear description of the feature or features you are proposing.
* Receive partial credit if the narrative is present, but does not describe the problems that the project aims to solve, or does not give a clear description of the feature or features you are proposing.

### User stories (45 points):
Each of the three user stories will account for 15% of your grade on this assignment and will be graded as follows:
* Receive full marks if:
  * The user story fits the problem statement
  * The user story satisfies the INVEST criteria for good user stories (construed quite broadly)
  * The user story includes conditions of satisfaction that cover the "normal" expected behavior of the feature, and any important error cases
  * Conditions of satisfaction can be turned into Testable behaviors
  * Conditions of satisfaction are prioritized
  * Each user story includes one or more condition of satisfaction marked with essential, desirable and extension priority. We recommend that your essential COS be twice the number of desirable COS.
  * Any deficiencies or concerns noted by your TA mentor on your preliminary plan are addressed

### Work breakdown (50 points):
Your work breakdown will be evaluated holistically on the following rubric:

#### Coverage of tasks needed (20 points):
Receive full marks if the work breakdown includes all (reasonably expected) tasks to implement your features, considering these kinds of tasks: 
  * Background research 
  * Design of interfaces and data types
  * Deployment of third-party services
  * Implementation
  * Testing
  * Documentation

It is not possible to state generically for all projects whether *all* of the above types of tasks are necessary.
However, we believe that this list is exhaustive (we do not expect other kinds of tasks).

#### Assignment of tasks (5 points):
Receive full marks if:
* Each element on the work breakdown is assigned to one team member
* Each team member is assigned work that includes development / coding, even if working with pair programming 
* The distribution of tasks of each size are roughly similar between the whole team (no single person is assigned significantly more or fewer tasks of one size)
* Any deficiencies or concerns noted by your TA mentor on your preliminary plan are addressed

#### Sizing of tasks (20 points):
Receive full marks if each element on the work breakdown:
* Has a size estimate (small, medium, or large) that is provided by the team member assigned the task.
* Has a responsible justification for that estimation
* Every "large" task:
  * Is accompanied by a reasonable explanation of why the team is unable to provide a responsible estimate
  * Is accompanied by at least one small or medium task, scheduled well-before the "large" task is due to be completed. We would expect that most of these research tasks are scheduled to sprint -1, or perhaps sprint 0.
* Any deficiencies or concerns noted by your TA mentor on your preliminary plan are addressed

#### Scheduling of tasks (5 points):
Receive full marks if each element on the work breakdown:
* Is assigned to a sprint
* There are no obvious constraint violations (tasks that logically must happen before others should be scheduled before them)
* There are no "Large" tasks scheduled in sprint 0
* Tasks scheduled to be completed before the deadline of this assignment have an update as to their status, and the work breakdown is updated to reflect the result of these tasks.
* Any deficiencies or concerns noted by your TA mentor on your preliminary plan are addressed