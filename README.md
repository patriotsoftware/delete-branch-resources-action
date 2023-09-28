# delete-branch-resources-action

Action intended to be called from delete branch cleanup.


## Parameters

#### 'branch-name' required)
Branch name github.event.ref.

#### 'namespace' required)
Namespace used by the repo and required for the helm uninstall command.

#### 'release-names-array' required)
Array containing release names in this format with quotation marks, space delimited.

#### 'aws-access-key-id' (required)
The AWS access key id, should always be for dev.

#### 'aws-secret-access-key' (required)
The AWS secret access key, should always be for dev.


## Sample Use

```
delete_branch_resources:
  name: "Helm Cleanup"
  runs-on: psidev-linux
  if: github.event.ref != 'refs/heads/main' && github.event.ref != 'refs/heads/master' && github.event.ref != '_InitialSolutionRename'
  runs-on: psidev-linux
  steps:
  - uses: patriotsoftware/delete-branch-resources-action@v1
    with:
      branch-name: github.event.ref
      namespace: payrollcore
      release-names-array: ("notifier-consumer" "payroll-consumer" "payrollcore")
      aws-access-key-id: ${{ secrets.DEV_AWS_ACCESS_KEY_ID }}
      aws-secret-access-key: ${{ secrets.DEV_AWS_SECRET_ACCESS_KEY }}        
```
