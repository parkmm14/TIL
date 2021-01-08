## git  사용법 한 눈에 정리





### > 새로운 Git 저장소(repository) 생성

#### 1) git init

​	`git init` : 현재 디렉토리를 기준으로 Git 저장소가 생성됨. 

						- .git 디렉토리 생성 . Git이 버전 관리를 하기 위한 메타 정보가 담겨 있음.
						- .git 디렉토리 지우면 해당 Git 저장소의 모든 변경 이력 소실되고 일반 디렉토리로 돌아옴.
						-  생성한 Git 저장소를 혼자서 로컬에서만 사용할 경우 원격 저장소와 연결하는 `git remote` 명령은 사용 x 



### > .gitignore 생성

- `.gitignore`파일은 Git으로 버전 관리를 하면 안 되거나, 할 필요가 없는 경로를 정의하는데 쓰임.
  -  Ex) `.env` 파일은 많은 자바스크립트 프로젝트에서 개발자들이 로컬 컴퓨터에 임의의 환경 변수를 설정하기 위한 용도로 사용함. 따라서 이 파일은 `.gitignore` 파일에 등록을 해야 보안적으로 안전, 불필요한 코드 충돌 피함.



### > 원격 저장소(Remote Repository) 연결

#### 1) git remote

`git remote -v` : 현재 연결되어 있는 원격 레파지토리 확인

`git remote remove <remote repo name>` : 해당 원격 저장소의 연결 제거

`git remote add <remote repo name> <repo url>` 해당 원격 저장소와 연결

`git remote show 이름 ` : 특정 원격 저장소의 정보 확인



#### 2) git push

`git push [remote repo name(별명)] [branch name]`  : 로컬 저장소에 commit한 파일들을 원격 저장소에 추가

​	ex) git push origin master - 파라미터가 없으면 origin 저장소에 푸쉬

#### 3) git pull

`git pull[remote repo name(별명)] [branch name]` : 해당 원격 저장소의 내용을 해당 브랜치로 업데이트





### > Remote Repository, 원격 저장소 다른 사용자 초대하기

​	- "Settings" 탭 클릭 > Manage access > "invite a collaborator" 클릭

	- 초대받은 사용자 또한 위의 명령어를 통해 저장소를 연결.

#### 1) git clone

`git clone [remote repo addr]`

#### 2) git pull

`gitt pull [remote repo name] [branch name]` 

 - ex) git pull origin master

    - git fetch에서 하는 원격저장소의 변경 사항을 가져와서 지역 브랜치에 합치는 작업을 함.

       -  다른 사람들의 작업 변경 사항을 클라이언트로 내려 받기 한다고 보면 된다.

      

