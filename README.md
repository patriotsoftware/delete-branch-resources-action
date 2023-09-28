# helm-cleanup-action

Action intended to be called from cleanup bad deploys to do a helm-uninstall.


## Parameters

#### 'helm-namespace' required)
Namespace used by the repo and required for the helm uninstall command.

#### 'aws-access-key-id' (required)
The AWS access key id, should always be for dev.

#### 'aws-secret-access-key' (required)
The AWS secret access key, should always be for dev.


## Sample Use

```
helm-cleanup:
  name: "Helm Cleanup"
  runs-on: psidev-linux
  steps:
  - uses: patriotsoftware/helm-cleanup-action
    with:
      aws-access-key-id: ${{ secrets.DEV_AWS_ACCESS_KEY_ID }}
      aws-secret-access-key: ${{ secrets.DEV_AWS_SECRET_ACCESS_KEY }}
      sonar-project-name: payrollcorepayschedulesapi
```
