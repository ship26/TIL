# Github 특강 2일차

> 2022-03-29 진행된 GIT허브 특강입니다.



**질문에 대한 답변**

GitHub는 BIOB로 변환하여 파일을 저장하고 표현은 .txt , .script와 같이 표현을 합니다. 다른 버전이라도 내용이 같으면 같은 BIOB파일을 공유하며 다른 내용일 경우 새로운 BIOB를 생성합니다.

이렇게 함으로써 용량을 줄일 수 있습니다.



---



### .gitignore

프로젝트를 할 시 .gitignore 파일을 만드는 습관을 들이면 좋다.

마크다운에서 .gitignore을 알아서 인식한다. git에서는 gitignore에 적힌 파일들은 working area 에서 stage로 넘어가지 않는다 .

*한 번 git add에 들어간 파일들은 .gitignore로 무시 할 수 없다.*

**gitignore.io**

gitignore에 들어가야할 파일들을 운영체제, 언어 등의 환경을 입력하면 자동으로 작성해주는 사이트이다.

[gitignore.io](https://www.toptal.com/developers/gitignore)

- gitignore에 작성하는 목록

민감한 개인정보,os에활용되는파일 , ide에활용되는파일 등등..



- gitignore 작성시 주의사항

반드시 이름을 .gitignore로한다.

.gitignore 파일은 .git폴더와 동일한 위치에 생성한다.

**제외하고싶은 파일은 반드시 git add전에 .gitignore에 작성한다**



- gitignore 패턴 규칙

1. 아무것도 없는 라인이나 #로시작하는 라인은 무시한다.

2. '/'로 시작하면 하위 디렉터리에 재귀적으로 적용되지 않는다.

3. 디렉터리는 '/'를 끝에 사용하는 것으로 표현한다

4. '!'로 시작하는 패턴의 파일은 무시하지 않는다

5. 표준 Glob 패턴을 사용한다.
   - *는 문자가 하나도없거나 하나 이상을 의미
   - [abc]는 중괄호 안에 있는 문자중하나를 의미
   - ?는 문자하나를 의미
   - [0-9]처럼 중괄호 안에 하이폰의경우 0과 9사이의 문자중 하나를 의미
   - **는 디렉터리 내부의 디렉터리까지 지정할 수 있다 a/(애스터리스크2개)/z 라면 a/z ,a/b/z,a/b/c/z 까지 모두 영향을 끼친다.

---

### 원격저장소 내용 가져오기



**git clone**

원격 저장소의 커밋 내역을 모두 가져와서 로컬 자정소를 생성하는 명령어

원격 저장소를 통째로 복제해서 내 컴퓨터에 옮길 수 있음

`git clone <url>` 의 형태로 작성합니다

`git init`과 `git remote add`가 포함됩니다.

**git pull**

원격 저장소의 변경사항을 가져와서 로컬 저장소를 업데이트합니다

`git pull <저장소이름> <브랜치이름>`

*git clone vs git pull*

> git clone 은 git init 처럼 처음에 한번만 실행한다
>
> 로컬 저장소를 만드는 역할이다.
>
> 단, git init처럼 직접 로컬저장소를 만드는게 아니라 github에서 저장소를 복제해서 내컴퓨터에 똑같은 복제본을 만든다.

> git pull 은 git push 처럼 로컬저장소와 원격 저장소의 내용을 동기화 하고싶다면 언제든 사용
>
> 

**git 을 push나 pull을 할 때 같은 파일의 같은 라인에 서로 다른 내용이 작성 될 경우 충돌(conflict)가 난다 그 경우 사람이 어느 한 버전을 선택 해 줘야 한다**

---



### branch

![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd6378065-5864-4832-8122-0fde3eb4f6ec%2FUntitled.png?table=block&id=073a069d-f718-4054-be7e-7e979bfa1cb8&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

- Branch는 `나뭇가지`라는 뜻의 영어 단어입니다.
- 즉 `브랜치`란 나뭇가지처럼 여러 갈래로 작업 공간을 나누어 **독립적으로 작업**할 수 있도록 도와주는 Git의 도구입니다.
- 장점
  1. 브랜치는 독립 공간을 형성하기 때문에 원본(master)에 대해 안전합니다.
  2. 하나의 작업은 하나의 브랜치로 나누어 진행되므로 체계적인 개발이 가능합니다.
  3. 특히나 Git은 브랜치를 만드는 속도가 굉장히 빠르고, 용량도 적게 듭니다.
- 그래도 브랜치 꼭 써야하나요?
  1. 일단 master 브랜치는 상용을 의미합니다. 그래서 언제든 세상에 공개되어 있습니다.
  2. 만약 상용에 에러가 있어서 고쳐야 한다면 어떻게 해야할까요?
  3. 고객들이 사용하고 있는데, 함부로 버전을 되돌리거나 삭제할 수 있을까요?
  4. 따라서 브랜치를 통해 별도의 작업 공간을 만들고, 그곳에서 되돌리거나 삭제를 합니다.
  5. 브랜치는 완전하게 독립이 되어있어서 어떤 작업을 해도 master에는 영향을 끼치지 못하죠.
  6. 그리고 이후에 에러를 해결했다면? 그 내용을 master에 반영할 수도 있습니다!
  7. 이러한 이유 때문에 Git에서 브랜치는 정말 강력한 기능 중의 하나라고 할 수 있습니다.



브랜치 조회, 생성, 삭제 등 브랜치와 관련된 Git 명령어

````Bash
#브랜치 목록 확인
$git branch
#원격 저장소의 브랜치 목록
$git branch -r
#새로운 브랜치 생성
$git branch <브랜치이름>

#특정 커밋 기준으로 브랜치 생성
$git branch <브랜치 이름> <커밋 id>
#특정 브랜치 삭제
$git branch -d <브랜치 이름> # 병합된 브랜치만 삭제 가능
$```bash
# 브랜치 목록 확인
$ git branch

# 원격 저장소의 브랜치 목록 확인
$ git branch -r

# 새로운 브랜치 생성
$ git branch <브랜치 이름>

# 특정 커밋 기준으로 브랜치 생성
$ git branch <브랜치 이름> <커밋 ID>

# 특정 브랜치 삭제
$ git branch -d <브랜치 이름> # 병합된 브랜치만 삭제 가능
$ git branch -D <브랜치 이름> # (주의) 강제 삭제 (병합되지 않은 브랜치도 삭제 가능)
```
````



#### git switch

현재 브랜치에서 다른 브랜치로 HEAD를 이동시키는 명령어 HEAD란 현재 브랜치를 가리키는 포인터를 의미합니다.

``` b

# 다른 브랜치로 이동
$ git switch <다른 브랜치 이름>

# 브랜치를 새로 생성과 동시에 이동
$ git switch -c <브랜치 이름>

# 특정 커밋 기준으로 브랜치 생성과 동시에 이동
$ git switch -c <브랜치 이름> <커밋 ID>



```

**! git switch 하기 전에 브랜치의 변경 사항을 커밋해야 합니다**



---

### Branach -merge

지금까지는 브랜치를 통해서 독립된 작업 공간을 만드는 것 까지 진행했습니다. 이제 각 브랜치에서의 작업이 끝나면 어떻게 할까요?  그 작업 내용을 master에 반영해야 하지 않을까요? 지금부터는 Merge라고 하는 병합을 학습하면서 브랜치를 합치는 것을 살펴보겠습니다.



#### git merge

- 분기된 브랜치들을 하나로 합치는 명령어

- `git merge <합칠 브랜치 이름>`의 형태로 사용합니다.

- **Merge하기 전에 일단 다른 브랜치를 합치려고 하는, 즉 메인 브랜치로 switch 해야합니다.**

  ```bash
  # 1. 현재 branch1과 branch2가 있고, HEAD가 가리키는 곳은 branch1 입니다.
  $ git branch
  * branch1
    branch2
  
  # 2. branch2를 branch1에 합치려면?
  $ git merge branch2
  
  # 3. branch1을 branch2에 합치려면?
  $ git switch branch2
  $ git merge branch1
  ```



### 2) Merge의 세 종류

1. **Fast-Forward**

   - 브랜치를 병합할 때 마치 `빨리감기`처럼 브랜치가 가리키는 커밋을 앞으로 이동시키는 것

   1. 현재 master는 C2 커밋을, hotfix는 C4 커밋을 가리키고 있습니다.

      ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F454c4f14-e3f0-44b7-8395-1bc9d0365dec%2FUntitled.png?table=block&id=5eb24993-bef8-4926-80ab-7719cf90e0ed&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   

   

   1. master에 hotfix를 병합하면 어떻게 될까요?

      ```bash
      $ git switch master
      $ git merge hotfix
      Updating s1d5f1s..1325sd4
      **Fast-forward**
       index.html | 2 ++
       1 file changed, 2 insertions(+)
      ```

   2. hotfix가 가리키는 C4는 C2에 기반한 커밋이므로, master가 C4에 이동하게 됩니다.

      이렇게 따로 merge 과정 없이 브랜치의 포인터가 이동하는 것을 `Fast-Forward`라고 합니다.

      ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8f7f9cc1-e5c6-4bb0-808b-56ab5dd6caff%2FUntitled.png?table=block&id=37e7df04-ee84-4490-908d-e2665644fbf3&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

      

   3. 병합이 완료된 hotfix는 더 이상 필요 없으므로 삭제합니다.

      ```bash
      $ git branch -d hotfix
      Deleted branch hotfix (1325sd4).
      ```

2. **3-Way Merge**

   - 브랜치를 병합할 때 `각 브랜치의 커밋 두개와 공통 조상 하나`를 사용하여 병합하는 것
   - 두 브랜치에서 `다른 파일` 혹은 `같은 파일의 다른 부분`을 수정했을 때 가능합니다.

   1. 현재 master는 C4 커밋을, iss53은 C5 커밋을 가리키고 있습니다.

      master와 iss53의 공통 조상은 C2 커밋입니다.

      

   2. 이 상황에서 master에 iss53을 병합하면 어떻게 될까요?

      ```bash
      $ git switch master
      Switched to branch 'master'
      $ git merge iss53
      **Merge made by the 'ort' strategy.**
      index.html |    1 +
      1 file changed, 1 insertion(+)
      ```

   3. master와 iss53은 갈래가 나누어져 있기 때문에 Fast-Forward로 합쳐질 수 없습니다.

      따라서 공통 조상인 C2와 각자가 가리키는 커밋인 C4, C5를 비교하여 3-way merge를 진행합니다.

      ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa76a9563-95f0-4cc8-abb9-ab2b8366682e%2FUntitled.png?table=block&id=259661f0-dc86-436f-a5fb-2ddb1e7822a6&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

      

      

   4. 이때 생긴 C6는 master와 iss53이 병합되면서 발생한 Merge Commit입니다.

   5. 병합이 완료된 iss53은 더 이상 필요 없으므로 삭제합니다.

      ```bash
      $ git branch -d iss53
      Deleted branch iss53 (58sdf23).
      ```

3. **Merge Conflict**

   - 병합하는 두 브랜치에서 `같은 파일의 같은 부분`을 수정한 경우, Git이 어느 브랜치의 내용으로 작성해야 하는지 판단하지 못해서 발생하는 충돌(Conflict) 현상
   - 결국은 사용자가 직접 내용을 선택해서 Conflict를 해결해야 합니다.

   1. 현재 master는 C4 커밋을, iss53은 C5 커밋을 가리키고 있습니다.

      master와 iss53의 공통 조상은 C2 커밋입니다. `(3-way merge에서 상황과 같습니다)`

      ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F11ffb183-4b65-41c9-8c40-058e681564e6%2FUntitled.png?table=block&id=48c21401-ba33-4216-a3e4-9b855e53b55c&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

      

   2. 3-way merge와는 달리, 만약 master와 iss53이 `같은 파일의 같은 부분`을 수정하고 병합한다면 어떤 일이 발생할까요?

      ```bash
      $ git merge iss53
      Auto-merging index.html
      CONFLICT (content): Merge conflict in index.html
      Automatic merge failed; fix conflicts and then commit the result.
      ```

   3. 충돌이 일어난 파일을 확인하기 위해 `git status`를 입력합니다.

      ```bash
      $ git status
      On branch master
      You have unmerged paths.
        (fix conflicts and run "git commit")
      
      Unmerged paths:
        (use "git add <file>..." to mark resolution)
      
          both modified:      index.html
      
      no changes added to commit (use "git add" and/or "git commit -a")
      ```

   4. `index.html`을 열어보면 아래와 같이 충돌 내역이 나옵니다.

      ```html
      <<<<<<< HEAD:index.html
      <div id="footer">contact : email.support@github.com</div>
      =======
      <div id="footer">
       please contact us at support@github.com
      </div>
      >>>>>>> iss53:index.html
      ```

   5. `=======` 를 기준으로 위는 master의 내용, 아래는 iss53의 내용입니다.

      이 중 하나를 선택할 수도 있고, 둘 다 선택할 수도 있고, 아예 새롭게 작성할 수도 있습니다.

      ```html
      <div id="footer">
      please contact us at email.support@github.com
      </div>
      ```

   6. 이후 git add와 git commit을 통해 병합한 내용을 커밋할 수 있습니다.

      ```bash
      $ git add .
      $ git commit
      ```

   7. Vim 편집기를 이용해서 커밋 내역을 수정할 수 있습니다.

      ```bash
      Merge branch 'iss53'
      
      Conflicts:
          index.html
      #
      # It looks like you may be committing a merge.
      # If this is not correct, please remove the file
      #	.git/MERGE_HEAD
      # and try again.
      
      # Please enter the commit message for your changes. Lines starting
      # with '#' will be ignored, and an empty message aborts the commit.
      # On branch master
      # All conflicts fixed but you are still merging.
      #
      # Changes to be committed:
      #	modified:   index.html
      #
      ```

   8. Vim 편집기를 통해 작성한 커밋이 이제 C6 커밋이 됩니다.![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F586bcfc3-2aeb-4aed-840c-33b24bf19b8b%2FUntitled.png?table=block&id=77067b4b-80bc-4206-bc68-81ab97ef8dc3&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

      

   9. 병합이 완료된 iss53은 더 이상 필요 없으므로 삭제합니다.

      ```bash
      $ git branch -d iss53
      Deleted branch iss53 (58sdf23).
      ```

## [2] Branch-merge Scenario

> 지금까지 학습했던 git merge와 세 가지 상황에 대해 다시 한 번 살펴봅니다.

### (1) 사전 세팅

```bash
$ mkdir git_merge
$ cd git_merge

$ git init
$ touch test.txt

# test.txt 에 master test 1 을 입력 후 저장

$ git add .
$ git commit -m "master test 1"
```

### (2) Fast-Forward



![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb623c2ed-098d-44d7-84c9-a710268d6351%2F111.png?table=block&id=ffc2928b-7218-4171-8d84-39ffb102c1f6&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1060&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)





<aside> 💡 **login 브랜치가 생성된 이후 master 브랜치에 변경 사항이 없는 상황**

즉, master 브랜치에서 login 브랜치를 merge 할 때 login 브랜치가 master 브랜치 이후의 커밋을 가리키고 있으면 그저 master 브랜치가 login 브랜치와 동일한 커밋을 가리키도록 이동 시킬 뿐입니다.

</aside>

1. `login` 브랜치 생성 및 이동합니다.

   ```bash
   $ git switch -c login
   ```

2. `login.txt`를 만들고 커밋합니다.

   ```bash
   $ touch login.txt
   $ git add .
   $ git commit -m "login test 1"
   ```

3. `master` 브랜치로 이동합니다.

   ```bash
   $ git switch master
   
   $ git log --oneline --all --graph
   * df231d0 (login) login test 1
   * 1e62b4c (HEAD -> master) master test 1
   ```

4. `master`에 `login`을 병합합니다.

   ```bash
   $ git merge login
   Updating 1e62b4c..df231d0
   **Fast-forward**
    login.txt | 0
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 login.txt
   ```

5. 결과를 확인합니다. (**Fast-forward**, 단순히 HEAD를 앞으로 빨리감기)

   ```bash
   $ git log --oneline --all --graph
   * df231d0 (HEAD -> master, login) login test 1
   * 1e62b4c master test 1
   ```

6. `login` 브랜치를 삭제합니다.

   ```bash
   $ git branch -d login
   Deleted branch login (was df231d0).
   
   $ git log --oneline --all --graph
   * df231d0 (HEAD -> master) login test 1
   * 1e62b4c master test 1
   ```

### (3) 3-way Merge (Merge commit)

![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F803426c3-d332-4704-8479-2d3a3de6ba47%2F222.png?table=block&id=2f6bf1c6-b919-4acb-a81f-49452d40c768&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)



<aside> 💡 현재 브랜치(master)가 가리키는 커밋이 Merge 할 브랜치의 조상이 아니면, git은 각 브랜치가 가리키는 커밋 2개와 공통 조상 하나를 사용하며 `3-way Merge` 합니다.

단순히 브랜치 포인터를 최신 커밋으로 옮기는 게 아니라 3-way Merge 의 결과를 별도의 커밋으로 만들고 나서 해당 브랜치가 그 커밋을 가리키도록 이동 시킵니다. 그래서 이런 커밋은 부모가 여러 개고 `Merge commit` 이라고 합니다.

</aside>

1. `signout` 브랜치를 생성 및 이동합니다.

   ```bash
   $ git switch -c signout
   ```

2. 특정 작업 완료 후 커밋합니다.

   ```bash
   $ touch signout.txt
   
   $ git add .
   $ git commit -m "signout test 1"
   
   $ git log --oneline
   bcade83 (HEAD -> signout) signout test 1
   df231d0 (master) login test 1
   1e62b4c master test 1
   ```

3. `master` 브랜치로 이동합니다.

   ```bash
   $ git switch master
   ```

4. `master`에 추가 작업 후 커밋합니다. (단 **`signout` 브랜치와 다른 파일**을 생성 혹은 수정합니다.)

   ```bash
   $ touch master.txt
   
   $ git add .
   $ git commit -m "master test 2"
   
   $ git log --all --oneline
   48bd5a6 (HEAD -> master) master test 2
   bcade83 (signout) signout test 1
   df231d0 login test 1
   1e62b4c master test 1
   ```

5. `master`에 `signout`을 병합합니다. (자동 merge commit 발생)

   ```bash
   $ git merge signout
   Merge made by the 'ort' strategy.
    signout.txt | 0
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 signout.txt
   ```

6. log 확인

   ```bash
   $ git log --oneline --all --graph
   *   ac0e971 (HEAD -> master) Merge branch 'signout'
   |\\
   | * bcade83 (signout) signout test 1
   * | 48bd5a6 master test 2
   |/
   * df231d0 login test 1
   * 1e62b4c master test 1
   ```

7. `signout` 브랜치 삭제

   ```bash
   $ git branch -d signout
   Deleted branch signout (was bcade83).
   ```

### (4) Merge Conflict

![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb31206af-b48f-4193-8b5f-f9c068f8c0be%2F.png?table=block&id=3d2331e9-946d-4d69-963e-3d66aaf1e3bd&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)



<aside> 💡 Merge 하는 두 브랜치에서 **같은 파일의 한 부분을 동시에 수정**하고 Merge 하면 Git은 해당 부분을 자동으로 Merge 하지 못하고 충돌이 일어납니다. **(반면 동일 파일이더라도 서로 다른 부분을 수정했다면, Conflict 없이 자동으로 Merge Commit 됩니다!)**

</aside>

1. `hotfix` 브랜치를 생성 및 이동합니다.

   ```bash
   $ git switch -c hotfix
   ```

2. 특정 작업 완료 후 커밋합니다.

   ```bash
   # test.txt 수정
   
   master test 1
   **이건 hotfix에서 작성한 문장입니다.**
   ```

   ```bash
   $ git add .
   $ git commit -m "hotfix test 1"
   
   $ git log --oneline --graph --all
   * ad045fa (HEAD -> hotfix) hotfix test 1
   *   ac0e971 (master) Merge branch 'signout'
   |\\
   | * bcade83 signout test 1
   * | 48bd5a6 master test 2
   |/
   * df231d0 login test 1
   * 1e62b4c master test 1
   ```

3. `master` 브랜치로 이동합니다.

   ```bash
   $ git switch master
   ```

4. 특정 작업(`hotfix` 와 동일 파일의 동일 부분 수정) 완료 후 커밋합니다.

   ```bash
   # text.txt 수정
   
   master test 1
   **이건 master에서 작성한 문장입니다.**
   ```

   ```bash
   $ git add .
   $ git commit -m "master test 3"
   
   $ git log --oneline --all --graph
   * 3170247 (HEAD -> master) master test 3
   | * ad045fa (hotfix) hotfix test 1
   |/
   *   ac0e971 Merge branch 'signout'
   |\\
   | * bcade83 signout test 1
   * | 48bd5a6 master test 2
   |/
   * df231d0 login test 1
   * 1e62b4c master test 1
   ```

5. `master`에 `hotfix`를 병합합니다.

   ```bash
   $ git merge hotfix
   ```

6. 결과 → merge conflict 발생 (**같은 파일의 같은 문장을 수정했기 때문입니다!**)

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F072a8eb0-4fa6-4759-806e-6ae38069eb8e%2FUntitled.png?table=block&id=6ffbe41b-01e2-4733-be5a-197432b9455d&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

7. 충돌 확인 및 해결

   - Merge Conflict가 일어났을 때 Git이 어떤 파일을 Merge 할 수 없었는지 살펴보려면 `git status` 명령을 이용합니다.

   ```bash
   $ git status
   On branch master
   You have unmerged paths.
     (fix conflicts and run "git commit")
     (use "git merge --abort" to abort the merge)
   
   Unmerged paths:
     (use "git add <file>..." to mark resolution)
           both modified:   test.txt
   
   no changes added to commit (use "git add" and/or "git commit -a")
   ```

   ```
   master test 1
   <<<<<<< HEAD
   이건 master에서 작성한 문장입니다.
   =======
   이건 hotfix에서 작성한 문장입니다.
   >>>>>>> hotfix
   ```

   - `=======` 위쪽의 내용은 HEAD 버전(merge 명령을 실행할 때 작업하던 `master` 브랜치)의 내용이고 아래쪽은 `hotfix` 브랜치의 내용입니다. 충돌을 해결하려면 위쪽이나 아래쪽 내용 중에서 고르거나 새로 작성하여 Merge 해야 합니다. (`<<<<<<<, =======, >>>>>>>` 가 포함된 행은 삭제)

   ```bash
   # test.txt 최종본
   
   master test 1
   이건 충돌을 해결한 후의 문장입니다.
   ```

8. merge commit 진행합니다.

   ```bash
   $ git add .
   $ git commit
   ```

   - vim 편집기 등장

     ```bash
     Merge branch 'hotfix'
     
     # Conflicts:
     #       test.txt
     #
     # It looks like you may be committing a merge.
     # If this is not correct, please run
     #       git update-ref -d MERGE_HEAD
     # and try again.
     
     # Please enter the commit message for your changes. Lines starting
     # with '#' will be ignored, and an empty message aborts the commit.
     #
     # On branch master
     # All conflicts fixed but you are still merging.
     #
     ```

   - 작성된 커밋 메세지를 확인하고 `esc` 를 누른후 `:wq` 를 입력하여 저장 & 종료합니다.

     ```bash
     $ git commit
     [master 8ef1443] Merge branch 'hotfix'
     ```

9. log 확인

   ```bash
   $ git log --oneline --all --graph
   *   8ef1443 (HEAD -> master) Merge branch 'hotfix'
   |\\
   | * ad045fa (hotfix) hotfix test 1
   * | 3170247 master test 3
   |/
   *   ac0e971 Merge branch 'signout'
   |\\
   | * bcade83 signout test 1
   * | 48bd5a6 master test 2
   |/
   * df231d0 login test 1
   * 1e62b4c master test 1
   ```

10. `hotfix` 브랜치를 삭제합니다.

---

### Git workflow



------

<aside> 💡 **Branch를 이용해 협업을 하는 두 가지 방법**에 대해 알아봅니다.

1. 원격 저장소 소유권이 있는 경우 (Shared repository model)
2. 원격 저장소 소유권이 없는 경우 (Fork & Pull model)

</aside>

## [1] 원격 저장소 소유권이 있는 경우 (Shared repository model)

### (1) 개념

- 원격 저장소가 자신의 소유이거나 collaborator로 등록되어 있는 경우에 가능합니다.
- master에 직접 개발하는 것이 아니라, `기능별로 브랜치`를 따로 만들어서 개발합니다.
- `Pull Request`를 같이 사용하여 팀원 간 변경 내용에 대한 소통을 진행합니다.

### (2) 작업 흐름

1. 소유권이 있는 원격 저장소를 로컬 저장소로 `clone` 받습니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9d8aab56-c8b0-4d72-9bb9-0cb1789761ae%2FUntitled.png?table=block&id=a5ac392b-068c-480a-992f-afef67193246&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git clone <https://github.com/edukyle/django-project.git>
   ```

2. 사용자는 자신이 작업할 기능에 대한 `브랜치를 생성`하고, 그 안에서 `기능을 구현`합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd6ec3f5c-abb0-44be-b923-c57373606795%2FUntitled.png?table=block&id=8f1f7df1-fb76-4297-921c-330f3c3dba25&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git switch -c feature/login
   ```

3. 기능 구현이 완료되면, 원격 저장소에 해당 브랜치를 `push` 합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F90c5722c-9ac9-4c60-a250-421a313222cb%2FUntitled.png?table=block&id=2ca09ede-b54c-4f69-bed5-2c49454bd1ce&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git push origin feature/login
   ```

4. 원격 저장소에는 master와 각 기능의 브랜치가 반영되었습니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F9c8e693a-241f-41f6-88d4-ef127c7c4b14%2FUntitled.png?table=block&id=b30a1929-eb14-4ee5-854c-19346cb8f998&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

5. Pull Request를 통해 브랜치를 master에 반영해달라는 요청을 보냅니다. (팀원들과 코드 리뷰를 통해 소통할 수 있습니다.)

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F2ced8346-37e0-4291-8811-fe0d2422539d%2FUntitled.png?table=block&id=ba04872e-4ec7-4aa9-97f2-0b923388ad3d&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

6. 병합이 완료되면 원격 저장소에서 병합이 완료된 브랜치는 불필요하므로 삭제합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Feb9c4d7e-ebd9-4016-8306-3882ad791464%2FUntitled.png?table=block&id=0678e8db-9575-4c38-96df-2fea5ce1ad1b&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

7. master에 브랜치가 병합되면, 각 사용자는 로컬의 master 브랜치로 이동합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ff95c707b-3ad3-41c3-beee-00eba8db2789%2FUntitled.png?table=block&id=28f90e8b-9f35-4f61-b75f-d110cb157ecb&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git switch master
   ```

8. 병합으로 인해 변경된 원격 저장소의 master 내용을 로컬에 받아옵니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F139021e6-2d00-4099-8205-2dca5e35f445%2FUntitled.png?table=block&id=72471370-aba7-490d-8ec1-139820d3cb08&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git pull origin master
   ```

9. 병합이 완료된 master의 내용을 받았으므로, 기존 로컬 브랜치는 삭제합니다. (한 사이클 종료)

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fcc543835-9e05-4f4f-a6d5-acc96f6ba91f%2FUntitled.png?table=block&id=d66a8f7b-f621-4faa-a199-8746a272356d&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git branch -d feature/login
   ```

10. 새로운 기능 추가를 위해 새로운 브랜치를 생성하며 위 과정을 반복합니다.

    ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc96da544-1374-4921-b4dc-417a890adcf2%2FUntitled.png?table=block&id=2f860245-4e21-4246-94bf-7d538e976404&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

    

    ```bash
    $ git switch -c feature/pay
    ```

## [2] 원격 저장소 소유권이 없는 경우 (Fork & Pull model)

### (1) 개념

- 오픈 소스 프로젝트와 같이, 자신의 소유가 아닌 원격 저장소인 경우 사용합니다.
- 원본 원격 저장소를 그대로 내 원격 저장소에 `복제`합니다. (이 행위를 `fork`라고 합니다.)
- 기능 완성 후 `Push는 복제한 내 원격 저장소에 진행`합니다.
- 이후 `Pull Request`를 통해 원본 원격 저장소에 반영될 수 있도록 요청합니다.

### (2) 작업 흐름

1. 소유권이 없는 원격 저장소를 `fork`를 통해 내 원격 저장소로 `복제`합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fe1c48127-e989-4fd5-b697-aecf54cd21e0%2FUntitled.png?table=block&id=afabe823-2975-4721-9ce9-b054aa13eaf0&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   아래와 같이 `Fork` 버튼을 누르면 자동으로 내 원격 저장소에 복제됩니다.

   ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c3c3ff28-9a8d-4429-ad78-740a059e6457/Untitled.png)

2. `fork` 후, 복제된 내 원격 저장소를 로컬 저장소에 `clone` 받습니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fe8628903-8781-41fe-a034-6e9746eb5407%2FUntitled.png?table=block&id=198ca684-74c2-4799-9b9a-edbf60dbd52c&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git clone <https://github.com/edukyle/kakao_clone.git>
   ```

3. 이후에 로컬 저장소와 원본 원격 저장소를 동기화 하기 위해서 연결합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0bbcb751-e5c2-49b6-8eb5-f6bc71c39aa8%2FUntitled.png?table=block&id=b8aa2179-2cfb-48ad-a01f-38764b7f1e40&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   # 원본 원격 저장소에 대한 이름은 upstream으로 붙이는 것이 일종의 관례
   
   $ git remote add upstream <https://github.com/AlexKwonPro/kakao_clone.git>
   ```

4. 사용자는 자신이 작업할 기능에 대한 `브랜치를 생성`하고, 그 안에서 `기능을 구현`합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0d535639-8145-430c-aebd-eee2fb8d5bbb%2FUntitled.png?table=block&id=702c531b-7843-4fdc-a38b-6ad8ccfa169e&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git switch -c feature/login
   ```

5. 기능 구현이 완료되면, `복제 원격 저장소(origin)`에 해당 브랜치를 `push` 합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0cc34aa6-0689-47c6-a71a-0f36de47eb28%2FUntitled.png?table=block&id=120ead06-f22d-40a6-8ef8-0837e242644a&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git push origin feature/login
   ```

6. `복제 원격 저장소(origin)`에는 master와 브랜치가 반영되었습니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fed7ed6b1-894c-4c40-862d-c84eb2431112%2FUntitled.png?table=block&id=aa9f0064-db45-4b75-a5d6-ca8add17d4b5&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

7. `Pull Request`를 통해 `복제 원격 저장소(origin)의 브랜치`를 `원본 원격 저장소(upstream)의 master`에 반영해달라는 요청을 보냅니다. (원본 원격 저장소의 관리자가 코드 리뷰를 진행하여 반영 여부를 결정합니다.)

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc82e4c12-dc9a-48f3-bba9-f9dca06eb5a1%2FUntitled.png?table=block&id=e0d91c00-4972-4866-a5ab-e93a0c1abc86&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

8. `원본 원격 저장소(upstream)`의 master에 브랜치가 병합되면 `복제 원격 저장소(origin)`의 브랜치는 삭제합니다. 그리고 사용자는 로컬에서 master 브랜치로 이동합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F88eabf2b-490c-4e22-b284-8c3789b1729e%2FUntitled.png?table=block&id=d02de39a-898f-4fe8-9b39-8bf8a3155062&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git switch master
   ```

9. 병합으로 인해 변경된 `원본 원격 저장소(upstream)의 master` 내용을 로컬에 받아옵니다. 그리고 기존 로컬 브랜치는 삭제합니다. (한 사이클 종료)

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa213ba54-b4c1-487a-9745-f6316928f3bd%2FUntitled.png?table=block&id=9c4b0c4e-01cc-4bd2-9c99-e3d887794608&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   ```bash
   $ git pull upstream master
   $ git branch -d feature/login
   ```

10. 새로운 기능 추가를 위해 새로운 브랜치를 생성하며 위 과정을 반복합니다.

    ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fd9e93191-e93c-4395-baaf-127d88cdf729%2FUntitled.png?table=block&id=8eb55a5c-bd53-453a-920a-4e168aaba708&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

    

    ```bash
    $ git switch -c feature/pay
    ```

## [3] Pull Request (PR) 자세히 알아보기

> Github 화면을 통해 Pull Request 과정을 자세히 알아봅니다.

1. 브랜치를 Push 하면 `Compare & pull request` 라는 알림 버튼이 나타나는데, 이를 누르면 됩니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8e93888e-c19b-4c07-ac2e-d58e03ee7e1d%2FUntitled.png?table=block&id=c60306b8-836d-45b6-b6a5-0727d318e320&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

2. 혹은 원격 저장소 상단 바에서 `Pull requests → New pull request`을 통해서도 가능합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fcd42e34a-aae5-42ff-95cb-efa5226e2eb9%2FUntitled.png?table=block&id=2cfcf3ed-318c-4c01-8f64-89a3bf8ef286&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

3. `base`는 병합될 대상입니다. `master를 base로` 두면 됩니다. `compare`는 병합할 대상입니다. 우리가 만든 `feature/login 브랜치를 compare로` 두면 됩니다. 그리고 아래쪽에서 비교 내용을 확인하고 `Create pull request`를 클릭합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F16d746e2-6f1d-4272-912f-ccfe7f4580f3%2FUntitled.png?table=block&id=275beb00-4e80-4696-beb4-e445d08fce7c&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

4. Pull Request에 대한 제목과 내용, 각종 담당자를 지정하는 페이지가 나옵니다. 모두 작성했다면 `Create pull request`를 눌러서 PR을 생성합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Ffed29aad-7ec5-4f93-8afd-684afc195e65%2FUntitled.png?table=block&id=26da7371-41d3-46dd-bafa-b2bc57ff2382&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   `Reviewers` : 현재 PR에 대해 코드 리뷰를 진행해 줄 담당자

   `Assignees` : 현재 PR에 대한 작업을 맡고 있는 담당자

5. PR이 생성되면 다음과 같은 화면이 나타납니다. 빨간 표시가 된 세 부분을 살펴보겠습니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fe2ba1dd2-57ff-40f4-9f58-1053f1c00ccc%2FUntitled.png?table=block&id=c854e50c-3926-40b6-b1d5-c6d656ea5e2f&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

6. `Conversation` : 아래 Write 부분에서 comment를 별도로 작성할 수도 있습니다. 그리고 `Merge pull request` 버튼을 누르면 병합이 시작됩니다. (충돌(conflict) 상황에서는 충돌을 해결하라고 나옵니다.)

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0e1a6f87-17b2-4c79-8ab6-879b1891aa8e%2FUntitled.png?table=block&id=ca27c177-0ea2-457c-b2b8-c6041baed068&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

7. `Commits` : PR을 통해 반영될 커밋들을 볼 수 있습니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F3c37c888-187a-47c2-b945-94fb440f6a88%2FUntitled.png?table=block&id=4d066510-e04d-4abd-82c9-169f49afe3d3&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)`Files changed` : 파일의 변화 내역들을 볼 수 있습니다.

   

8. 코드리뷰를 원하는 라인에서 `+` 를 눌러서 해당 라인에 리뷰를 남길 수 있습니다.

   빨간 사각형으로 표시된 작은 아이콘을 클릭하면, **`suggestion 기능`(코드를 이렇게 바꾸라고 추천하는 기능)**을 넣을 수도 있습니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1cd52944-6941-4302-b520-c54eac4f2447%2FUntitled.png?table=block&id=aada09ec-769f-4fb5-8ba0-99b9155251aa&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

9. 코드 리뷰를 끝내려면 `Finish your review` 버튼을 누르면 됩니다. 그리고 옵션을 선택하고 `Submit review`를 클릭합니다.

   ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F1cd52944-6941-4302-b520-c54eac4f2447%2FUntitled.png?table=block&id=aada09ec-769f-4fb5-8ba0-99b9155251aa&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

   

   - `Comment`: 추가적인 comment를 작성할 경우 선택
   - `Approve`: merge를 승인하는 경우 선택
   - `Request change` : 수정해야 하는 사항이 있을 경우 선택

10. 다시 conversation으로 가보면 진행했던 리뷰가 이렇게 나타난 것을 확인할 수 있습니다.

    ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc69d4afa-c6df-4b42-8226-cb51c2f45ef0%2FUntitled.png?table=block&id=65e81a81-eede-45e4-b829-44b73766d54e&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

    

11. 병합을 하게 되면 아래와 같이 보라색으로 병합이 완료되었다고 나오면 성공입니다.

    `Delete branch` 버튼을 통해 병합된 `feature/login` 브랜치를 지울 수 있습니다. (원격 저장소에서만 지워집니다.)

    ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fefb77ecb-305a-472d-9414-ece0ec9192b8%2FUntitled.png?table=block&id=f93ed24b-de93-41f1-a6b3-297612189bb1&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

    

12. `master`를 확인해보면 `feature/login`의 내용이 master에 병합된 것을 확인할 수 있습니다.

    ![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F311953ae-acc1-4393-9f28-c724efc92aee%2FUntitled.png?table=block&id=07ffcb3d-018e-4549-9636-3a126e9c8c1e&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

    

13. 이후 로컬 저장소의 master 브랜치에서 `git pull`을 이용해 로컬과 원격을 동기화 합니다.

