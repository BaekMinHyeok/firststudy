git-flow 강의

Main Branch - Mastrer 브랜치, 제품의 안정된 상태를 유지하기 위한 메인 브랜치 입니다.
배포 가능한 상태의 코드만을 관리하며, 마스터 브랜치에서는 직접적인 작업을 하지 않습니다.

Develop Branch - 개발의 기준이 되는 브랜치, 새로운 기능이나 버그 수정 등의 개발작업(Master 복사본)

Feature Branch - 각자 자기 Feature Branch에 작업, 새로운 기능을 개발하는데 사용
Develop브랜치에서 분기하여 개발하고, 완료된 기능은 Devleop 브랜치로 다시 merge

Release Branch - qa: 테스트 , 추가 수정이나 버그등을 작업, 새로운 버전을 준비하기 위한 브랜치,
완료된 기능들을 모아서 테스트 및 버그수정, 안정화된 상태가 되면 Main 브랜치와 Develop 브랜치로 merge

Hotfix Branch - 배포된 제품에서 발생한 신속한 버그 수정을 위한 브랜치 입니다. Master 브랜치에서 분기하여 버그를 수정하고, 수정된 내용은 Master 브랜치와 Develop 브랜치로 merge 됩니다.

-----------------------------------------------------

깃 메모

버전관리시스템이라 불리는 도구
버전: 프로그램을 수정, 개선할 때의 변화, 코드가 변경 되었을때 

버전관리의 어려움을 효과적으로 해결해준 시스템


working directory: 내가 코드를 작성하는 공간
staging Area: 버전이 될 코드가 존재하는 공간
repository: 버전이 저장되어 있는 공간

git add . : staging Area로 옮겨진다

git commit -m "" : repository로 옮겨진다


git flow
표준 형식
master 에서 Develop 나누고 거기서 프론트 백 나누고 , 프론트와 백에서 다시 feature branch 나누고
develop Branch


develop branch에서 feature branch merge를 하면 코드리뷰 가능

source branch (feature branch 라고 생각)

target branch(합쳐질 대상)

New merge request
Title = 머지 내용타이틀
Description
write =  코드 추가 수정 내용

Assignee 보는 사람
Reviewer 리뷰하는 사람


합침을 당하는  대상 빨간 
합쳐질 코드는 초록

request 후 merge

merge를 하면 develop branch만 남고 합침 당하는 feature branch는 기본값으로 삭제
보통 머지 후 브랜치 삭제

##Commit 컨벤션 
type(옵션): Subject // -> 제목

깃충동 상황
같은 파일에서 원격 저장소에서 내용변경, 로컬에서 내용변경
vscode에서 원하는 코드만 남기고 다 지우면 병합 편집기가 나오고 병합완료
소스제어에서 게시가 뜨면 다시 git commit -m "메세지"를 해서 진행
git branch -D [브랜치] : 머지되지않은 브랜치 강제 삭제

꼭 pull먼저 받고 병합해야 충돌을 방지 할 수 있다.

라벨 만들기 Issues - Labels
라벨은 이슈를 꾸며주는 역할을 하는 도구

마일스톤 만들기 Milestones 
일정체크

이슈 만들기
모든 일정과 담당자 등을 설정

Wiki 작성