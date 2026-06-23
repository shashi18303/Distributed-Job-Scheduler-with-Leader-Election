System Architecture
                Client/Admin
                      |
                      |
               REST APIs
                      |
      --------------------------------
      |              |              |
      |              |              |
    Node1          Node2          Node3
 (Leader)       (Follower)      (Follower)
      |              |              |
      --------------------------------
                      |
                PostgreSQL
                      |
                 Job Tables          







                 . Project Folder Structure
src
 ├── controller
 │      └── JobController
 │
 ├── service
 │      ├── JobService
 │      ├── SchedulerService
 │      └── LeaderElectionService
 │
 ├── repository
 │      ├── JobRepository
 │      └── NodeRepository
 │
 ├── entity
 │      ├── Job
 │      ├── Node
 │      └── JobExecution
 │
 ├── scheduler
 │      └── JobExecutor
 │
 └── config
        └── SchedulerConfig









        . Docker Architecture
Docker Image
       |
Docker Container
       |
Spring Boot Application
       |
PostgreSQL








End-to-End Flow
Admin creates Job
          |
          v
Job saved in PostgreSQL
          |
          v
Leader checks pending jobs
          |
          v
Leader executes job
          |
          v
Execution details stored
          |
          v
Leader crashes
          |
          v
Follower becomes Leader
          |
          v
Jobs continue running
