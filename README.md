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

Functions :
1. General Functions : fromJSON(), toJSON(), contains(), endsWith(), format()
2. Status Check Functions : success(), failure(), always(), cancelled()

Conditional Execution:
Downstream jobs and steps can be executed even if the upstream ones fail.

continue-on-error: true

Outputs: data from jobs for later usage.
    1. Define id for steps
    2. echo key value pairs to the $GITHUB_OUTPUT variable
    3. Mention outputs in the output sections of the job <steps.stepName.outputs.key>
    4. List the jobs as dependency of jobs that need the output
    5. Accept the output via the needs context

Artifacts : shares the data between jobs and store data after workflows have completed
By default stores for 90 days.
actions: upload-artifact, download-artifact ## can be used within the same workflow

cache are used to store for 7 days.
Managed via single action and recommended when the files are to use within the same workflow.

Matrices : runs several variations of the same job

Usecases : run test suits in parallel in multiple nodes versions before publishing an npm package

include and exclude options !!

GitHub Actions allows you to use the concurrency configuration to ensure that only a single job or workflow using the same concurrency group will run at a time:

concurrency:
  group: ${{ github.workflow }}-${{ github.ref }}
  cancel-in-progress: true

Job-Level Concurrency
For more granular control, define concurrency at the job level:

jobs:
  build:
    concurrency:
      group: build-${{ github.ref }}
      cancel-in-progress: false
  deploy:
    concurrency:
      group: deploy-${{ github.ref }}
      cancel-in-progress: true

Custom Actions :
1. Composite Actions
2. Javascript Actions
3. Docker Actions