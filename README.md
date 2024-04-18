# delete-branch-resources-action

Action intended to be called from delete branch cleanup.


## Parameters

#### 'branch-name' required)
Branch name github.event.ref.

#### 'namespace' required)
Namespace used by the repo and required for the helm uninstall command.

#### 'release-names-array' required)
Array containing release names in this format with quotation marks, space delimited.

#### 'delete-branch-db'
Optional parameter to also delete the associated branch database.

#### 'aws-access-key-id' (required)
The AWS access key id, should always be for dev.

#### 'aws-secret-access-key' (required)
The AWS secret access key, should always be for dev.


## Sample Use

from GitHub delete branch action
```
  - uses: patriotsoftware/delete-branch-resources-action@v1
    with:
      branch-name: ${{ github.event.ref }}
      namespace: payrollcore
      delete-branch-db: true
      release-names-array: ("notifier-consumer" "payroll-consumer" "payrollcore")
      aws-access-key-id: ${{ secrets.DEV_AWS_ACCESS_KEY_ID }}
      aws-secret-access-key: ${{ secrets.DEV_AWS_SECRET_ACCESS_KEY }}         
```

from list expired branches action
```
  - uses: patriotsoftware/delete-branch-resources-action@v1
    with:
      branch-name: ${{ matrix.branch_name }}
      namespace: payrollcore
      release-names-array: ("notifier-consumer" "payroll-consumer" "payrollcore")
      delete-branch-db: true
      aws-access-key-id: ${{ secrets.DEV_AWS_ACCESS_KEY_ID }}
      aws-secret-access-key: ${{ secrets.DEV_AWS_SECRET_ACCESS_KEY }}  
```