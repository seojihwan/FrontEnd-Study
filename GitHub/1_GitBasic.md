# Git 기본 사용법
Git을 통해 로컬 저장소의 파일들을 원격 서버에 업로드 할 수 있다. 이러한 과정의 순서는 다음과 같다.
> 작업 폴더 --> Index(준비 영역, Staging Area) --> HEAD(최종 확정본)
>
add를 통해 Index에 파일을 추가하고, commit을 통해 확정을 내린다.
### 1.로컬 저장소
#### (1)새로운 로컬 저장소 만들기
```
git init
```
새로운 폴더를 만들고 해당 위치에서 git init을 실행하면 새로운 git 저장소가 만들어진다.

#### (2)기존 로컬 저장소 받아오기
```
git clone <로컬 저장소 경로>
```
다른 위치에 존재하는 로컬 저장소를 받아오기 위해 git clone을 사용한다.
#### (3)기존 원격 저장소 받아오기
```
git clone <원격 저장소 경로>
```
원격 서버에 존재하는 저장소를 받아오기 위해 git clone을 사용한다.
#### (4)원격 저장소를 가져와서 로컬 저장소와 병합
```
git pull 
```
git pull은 fetch와 merge를 한 번에 한다. fetch 과정을 통해 원격 저장소의 master 가지를 가져온다. merge 과정을 통해 로컬 저장소의 master 가지와 병합된다.
### 2.로컬 저장소에서 원격 저장소
**1. add를 통해 작업 폴더에서 Index에 파일 추가**
```
git add <파일 이름>
git add *
```
**2. commit을 통해 Index의 파일을 HEAD에 추가**
```
git commit -m "commit msg"
```
**3. push를 통해 원격 저장소에 업로드**
```
git push origin master 
```
만약 기존 원격 저장소를 가져온 것이 아니라면
```
git remote add origin <원격 저장소 주소>
```

### 3.Branch(가지) 사용하기
가지는 격리된 환경속에서 안전하게 작업하기 위해 필요하다. 
#### (1)가지 생성하기
```
git checkout -b <가지 이름>
```
#### (2)가지 삭제하기
```
git checkout -d <가지 이름>
```
#### (3)master 가지로 돌아가기
```
git checkout master
```
#### (4)가지에서 push하기
```
git push origin <가지 이름>
```
#### (5)가지 비교하기
```
git diff <원래 가지> <비교할 가지>
```
#### (6)가지 병합하기
```
git merge <병합할 가지 이름>
```

