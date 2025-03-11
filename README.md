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

Workflow Runners : Virtual Servers that executes jobs from workflows.

1. Github Standard Runners: Windows, Ubuntu and Mac
    -   Managed service
    -   VM is scoped to a job. Steps in the job shares the VM
2.  Self Hosted Runners:
    -   any infrastructure of your choice
    -   full control over the VM
    -   Can be added at the repository level, org level

Do not use self hosted runners in the public repository.

RUNNER OS : $RUNNER_OS

Actions : custom applications to perform complex, frequently repeated tasks.
with:   configuration can be done by with which is a key-value pair.

Workflow Contexts : Access information about the runs,variables,jobs

Environment Variable is overwritten in the order : steps, job, workflow

env.variableName : defines at the workflow, jobs and steps level
vars.variableName : defines at the organization, repository and environment level

ORGANISATION VARIABLE/SECRETS
REPOSITORY VARIABLE/SECRETS

environment : key used to pull the variables from environment

while giving inputs if we are planning to take environments in the repo, type should be as environment