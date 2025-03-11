Concepts of Github Actions:

Basic building blocks of GHA

1. Workflows:
    -   defined at the repository level
    -   defines which events triggers the workflow
    -   contains multiple jobs
2. Jobs
    -   defined at the workflow level
    -   define in which execution environment they run
    -   composed of one or more steps
    -   run in parallel by default
3. Steps
    -   defined at the job level
    -   define the actual script that GHA executes
    -   runs sequentially bu default