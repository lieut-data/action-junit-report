<div align="center">
  :octocat:
</div>
<h1 align="center">
  action-junit-report
</h1>

<p align="center">
    ... reports JUnit test results as GitHub pull request check.
</p>

<div align="center">
  <img src=".github/images/action.png"/>
</div>

<div align="center">
  <a href="https://github.com/mikepenz/action-junit-report">
		<img src="https://github.com/mikepenz/action-junit-report/workflows/CI/badge.svg"/>
	</a>
</div>
<br />

-------

## GitHub Action: Process JUnit reports

This action processes JUnit XML test reports on pull requests and shows the result as a PR check with summary and annotations.

Based on action for [Surefire Reports by ScaCap](https://github.com/ScaCap/action-surefire-report)

### Inputs

| **Input**      | **Description**                                                                                                                                                    |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `github_token`    | **Required**. Usually in form of `github_token: ${{ secrets.GITHUB_TOKEN }}`.                                                                                      |
| `report_paths`    | **Required**. [Glob](https://github.com/actions/toolkit/tree/master/packages/glob) expression to junit report paths. The default is `**/junit-reports/TEST-*.xml`. |
| `check_name`      | Optional. Check name to use when creating a check run. The default is `Test Report`.                                                                               |
| `commit`          | Optional. The commit SHA to update the status. This is useful when you run it with `workflow_run`.                                                                 |
| `fail_on_failure` | Optional. Fail the build in case of a test failure.                                                                 |

### Example usage

```yml
name: build
on:
  pull_request:

jobs:
  build:
    name: Build and Run Tests
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v1
      - name: Build and Run Tests
        run: # execute your tests generating test results
      - name: Publish Test Report
        uses: mikepenz/action-junit-report@v1
        with:
          report_paths: '**/build/test-results/test/TEST-*.xml'
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

## Sample

<div align="center">
  <img src=".github/images/annotated.png"/>
</div>

<div align="center">
  <img src=".github/images/annotations.png"/>
</div>

## Contribute

```bash
# Install the dependencies  
$ npm install

# Build the typescript and package it for distribution
$ npm run build && npm run package

# Run the tests, use to debug, and test it out
$ npm test

# Verify lint is happy
$ npm run lint -- --fix
```

### Attribution

Original idea and GitHub Actions by: https://github.com/ScaCap/action-surefire-report


## License

    Copyright (C) 2021 Mike Penz

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
