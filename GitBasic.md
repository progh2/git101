# 1. Git 시작하기
git을 사용하여 소스를 관리하는 방법에 대해서 알아보도록 하겠습니다.

## 1.1 터미널 띄우기
터미널은 커맨드라인(CommandLine), cmd창, 콘솔창 등 여러 이름으로 불리곤 하며 글자 명령어로 컴퓨터와 소통하는 프로그램입니다. 이런 방식을 `CUI(Character User Interface)`라고 합니다. 

이제 `Windows + r`키를 눌러서 `실행`입력창을 띄운 후 `cmd` 명령어를 입력해서 터미널을 실행합니다.

![image](https://user-images.githubusercontent.com/1307187/56176699-dcc66200-6036-11e9-9509-8aac14ae46ea.png)

![image](https://user-images.githubusercontent.com/1307187/56176722-eea80500-6036-11e9-8131-19776fee517a.png)

## 1.2 Home Directory

![image](https://user-images.githubusercontent.com/1307187/56176722-eea80500-6036-11e9-8131-19776fee517a.png)

터미널 화면을 보면 하얀 밑줄 막대가 깜짝이는데 이를 `커서` 또는 `프롬프트`라고 합니다. 사용자가 명령어를 입력할 수 있음을 알려줍니다. 커서 왼쪽에는 `C:\Users\Mirim>`라고 표시가 되어 있습니다. 

처음 터미널을 실행했을 때 시작하는 이 디렉토리 경로를 `Home Directory`라고 합니다. 즉 `Mirim` 사용자의 개인 디렉토리라는 의미입니다. 만약 `FooBar`라는 사용자가 로그인해서 `cmd`를 실행했다면 `C:\Users\FooBar`가 그 사용자의 `Home Directory`가 될 것입니다. 

이제 다음 명령어를 실행합니다.
```cmd
dir
```

> ![image](https://user-images.githubusercontent.com/1307187/56176913-b05f1580-6037-11e9-8216-0fbcf6b9bd11.png)

dir 명령을 하면 자신의 `Home Directory`의 파일, 디렉토리 목록이 나타납니다. 단 윈도우의 바탕화면(`단축키:Windows + d`)과는 다르게 주요 디렉토리명이 한글이 아니라 영어로 표시됨을 알 수 있습니다.


**디렉토리 영문 - 한글 표시**

원래 디렉토리명 | 한글 별명
---- | ----
Desktop | 바탕화면
Documents | 문서
Downloads | 다운로드
Favorites | 즐겨찾기
Music | 음악
Pictures | 사진
Videos | 비디오

## 1.3 파일탐색기(Explorer)에서의 Home Directory
![image](https://user-images.githubusercontent.com/1307187/56176949-d5538880-6037-11e9-9b94-b49768de71cc.png)

단축키 `Windows + e` 를 눌러서 파일탐색기(Explorer)를 실행하여 자신의 계정의 `Home Directory`로 들어가보면 익숙한 디렉토리(다운로드, 문서, 바탕화면 등)가 보이는 것을 알 수 있습니다. 파일탐색기에서는 사용자 편의를 위하여 `다운로드`, `문서`와 같이 주요 디렉토리명이 한글로 표시가 됩니다. C:\Users의 `Users` 디렉토리 또한 `사용자`로 표시됩니다. 하지만 여러분이 `cd`명령으로 `터미널`에서 이동을 하려면 **원래 영문 디렉토리명**으로 사용해야 함을 기억하기 바랍니다.

이제 버전관리를 하기 위한 예제를 만들기 위해 디렉토리를 생성해봅니다.

## 1.4 작업 디렉토리(Working Directory) 생성
 다음과 같이 `gitexample`이라는 디렉토리를 생성하고 해당 디렉토리로 이동합니다.

 ```cmd
 mkdir gitexample
 cd gitexample
 dir
 ```

![image](https://user-images.githubusercontent.com/1307187/56177794-d803ad00-603a-11e9-90cd-8b460756b0ac.png)

방금 만든 디렉토리라서 아무것도 없습니다. 

> *[노트]* `.`는 `현재 디렉토리`라는 의미이며 `..`는 상위 디렉토리를 의미합니다. 그래서 `cd .` 명령을 내리면 현재 디렉토리로 이동(제자리 뛰기나 마찬가지라서 위치가 바뀌지 않음), `cd ..`하면 상위 디렉토리로 이동하게 됩니다. 

이 디렉토리 안에 작업 파일들(프로젝트, 소스 등)을 저장할 것입니다. 이렇게 작업하는 위한 디렉토리를 `Working Directory`라고 합니다. 나중에 살펴볼 `저장소(Repository)`와 구분하는 용어이므로 꼭 기억하기 바랍니다. 

> *[노트]* 리눅스에서는 현재 디렉토리 위치를 알기위해 `pwd`라는 명령어가 있는데, 여기서 pwd의 의미가 `Print Working Directory`(작업 디렉토리를 표시해라) 또는 `Present Working Directory`(현재 작업 디렉토리)라고 합니다.

## 1.5 샘플 파일 생성
이제 저장소에 넣기 위한 샘플 소스를 만들어 봅니다. 

```cmd
notepad README.md
```

위 명령어를 실행하면 메모장이 뜨면서 `README.md`파일이 없다고 생성하겠냐는 내용이 나옵니다. 

![image](https://user-images.githubusercontent.com/1307187/56178208-5f9deb80-603c-11e9-9816-62d7ceff46c8.png)

`예(Y)`를 누르면 파일이 생성됩니다. 안에 다음과 같은 샘플 코드를 작성해 넣습니다.

```md
# Nice Project
## About
Git practice example project
## Dev. Language
C#, .Net Framework4
```

![image](https://user-images.githubusercontent.com/1307187/56178318-d3d88f00-603c-11e9-96cd-c606ced1a61d.png)

`Ctrl + s`를 눌러서 내용을 저장합니다. 이제 내용이 잘 저장되었는지 확인하기 위해서 터미널에서 확인해봅니다.

```cmd
dir
type README.md
```

![image](https://user-images.githubusercontent.com/1307187/56178388-113d1c80-603d-11e9-9325-59b57b36fb30.png)

README.md 파일이 생성되었고 용량이 93바이트임을 알 수있습니다. 또한 텍스트 파일 내용을 간단하게 확인할 수 있는 `type` 명령으로 README.md 파일을 열어보니 내용이 잘 작성되어 있음을 확인할 수 있습니다.

## 1.6 저장소(repository) 생성하기
이제 git 명령으로 상황을 확인하기 위해 `git status` 명령을 실행합니다. `git status` 명령은 소스나 디렉토리에 어떠한 변경사항을 만들지 않으며 단지 어떠한 변경사항이 있는지만 표시해주는 명령으로 앞으로도 빈번하게 사용하게 될 것입니다. 

```cmd
git status
```

![image](https://user-images.githubusercontent.com/1307187/56178520-86105680-603d-11e9-98f0-df8f7b4358e5.png)

`git status` 명령을 실행하니 다음과 같은 에러 메시지가 출력됩니다.

> fatal: not a git repository (or any of the parent directories): .git

현재 디렉토리에 .git 이라는 git repository가 없어서 심각한`(fatal) 문제가 있다는 내용입니다. 말 그대로 repository가 없어서 에러가 나는거니 repository를 생성해줍니다.

```cmd
git init
```

![image](https://user-images.githubusercontent.com/1307187/56178639-f1f2bf00-603d-11e9-8c42-b977fde2cfd7.png)

`git init` 명령을 실행하면 `Working Directory` 안에 있는 `.git` 이라는 디렉토리에 저장소를 초기화 하였다는 메시지가 출력됩니다. 어디에 .git 디렉토리가 생성되었는지 경로를 확인해보도록 합니다.

## 1.7 저장소(repository) 생성 확인하기 - 터미널에서 확인하기
자, 정말로 제대로 디렉토리가 생성되었는지 `cmd` 명령으로 확인해 봅니다.

```cmd
dir
```

![image](https://user-images.githubusercontent.com/1307187/56178701-21093080-603e-11e9-83da-04d5db98f8ec.png)

확인해보면 저장소를 생성하기 전과 차이가 없습니다. .git 디렉토리를 생성했다는데 보이지 않습니다! `윈도우` 운영체제에서는 `.git` 디렉토리는 `숨김 속성`이 적용되어 바로 볼 수 없습니다. 숨겨진 파일/디렉토리를 보기 위해서는 `/a` 옵션을 붙여서 `dir /a`명령으로 확인해야 합니다. 

``` cmd
dir /a
```

![image](https://user-images.githubusercontent.com/1307187/56178820-94ab3d80-603e-11e9-9d05-4b2759f9dc8a.png)

`dir /a` 명령으로 숨겨진 `.git` 디렉토리가 보입니다. 이 디렉토리가 현재 우리가 작업하는 Working Directory의 저장소(Repository)로 여기에 소스의 모든 역사가 담기게 됩니다. 소중히 관리해야 합니다. 

## 1.8 저장소(repository) 생성 확인하기 - 파일 탐색기에서 확인하기
파일탐색기(explorer)에서 Working Directory로 이동합니다. 역시 Repository인 `.git` 디렉토리가 보이지 않습니다.

![image](https://user-images.githubusercontent.com/1307187/56179033-49ddf580-603f-11e9-95ce-d71e598ac16b.png)

파일탐색기의 `보기` 탭을 클릭하여 우측에 `숨긴 항목`을 체크합니다. 편의를 위하여 `파일 확장명`도 체크한 상태로 만듭니다.

![image](https://user-images.githubusercontent.com/1307187/56179080-6bd77800-603f-11e9-8e19-9e41b9b45ca7.png)

> *[노트]* 만약 여러분의 윈도우 운영체제 버전이 `10`이 아니라면 `숨김항목`을 표시하는 방법이 살짝 다릅니다. 구글 등에 검색해보기 바랍니다. [검색해보기](https://www.google.com/search?q=%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C+%EB%B3%84+%EC%88%A8%EA%B9%80%ED%95%AD%EB%AA%A9+%ED%91%9C%EC%8B%9C%ED%95%98%EA%B8%B0&rlz=1C1NHXL_koKR839KR839&oq=%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C+%EB%B3%84+%EC%88%A8%EA%B9%80%ED%95%AD%EB%AA%A9+%ED%91%9C%EC%8B%9C%ED%95%98%EA%B8%B0&aqs=chrome..69i57.5041j0j1&sourceid=chrome&ie=UTF-8)

이제 `.git` 디렉토리가 나타남을 알 수 있습니다. 이러한 `숨김` 기능은 일반 사용자가 실수로 중요한 파일을 삭제하거나 이동하는 것을 막기 위해 있는 기능입니다. 

![image](https://user-images.githubusercontent.com/1307187/56179219-d38dc300-603f-11e9-9f12-126289e4a77a.png)

> *[노트]* 만약 파일 또는 디렉토리의 `숨김` 속성을 적용/해제하고 싶다면 해당 파일/디렉토리를 `우측 마우스 클릭`하여 `속성`으로 들어갑니다. 그러면 `숨김` 속성 항목이 나타나며 이 항목을 체크하거나 해제해서 숨김 처리를 선택할 수 있습니다. 단, `바탕화면`이나 `파일탐색기`에서 숨긴 상태가 안보이게 하려면 앞에 파일탐색기에서 설정했던 `숨김항목`을 표시하지 않게 돌려놔야 합니다.
>
> ![image](https://user-images.githubusercontent.com/1307187/56179309-223b5d00-6040-11e9-81d5-1e02bac511ce.png)

## 1.9 Staging 하기
자 이제 `git status` 명령으로 Woring Directory의 버전관리 상태를 확인해봅니다. 
```cmd
git status
```

![image](https://user-images.githubusercontent.com/1307187/56178613-ddaec200-603d-11e9-90fe-63afec171556.png)

위 내용에서 얻을 수 있는 정보는 다음과 같습니다. 

> On branch master 

master branch 상태입니다.(branch에 대해서는 나중에 배웁니다.)

> No commits yet

커밋 내역이 없습니다. 빈 저장소입니다. 
 
> Untracked files:
   (use "git add <file>..." to include in what will be committed)
>
>        README.md
 
추적(track)되지 않는(Un) 파일이 있는데 이 파일은 README.md라는 파일입니다. (커밋 할 생각이라면 `git add 파일명` 명령을 사용하세요)

우리가 마트에 가서 물건을 살 때 살 물건 각각마다 결제하지 않고 모아서 한번에 결제하는 것처럼 Git 또한 매번 커밋하지 않습니다. 장바구니에 물건 담듯이 커밋할 대상들을 표시해놓고 의미를 나눠서 커밋해서 저장소에 넣곤 합니다. 여기서 장바구니에 물건을 담는 것 같은 과정을 Staging 또는 Add to Index라고 합니다. 공연 할 아이돌들이 Stage(무대)에 오르거나 특정 목적으료 명렬(Index)에 표시하는 것과 닮아 있습니다. 

이제 파일을 커밋하기 위해서 스테이징을 하도록 합니다.
```cmd
git add README.md
```
![image](https://user-images.githubusercontent.com/1307187/56188217-dd272300-605f-11e9-8d5d-dc9f9aade63f.png)

스테이징을 한 명령만으로는 특별히 바뀐게 없어 보입니다. 다시 `git status` 명령으로 상태를 보도록 합니다.

```cmd
git status
```
![image](https://user-images.githubusercontent.com/1307187/56188277-05168680-6060-11e9-9c71-688b0d430b4b.png)

아까와는 메시지가 다르게 변해있습니다. 커밋을 하기 위한 변경 사항으로 README.md 파일이 새 파일로 추가된다고 알려주고 있습니다. 또한 스테이징에서 빼고 싶다면 `git rm --cached 파일명` 명령을 사용해서 제외할 수 있다고 알려줍니다. 

> *[노트]* 실수로 스테이징 한 경우에는 얼마든지 `git rm --cached 파일명` 명령을 사용해서 스테이징 상태에서 뺄 수 있습니다. 예를 들어 README.md 파일을 빼고자 한다면 다음과 같이 할 수 있습니다.
>
> ```cmd
> git rm --cached README.md
> ```
>
> 위와 같이 하면 README.md파일은 언스테이징(unstage)가 되며 스테이징 하기 전상태로 돌아가게 됩니다.  필요에 따라서 add 명령으로 다시 스테이징 할 수 있습니다.

## 커밋(commit)하기(1)
자, 이제 스테이징이 되었어니 커밋도 해보기로 합니다. 커밋(Commit)이란 스테이징된 변경사항들을 저장소에 반영하는 것을 의미합니다.


## 사용자 정보 등록하기

```cmd
git config global user.name "영문이름"
git config global user.email "이메일주소"
```

## 커밋(commit)하기(2)


## Github 가입(join/sign up), 로그인(sign in) 하기 

## Github 원격 저장소(Remote Repository) 생성하기

## 지역 저장소에 원격저장소 별명 등록, 지역 저장소의 커밋 내역을 원격 저장소로 커밋 보내기(Push)


