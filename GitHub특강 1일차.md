# Git 특강

## git을 왜 배우는가?

> git 이란 버전 관리 프로그램이다.

**git의 저장 방식**

1. 스냅샷

   ​	원본 파일과 변경된 파일 모두 저장하는 방식

2. 델타

   ​	원본파일하나와 변경 이력을 저장하는 방식

   ​	git은 변경 이력을 이용하여 버전별로 접근 할 수 있다.



- **git**은 **백업, 복원, 협업**을 하기 좋은 **무료프로그램**



- **git** 을 이용하여 **포트폴리오 작성**이 가능하다.





## git 특강을 위한 파일 설치



**git 설치**

[git 설치링크](https://hphk.notion.site/Git-Windows-7afbe2e93a014c93a6b49567819590b1)



**vs코드설치**

[VS 설치링크](https://hphk.notion.site/Vscode-Windows-Mac-fa6b0a5e8a9c43ce83da7c64e45f9704)



**Typora 설치**

[typora 설치링크](https://hphk.notion.site/hphk/Git-22-03-28-22-03-30-6-2157d9f961584680aa29fa19f9b5a68e?p=ce2e739f64da460f9bc27ba2ccdfe108)



## markdown 문법







---

### git 초기설정 및 기본명령어



git은 working directory, staging area, commits 라는 세 공간으로 이루어져 있음

![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7142d992-3d01-481c-9d4e-e818c6e185d8%2FUntitled.png?table=block&id=16a9c8b1-0b82-4bf9-93d4-331980c4d79a&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)

- `Working Directory (= Working Tree)` : 사용자의 일반적인 작업이 일어나는 곳
- `Staging Area (= Index)` : 커밋을 위한 파일 및 폴더가 추가되는 곳
- `Repository` : staging area에 있던 파일 및 폴더의 변경사항(커밋)을 저장하는 곳
- Git은 **Working Directory → Staging Area → Repository** 의 과정으로 버전 관리를 수행합니다.



`git config --global user.name "이름"`

`git config --global user.emial "메일주소"`

로 커밋기록을 누가 남겼는지 설정가능

`git config --global -l`

로 설정 확인 가능



#### git init

현재 작업중인 디렉토리를 git으로 관리한다는 명령어

`.git`이라는 숨김 폴더를 생성

**이미 git 저장소인 폴더 내부엥 또 git저장소를 만들지 않음(중첩x)**

**홈 디렉토리에서 git init을 하지 않음**

#### git status

working directory와 staging area 에 있는 파일의 현재 상태를 알려주는 명령어

작업을 시행하기전에 수시로 해주는게 좋다

1. `Untracked` : Git이 관리하지 않는 파일 (한번도 Staging Area에 올라간 적 없는 파일)

2. ```
   Tracked
   ```

    : Git이 관리하는 파일

   1. `Unmodified` : 최신 상태
   2. `Modified` : 수정되었지만 아직 Staging Area에는 반영하지 않은 상태
   3. `Staged` : Staging Area에 올라간 상태



#### git add

- Working Directory에 있는 파일을 Staging Area로 올리는 명령어
- Git이 해당 파일을 추적(관리)할 수 있도록 만듭니다.
- `Untracked, Modified → Staged` 로 상태를 변경합니다.

``` gitbash
#특정 파일
$ git add a.txt

#특정 폴더
$ git add my_folder/
#현재 디렉토리에 속한 파일,폴더 전부
$ git add .
```



#### git commit

- Staging Area에 올라온 파일의 변경 사항을 하나의 버전(커밋)으로 저장하는 명령어
- `커밋 메세지`는 현재 변경 사항들을 잘 나타낼 수 있도록 `의미` 있게 작성하는 것을 권장합니다.
- 각각의 커밋은 `SHA-1` 알고리즘에 의해 반환 된 고유의 해시 값을 ID로 가집니다.
- `(root-commit)` 은 해당 커밋이 최초의 커밋 일 때만 표시됩니다. 이후 커밋부터는 사라집니다.



#### git log

- 커밋의 내역(`ID, 작성자, 시간, 메세지 등`)을 조회할 수 있는 명령어
- 옵션
  - `--oneline` : 한 줄로 축약해서 보여줍니다.
  - `--graph` : 브랜치와 머지 내역을 그래프로 보여줍니다.
  - `--all` : 현재 브랜치를 포함한 모든 브랜치의 내역을 보여줍니다.
  - `--reverse` : 커밋 내역의 순서를 반대로 보여줍니다. (최신이 가장 아래)
  - `-p` : 파일의 변경 내용도 같이 보여줍니다.
  - `-2` : 원하는 갯수 만큼의 내역을 보여줍니다. (2 말고 임의의 숫자 사용 가능)



![img](https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fc86c667a-616f-45b6-892e-15da6a3c494e%2FUntitled.png?table=block&id=a6753b22-5808-4fe5-bb87-95e832bdcaad&spaceId=daa2d103-3ecd-4519-8c30-4f55e74c7ef4&width=1260&userId=57da478c-10a4-4cea-b600-6b58f3673e85&cache=v2)







[강의자료 노션](https://hphk.notion.site/Git-22-03-28-22-03-30-6-2157d9f961584680aa29fa19f9b5a68e  )



