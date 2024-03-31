
---
### Task7:
---
A new DevOps Engineer has joined the team and he will be assigned some Jenkins related tasks. Before that, the team wanted to test a simple parameterized job to understand basic functionality of parameterized builds. He is given a simple parameterized job to build in Jenkins. Please find more details below:
1. Create a `parameterized` job which should be named as `parameterized-job`  
2. Add a `string` parameter named `Stage`; its default value should be `Build`.  
3. Add a `choice` parameter named `env`; its choices should be `Development`, `Staging` and `Production`.  
4. Configure job to execute a shell command, which should echo both parameter values (you are passing in the job).  
5. Build the Jenkins job at least once with choice parameter value `Production` to make sure it passes.

---
### Answer:
---
### Steps:
-  Create job named `parameterized-job`.
-  [x] This job is parameterized.
-  Add require String & choice fields.
-  Add shell script `echo $Stage $env`.

### Pipeline script:
`pipeline {

    agent any

    parameters {

        string(name: 'Stage', defaultValue: 'Build', description: '')

        choice(name: 'env', choices: ['Development', 'Staging', 'Production'], description: '')

    }

    stages {

        stage('Build') {

            steps {

                sh "echo ${params.Stage} - ${params.env}"

            }

        }

    }

 }`
