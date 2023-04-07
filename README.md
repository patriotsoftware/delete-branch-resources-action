# project-validation-action

This action is intended to share a common set of steps we use to
validate the quality of a project.

- Checkout the code
- Start Sonar
- Run the tests
- Stop Sonar and publish it's results
- Publish test results

## Parameters

#### 'sonar-project-name' (required)
The name of the Sonar project so we can publish
the results to the right place.

#### 'sonar-tool-version' (optional)
The Sonar tool version we install for this run. Default 
is 5.8.0 but this param will allow one to override if
needed.

#### 'use-dependencies' (optional)
Tests can be ran with dependencies if needed. Dependencies
can be defined in a docker compose file. And this switch
can turn on the behavior to ensure the dependencies are 
started. This is off by default.

#### 'docker-compose-file-path' (optional)
This parameter tells the action where to find the 
Docker compose file that defines the dependencies
needed. Default is 'docker-compose/test-dependencies-compose.yml'
