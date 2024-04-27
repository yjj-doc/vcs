# Github Actions
: 프로젝트 코드를 빌드, 테스트, 배포 등을 자동화하는 깃허브 도구  
: 깃허브 리포지토리에 이벤트가 발생하면 자동으로 작업 실행  

- [Workflow](#workflow)
- [Action](#action)


**구조**
```
project (repository)
- .github/
  - action/
  - workflow/ 
  - ISSUE_TEMPLATE/
  - PULL_REQUEST_TEMPLATE/
  - SECURITY/
  - CODEOWNERS
  - dependabot.yml
```



## Workflow
: 실행 규칙, 동작 등의 프로세스가 정의된 파일  

**repo/.github/workflow/my-workflow.yaml**
```yaml
name: 워크플로우 이름 등록
run-name: 워크플로우 실행 이름 등록

# 어떤 이벤트에 반응하는지 등록  
on: 

# workflow에서 실행할 job 등록
jobs: 
  my-job: 
    runs-on: job이 실행될 runner 등록

    # job에서 실행될 흐름 등록 
    steps:
      - name: step 이름 등록
        run: runner에서 실행할 명령어 등록
        env: # 환경 변수 등록 
        uses: 사용할 액션 등록 
        with: # 액션에 전달할 값 등록 
```

**문법**
https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions


**on**
```yaml 
# 단일 이벤트
on: push 

# 다중 이벤트
on: [push, fork]

# 이벤트 + 필터
on:
  push:
    branches:
      - main
    tags:  
      - v1.*
```

**이벤트**  
https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows


**runner**  
: 실행될 환경으로 깃허브에서 제공하거나 직접 등록 가능

- github-hosted runner
- self-hosted runner



## Action 
: 빌드, 테스트, 배포, 알림 등 반복적인 작업 정의  

- Built-in Action 
- Custom Action 



### Built-in Action 

github action  
https://github.com/actions

marketplace action  
https://github.com/marketplace?type=actions  


**checkout**  
: 리포지토리의 소스 코드를 가져오는 액션



### Custom Action 

- container action
- javascript action 
- composite action


**repo/action.yaml**
```yaml
name: 액션 이름 등록
description: 액션 설명 등록

inputs:
  test-input:
    description: 
    required: true
    default: value

outputs:
  test-output:
    description: 

# 자바스크립트 액션 등록
runs: 
  using: 'node20'
  main: 'actions/my-action.js'

# 컨테이너 액션 등록 
runs: 
  using: 'docker'
  image: 'Dockerfile'
  args:
    - ${{ inputs.test-input }}
```


**문법**  
https://docs.github.com/en/actions/creating-actions/metadata-syntax-for-github-actions



#### JS Action 

```bash 
# 필요한 도구 설치
# https://github.com/actions/toolkit 
npm init -y
npm install @actions/core @actions/github
```

```js
import * as core from '@actions/core';
import * as github from '@actions/github';

async function run() {
  ...
}

run();
```