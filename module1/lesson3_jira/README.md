\# SEIR Foundations — Module 1, Lesson 3

\## Jira: A Day in My Shoes



\*\*Assignment:\*\* Week 5 — Jira and Agile Project Management  

\*\*Jira Space:\*\* SEIR-Saga-JMK  

\*\*Space Key:\*\* SEIR  

\*\*Epic:\*\* SEIR-1 — A day in my shoes  

\*\*Methodology:\*\* Scrum  

\*\*Space Type:\*\* Team-managed  

\*\*Estimation Method:\*\* Story Points



\---



\## 1. Project Overview



For this assignment, I created a Scrum space in Jira to break down a full day in my life as a cloud engineer.



I organized my day into five stories and 20 individual tasks covering everything from my morning routine and personal responsibilities to cloud infrastructure work, automation, troubleshooting, and technical development.



The purpose was to get a better understanding of how Agile works in practice, particularly how work is organized, estimated, and tracked using Jira.



I also wanted to understand how story points can be used to compare the complexity of different activities and how breaking work into smaller tasks can make it easier to manage.



\## 2. Jira Configuration



I created a new team-managed Scrum space named \*\*SEIR-Saga-JMK\*\* instead of using the existing Balerica AI incident-management project.



I configured the space to use Epic, Story, and Task work types. I also enabled sprints and story-point estimation.



| Setting | Configuration |

|---|---|

| Space name | SEIR-Saga-JMK |

| Space key | SEIR |

| Template | Scrum |

| Management | Team-managed |

| Work types | Epic, Story, Task |

| Workflow | To Do, In Progress, Done |

| Sprints | Enabled |

| Estimation | Enabled |

| Estimation method | Story points |



I selected story points because I wanted to estimate how much effort and complexity each activity involves rather than simply measuring how long it takes.



\### Evidence — Estimation Configuration



!\[Jira estimation enabled with story points selected](screenshots/jira\_estimation\_on.jpg)



\## 3. Epic — A Day in My Shoes



\*\*Issue Key:\*\* SEIR-1  

\*\*Work Type:\*\* Epic  

\*\*Story Points:\*\* Not assigned



My Epic represents one complete day, starting when my alarm goes off and ending when I go to sleep.



It covers my personal routines, meals, cloud engineering responsibilities, technical projects, and other daily activities.



I used the Epic as the Parent for all five stories and 20 tasks so that everything would be organized under the same overall objective.



I didn't assign story points to the Epic because it represents the entire day rather than an individual activity.



\### Evidence — Epic and Child Work Items



!\[Epic showing stories, tasks, and story-point estimates](screenshots/jira\_epic.jpg)



\## 4. Story Evidence Table



I divided my day into five major blocks to make the activities easier to organize.



| Issue Key | Work Type | Summary | Story Points |

|---|---|---|---:|

| SEIR-2 | Story | Morning routine and daily preparation | 2 |

| SEIR-3 | Story | Cloud infrastructure and engineering work | 5 |

| SEIR-4 | Story | Meals, breaks, and personal responsibilities | 3 |

| SEIR-5 | Story | Technical projects and professional development | 5 |

| SEIR-6 | Story | Evening routine and preparation for sleep | 2 |

| \*\*Total\*\* | | \*\*5 Stories\*\* | \*\*17\*\* |



Each story contains a description explaining what I do during that part of my day, approximately how long the activities take, and what needs to be completed.



I also made sure every story has SEIR-1 as its Parent and a story-point estimate.



\### Story Example — SEIR-2



For my morning routine, I assigned \*\*2 story points\*\* because the activities are straightforward and don't involve much uncertainty.



Things like getting ready, preparing breakfast, and checking my schedule still require time and effort, but they aren't as complex as troubleshooting cloud infrastructure.



\### Evidence — Story Details



!\[Story showing description, Parent, and story-point estimate](screenshots/jira\_story.jpg)



\## 5. Task Evidence Table



After creating my stories, I broke the activities down further into 20 individual tasks.



I included routine activities such as brushing my teeth, eating meals, taking a walk, and preparing for bed, along with more technical responsibilities involving AWS, Terraform, CloudWatch, security, and automation.



| Issue Key | Work Type | Summary | Story Points |

|---|---|---|---:|

| SEIR-7 | Task | \[Morning] Wake up and check my schedule | 1 |

| SEIR-8 | Task | \[Morning] Brush teeth and complete personal hygiene | 1 |

| SEIR-9 | Task | \[Morning] Prepare and eat breakfast | 2 |

| SEIR-10 | Task | \[Morning] Review emails and work notifications | 1 |

| SEIR-11 | Task | \[Work] Review AWS infrastructure and cloud resources | 2 |

| SEIR-12 | Task | \[Work] Review CloudWatch logs and investigate infrastructure alerts | 3 |

| SEIR-13 | Task | \[Work] Develop and maintain cloud infrastructure using Terraform | 5 |

| SEIR-14 | Task | \[Work] Troubleshoot AWS networking and security configurations | 5 |

| SEIR-15 | Task | \[Work] Review code, commit changes, and update GitHub documentation | 5 |

| SEIR-16 | Task | \[Meals] Take a break and prepare lunch | 2 |

| SEIR-17 | Task | \[Break] Take a walk and step away from my workstation | 1 |

| SEIR-18 | Task | \[Personal] Complete errands and household responsibilities | 2 |

| SEIR-19 | Task | \[Development] Review technical documentation and cloud architecture | 3 |

| SEIR-20 | Task | \[Development] Build and test cloud automation scripts | 5 |

| SEIR-21 | Task | \[Development] Review cloud security and IAM configurations | 3 |

| SEIR-22 | Task | \[Development] Check messages and coordinate project updates | 2 |

| SEIR-23 | Task | \[Evening] Prepare and eat dinner | 2 |

| SEIR-24 | Task | \[Evening] Review daily accomplishments and plan tomorrow's priorities | 2 |

| SEIR-25 | Task | \[Evening] Organize workspace and complete evening hygiene | 1 |

| SEIR-26 | Task | \[Evening] Wind down and go to sleep | 1 |

| \*\*Total\*\* | | \*\*20 Tasks\*\* | \*\*49\*\* |



All 20 tasks have SEIR-1 as their Parent.



I also gave each task a description explaining when and where it takes place, the approximate duration, what the activity involves, and what completion looks like.



I created these as regular Jira Tasks rather than Subtasks because the assignment required every Task to have the Epic as its Parent.



\### Task Example — SEIR-7



For waking up and checking my schedule, I assigned \*\*1 story point\*\* because it's a routine activity that doesn't require much effort or planning.



Even though it's a simple task, I included it because the assignment was meant to capture an entire day, including activities that I normally wouldn't think about tracking.



\### Evidence — Task Details



!\[Task showing description, Parent, and story-point estimate](screenshots/jira\_task.jpg)



\## 6. Story-Point Summary



| Work Type | Number of Items | Total Story Points |

|---|---:|---:|

| Epic | 1 | Not estimated |

| Stories | 5 | 17 |

| Tasks | 20 | 49 |

| \*\*Total\*\* | \*\*26\*\* | \*\*66\*\* |



My combined estimate is \*\*66 story points\*\*, based on the estimates recorded in the tables above.



The Epic itself has no story points.



I estimated stories and tasks separately as required by the assignment. Since the stories represent broader blocks of activities also described by the tasks, this combined total counts both levels rather than representing a deduplicated sprint workload.



\## 7. Biggest Task and Estimation Reasoning



One of my biggest tasks is \*\*SEIR-13 — Develop and maintain cloud infrastructure using Terraform\*\*, which I assigned \*\*5 story points\*\*.



I gave it that estimate because Terraform work involves more than just writing configurations. I also have to consider resource dependencies, validate my changes, troubleshoot errors, and make sure everything works as intended before applying approved changes.



Compared to something routine like checking emails or preparing a meal, there's more complexity and uncertainty involved, which is why I gave it a higher estimate.



\## 8. Backlog and Work Organization



I used Jira's List view to review the work items I created and check that they were organized under the correct Epic.



After expanding SEIR-1, I could see the stories and tasks with their corresponding story-point estimates.



This helped me verify that the work items were structured correctly and that I hadn't accidentally created Subtasks instead of regular Tasks.



\### Evidence — Jira List View



!\[Jira List view showing Epic, Stories, Tasks, and estimates](screenshots/jira\_backlog.jpg)



\## 9. Lessons Learned



One thing I learned from this assignment is that Agile isn't just about creating tasks and moving them across a board.



It's also about understanding the work that needs to be done, estimating its complexity, and establishing clear expectations for what completion looks like.



I can see how this applies to cloud engineering, especially when dealing with infrastructure changes, automation, security reviews, and troubleshooting.



Breaking down my day into individual tasks also made me realize how much work goes into activities that I normally wouldn't think about tracking.



Another important lesson was understanding that story points aren't necessarily related to how long something takes. Two activities might take the same amount of time but have completely different levels of complexity and uncertainty.



I also gained practical experience working with Jira's Scrum features, setting up story-point estimation, creating parent-child relationships, and organizing work into Epics, Stories, and Tasks.



\## 10. Evidence Files



All mandatory screenshots are stored in the `screenshots/` directory.



| Screenshot | Evidence |

|---|---|

| \[jira\_estimation\_on.jpg](screenshots/jira\_estimation\_on.jpg) | Estimation ON with Story points selected |

| \[jira\_epic.jpg](screenshots/jira\_epic.jpg) | Epic and child work items with estimates |

| \[jira\_story.jpg](screenshots/jira\_story.jpg) | Story with Parent, description, and points |

| \[jira\_task.jpg](screenshots/jira\_task.jpg) | Task with Parent, description, and points |

| \[jira\_backlog.jpg](screenshots/jira\_backlog.jpg) | List view showing Stories, Tasks, and estimates |



\## 11. Assignment Status



I completed the required reading from \*Head First Agile\*, Chapters 1–3, before building my Jira space.



For the practical assignment, I created a team-managed Scrum space, enabled story-point estimation, and organized a full day into one Epic, five Stories, and 20 Tasks.



I added descriptions and estimates to every Story and Task, assigned them to the correct Parent, and captured the five required screenshots as evidence.



The BAM extra-credit exercises are documented separately in `lesson3\_notes.md` as they are completed.



\---



\*\*SEIR Foundations — Module 1, Lesson 3\*\*  

\*\*Jira, Scrum, Agile Estimation, and Work Management\*\*

