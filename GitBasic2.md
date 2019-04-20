# Git으로 협업하기
Git으로 협업하는 경우 일어날 수 있는 상황에 대해서 처리하는 방법에 대해서 알아보도록 합니다.

## 1. 서로 다른 파일 추가, 수정하기
프로젝트에서 지역 저장소(Local Repository)와 원격 저장소(Remote Repository)에 각각 새로운 파일이 만들어지는 경우에 대해서 알아보겠습니다. 예를 들면 2명의 개발자가 각기 다른 파일을 만들어서 커밋, 푸쉬한 경우 이런 상황이 일어날 수 있습니다. 

### Local Repository에 파일 추가히기

다음과 같은 내용으로 INSTALL.md 라는 파일을 만들어 스테이징, 커밋, 푸쉬합니다.

```md
# INSTALL
## Requirement
* Windows 7
* JDK 1.6

## Install 
1. Download file
1. Unzip file
```

```cmd
notepad INSTALL.md
```

![image](https://user-images.githubusercontent.com/1307187/56461019-ebba6500-63e6-11e9-95f9-feabcb82c996.png)

```cmd
git add INSTALL.md
git commit -m "Add INSTALL.md"
```

![image](https://user-images.githubusercontent.com/1307187/56461076-aa768500-63e7-11e9-9734-149ff7f444a4.png)

### Remote Repository에 파일 추가하기 
깃허브 프로젝트에서 `Code` 탭을 클릭 후 `Create new file`을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56461104-32f52580-63e8-11e9-966e-aac34deb587c.png)

파일 이름은 `Greeting.md`로, 내용은 다음과 같이 작성합니다.

```md
# Hello, World?!
# 안녕, 세계야?!
```

![image](https://user-images.githubusercontent.com/1307187/56461124-78b1ee00-63e8-11e9-9dce-f4842fce135d.png)

화면 하단으로 스크롤하면 커밋 메시지를 작성하는 박스가 있습니다. 즉, 깃허브에서 간편하게 파일 생성 또는 편집을 할 수 있고 `Create new file`을 클릭하면 커밋, 푸쉬를 하는 것과 동일한 결과를 얻을 수 있습니다. `Create new file` 버튼을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56461134-ae56d700-63e8-11e9-829b-d761394f5599.png)

Greeting.md 파일이 커밋, 푸시된 것과 같은 결과가 나타난 것을 확인할 수 있습니다.

![image](https://user-images.githubusercontent.com/1307187/56461154-fd047100-63e8-11e9-8b6f-ed7b0184324d.png)

### Local Repository에서 파일 푸시하기(1)

이제 Local Repository에서 푸쉬를 해줍니다.

```cmd
git push origin master
```

![image](https://user-images.githubusercontent.com/1307187/56461167-3d63ef00-63e9-11e9-8cc8-0b5700992d16.png)

하지만 기대와는 다르게 푸쉬가 실패합니다. 메시지 내용을 해석해보면 다음과 같습니다.

> > To https://github.com/progh2/learngit.git 
> >
> > ! [rejected]        master -> master (fetch first)
>
>  ![거부됨] master -> master (fetch를 먼저 하세요)
>
>> error: failed to push some refs to 'https://github.com/progh2/learngit.git'
>
> 에러: 'https://github.com/progh2/learngit.git' 로 푸쉬가 실패하였습니다.
>
>> hint: Updates were rejected because the remote contains work that you do
>>
>> hint: not have locally. This is usually caused by another repository pushing
>> 
>> hint: to the same ref. You may want to first integrate the remote changes
>> 
>> hint: (e.g., 'git pull ...') before pushing again.
>> 
>> hint: See the 'Note about fast-forwards' in 'git push --help' for details.
>
> 도움말: 업데이트가 거절되었습니다. 왜냐하면 원격 저장에는 여러분의 지역저장소가 가지지 못한 작업들을 가지고 있기 때문입니다. 이 경우는 보통 다른 저장소에서 같은 원격 저장소로 푸시를 했을 때 발생합니다. 아마도 여러분은 푸쉬를 다시 하기 전에 원격 저장소의 변경 사항을 통합을 
먼저 해야할 것입니다.(예를들어 'git pull ...' 같은). 자세한 것을 알고 싶다면 'git push --help' 명령을 실행한 후 'Note about fast-forwards' 항목을 읽어보세요.

내용을 읽어보니 원격 저장소에 우리의 지역 저장소(즉 내 컴퓨터)에 없는 커밋 내역이 있어서 그걸 먼저 가져온 후 푸쉬를 하라고 합니다. 그대로 따라서 해봅시다.

### git pull로 Remote Repository의 Commit 내역을 Local Repository로 가져오기

push(밀다)의 반댓말은 pull(당기다)입니다. 원격 저장소에 있는 커밋 내역을 받아와봅시다.

```cmd
git pull origin master
```

![image](https://user-images.githubusercontent.com/1307187/56461477-bdd91e80-63ee-11e9-8962-0e5108711b9d.png)

>> Merge made by the 'recursive' strategy.
>>
> `재귀` 전략 방식으로 머지됩니다.
>> Greeting.md | 2 ++
>>
>> 1 file changed, 2 insertions(+)
>>
>> create mode 100644 Greeting.md
>
> 1개 파일이 수정됨, 2 줄 추가(+)
>
> 생성 모드 100644 Greeting.md

서로 다른 파일을 각기 추가한 경우 Git은 똑똑하게 처리하여 자동으로 합쳐주는 머지 커밋을 만듭니다. 따라서 `git pull origin master` 명령을 실행하면 원격 저장소에서 추가했던 Greeting.md 파일이 지역 저장소에도 생성된 것을 확인할 수 있습니다. 

```cmd
dir
type Greeting.md
```

![image](https://user-images.githubusercontent.com/1307187/56461283-ed862780-63ea-11e9-923b-a8a1d7367053.png)


### git push로 Local Repository Commit 내역을 Remote Repository로 보내기

이제 지역 저장소에서 원격 저장소로 푸쉬를 합니다.

```cmd
git push origin master
```

![image](https://user-images.githubusercontent.com/1307187/56461529-86b73d00-63ef-11e9-8747-cd2dd083955b.png)

이번에는 잘 푸시가 되는 것을 확인할 수 있습니다. 

### Github에서 Commit 내역 살펴보기

깃허브 프로젝트로 가서 `Commits`을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56461536-ab131980-63ef-11e9-9136-56c60e949f43.png)

들어가면 각각 만들었던 커밋 외에 Git에 의해서 합쳐주는 머지 커밋(Merge Commit)이 하나 더 생성되어 있음을 알 수 있습니다. 

![image](https://user-images.githubusercontent.com/1307187/56461549-d72e9a80-63ef-11e9-8510-e00b9e11b614.png)

### Github의 Insights, Network 살펴보기

깃허브의 `Insight` 탭에서 `Network`를 클릭합니다

![image](https://user-images.githubusercontent.com/1307187/56461571-1a890900-63f0-11e9-9d2a-86fdc522e041.png)

보면 각 커밋이 점으로 표시되며 갈라져 나온 커밋이 다시 합쳐지는 모습을 볼 수 있습니다. 

## 2. 서로 같은 파일의 다른 영역 수정하기
이번에는 지역 저장소, 원격 저장소에서 같은 파일의 다른 영역을 같이 수정한 경우 어떤 일이 발생하며 어떻게 해결해야 하는지 알아보도록 하겠습니다.

### Remote Repository에 파일 수정하기 
깃허브 프로젝트에서 `Code` 탭을 클릭한 후 INSTALL.md 파일을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56461709-2d044200-63f2-11e9-88a3-2b7af09b5c39.png)

우측 상단에 연필 모양의 편집 아이콘을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56461712-43aa9900-63f2-11e9-8ce3-705106cd21be.png)

내용을 다음과 같이 수정합니다. (숫자만 7을 10으로, 1.6을 1.11로 변경합니다.)

*수정전*

```md
## Requirement
* Windows 7
* JDK 1.6
```

![image](https://user-images.githubusercontent.com/1307187/56461740-ac921100-63f2-11e9-9e02-e6090bf64514.png)

*수정후*
```md
## Requirement
* Windows 10
* JDK 1.11
```

![image](https://user-images.githubusercontent.com/1307187/56461745-be73b400-63f2-11e9-9ca6-7525e29aa028.png)

커밋 메시지를 `설치 버전 업데이트`로 적고, 하단의 `Commit changes` 버튼을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56461755-d51a0b00-63f2-11e9-8c4c-57f9e60ccfec.png)

윈도우와 JDK 버전이 변경된 것을 확인할 수 있습니다.

![image](https://user-images.githubusercontent.com/1307187/56461767-0397e600-63f3-11e9-9836-6c4e691a734c.png)


### Local Repository에 파일 수정히기

이번에는 지역 저장소의 INSTALL.md 파일을 수정합니다. 노트패드 같은 프로그램으로 INSTALL.md 파일을 엽니다.

```cmd
notepad INSTALL.md
```

![image](https://user-images.githubusercontent.com/1307187/56461780-3d68ec80-63f3-11e9-8fcc-7df49a41c307.png)

내용을 다음과 같이 수정합니다. (`1. Execute Setup.exe` 한 줄을 추가합니다. )

*수정전*

```md
## Install 
1. Download file
1. Unzip file
```

![image](https://user-images.githubusercontent.com/1307187/56461788-4d80cc00-63f3-11e9-9939-b858e02f88fe.png)


*수정후*
```md
## Install 
1. Go to download page
1. Download file
1. Unzip file
```

![image](https://user-images.githubusercontent.com/1307187/56461901-262afe80-63f5-11e9-997b-d08dda589f13.png)

저장 후 스테이징, 커밋을 합니다.

```cmd
git add INSTALL.md
git commit -m "설치 과정 추가"
```

![image](https://user-images.githubusercontent.com/1307187/56461926-71dda800-63f5-11e9-845a-84363c3e5a99.png)

### Local Repository에서 파일 푸시하기(1)

지역 저장소의 커밋 내역을 원격 저장소로 푸시합니다.

```cmd
git push origin master
```

![image](https://user-images.githubusercontent.com/1307187/56461966-106a0900-63f6-11e9-9477-dde5cc68be4f.png)

이전과 비슷해보이지만 살짝 내용이 다릅니다. 

### git pull로 Remote Repository의 Commit 내역을 Local Repository로 가져오기

앞서 해결했던 방법대로 `git pull origin master`를 해봅니다.

```cmd
git pull origin master
```

![image](https://user-images.githubusercontent.com/1307187/56461970-414a3e00-63f6-11e9-9c5d-163b8e9d01d5.png)

Git pull을 실행하니 `Auto-merging`이 성공하여 Git이 자동으로 파일을 합쳐주었습니다. 

INSTALL.md 파일 내용을 확인해보면 원격, 지역 저장소에서 수정한 내용이 각각 반영되어 있음을 알 수 있습니다.

```cmd
type INSTALL.md
```

![image](https://user-images.githubusercontent.com/1307187/56461980-6fc81900-63f6-11e9-83d2-68e45fc89871.png)


### git push로 Local Repository Commit 내역을 Remote Repository로 보내기

이제 원격 저장소로 푸쉬를 합니다. 잘 동작 합니다.

```cmd
git push origin master
```

![image](https://user-images.githubusercontent.com/1307187/56461994-abfb7980-63f6-11e9-9c6c-cf03d7371ffe.png)

### Github에서 Commit 내역 살펴보기

깃허브에서 `Code`, `Commits`를 클릭하면 다음과 같이 우리가 제작한 2개의 커밋 이후에 자동으로 합쳐준 `Merge Commit`이 생겨있는 것을 확인할 수 있습니다.

![image](https://user-images.githubusercontent.com/1307187/56462006-ce8d9280-63f6-11e9-9ea7-9e5978ac506d.png)

### Github의 Insights, Network 살펴보기
`Insights` 탭의 `Network` 메뉴로 가보면 다음과 같이 합쳐진 것을 확인할 수 있습니다.

![image](https://user-images.githubusercontent.com/1307187/56462027-05fc3f00-63f7-11e9-917d-fc4c8bd66963.png)

## 3. 서로 같은 파일 같은 영역 수정하기
이번에는 지역 저장소, 원격 저장소에서 같은 파일의 같은 영역을 같이 수정한 경우 어떤 일이 발생하며 어떻게 해결해야 하는지 알아보도록 하겠습니다.

### Remote Repository에 파일 수정하기 

깃허브에서 `Code` 탭으로 간 후 `README.md` 파일을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56462778-f505fa80-6403-11e9-939a-4ea9d11536dd.png)

우측 상단의 편집 아이콘을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56462784-11099c00-6404-11e9-8455-bfbfd5f9e773.png)

`Git practice example project`를 `Simple Project using Git`로 수정합니다.

*수정전*

```md
# Nice Project
## About
Git practice example project
## Dev. Language
C#, .Net Framework4
```

![image](https://user-images.githubusercontent.com/1307187/56462814-75c4f680-6404-11e9-881e-cad264737f0d.png)

*수정후*

```md
# Nice Project
## About
Simple Project using Git
## Dev. Language
C#, .Net Framework4
```

![image](https://user-images.githubusercontent.com/1307187/56462819-8a08f380-6404-11e9-9707-aabef38222fe.png)

하단의 커밋 메시지에 `프로젝트 설명 수정`이라 적고 `Commit changes` 버튼을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56462829-b6247480-6404-11e9-9d9d-d8a7909a6ce8.png)

README.md 파일이 수정된 것을 확인할 수 있습니다.

![image](https://user-images.githubusercontent.com/1307187/56462837-d9e7ba80-6404-11e9-89ad-582648a81e06.png)

### Local Repository에 파일 수정히기

이제 지역 저장소에 있는 README.md 파일을 수정합니다.

```md
notepad README.md
```

![image](https://user-images.githubusercontent.com/1307187/56462860-2e8b3580-6405-11e9-9923-7e5d8fb016d2.png)

`Git practice example project`를 `Git Simple Project`로 수정합니다.

*수정전*

```md
# Nice Project
## About
Git practice example project
## Dev. Language
C#, .Net Framework4
```

![image](https://user-images.githubusercontent.com/1307187/56462850-026fb480-6405-11e9-872e-853f2938563f.png)

*수정후*

```md
# Nice Project
## About
Git Simple Project
## Dev. Language
C#, .Net Framework4
```

![image](https://user-images.githubusercontent.com/1307187/56462864-4b276d80-6405-11e9-953a-fb94cf9b7088.png)

수정했으면 저장 후 스테이징, 커밋을 합니다. 

```cmd
git add README.md
git commit -m "프로젝트 소개 수정"
```

![image](https://user-images.githubusercontent.com/1307187/56462879-888bfb00-6405-11e9-8477-e89d1ce43982.png)


### Local Repository에서 파일 푸시하기(1)

이제 원격 저장소로 푸시를 해봅니다.

```cmd
git push origin master
```

![image](https://user-images.githubusercontent.com/1307187/56462923-2e3f6a00-6406-11e9-9225-0ffd650fb1ab.png)

하지만 에러 메시지와 함께 거절되었다는 내용이 나타납니다.

### git pull로 Remote Repository의 Commit 내역을 Local Repository로 가져오기

이제 원격 저장소의 변경사항을 가져오기 위해 `git pull` 명령을 실행합니다.

```cmd
git pull origin master
```

![image](https://user-images.githubusercontent.com/1307187/56462932-444d2a80-6406-11e9-9a84-037ae2b3c446.png)

앞에서의 사례1, 2와는 다르게 이번에는 자동 머지가 실패했다(`Automatic merge failed`)라고 표시가됩니다. 즉 Git이 판단하기에는 똑같은 부분이 수정되어서 어느쪽으로 어떻게 수정할 지 알 수가 없어서 `직접 고치고 커밋`하라(fix conflicts and then commit the result)는 메시지를 보여주고 있습니다. 

### 충돌 내용 해결하기
다행히 Git은 친절하기 때문에 어느 부분이 `충돌(CONFLICT)`이 발생했는지 표시해줘서 쉽고 빠르게 충돌난 부분을 알아보고 수정할 수가 있습니다. 이미 README.md 파일에 해당 부분이 표시되어 있으므로 파일을 열어봅니다.

```cmd
notepad README.md
```

![image](https://user-images.githubusercontent.com/1307187/56462973-c76e8080-6406-11e9-8e43-adc241d5a34d.png)


*충돌 해결 전*

```md
# Nice Project
## About
<<<<<<< HEAD
Git Simple Project
=======
Simple Project using Git
>>>>>>> 11f3b9c1cd478d8946d8a6e7394e272150645d31
## Dev. Language
C#, .Net Framework4
```

![image](https://user-images.githubusercontent.com/1307187/56462979-eff67a80-6406-11e9-83bd-0718013c9a9d.png)

위에서 보면 `=======` 를 경계로 `<<<<<<<HEAD` 와 `>>>>>>>` 영역에 충돌이 발생한 부분이 표시되고 있습니다. 그래서 이를 하나로 합쳐주고 부가적으로 표시된 부분을 삭제하면 됩니다. 두 내용을 적절히 수정해서 다음과 같이 변경해줍니다. 

> *[노트]* 일반적으로 이렇게 코드가 충돌이 생기고 작성한 사람이 다른 경우, 충돌난 코드를 작성한 사람과 대화를 하여 어떻게 수정할지 논의하고 수정해야 합니다. 논의 없이 마음대로 코드를 수정하면 감정적인 문제로 발전할 수 있으므로 일방적으로 코드를 수정하지 않도록 합니다.

*충돌 해결 후*

```md
# Nice Project
## About
Nice Simple Project using Git
## Dev. Language
C#, .Net Framework4
```

![image](https://user-images.githubusercontent.com/1307187/56463018-79a64800-6407-11e9-9cf3-32dc124bf733.png)

이제 저장 후 스테이징, 커밋을 해줍니다.

```cmd
git add README.md
git commit -m "머지 - 충돌 해결"
```

![image](https://user-images.githubusercontent.com/1307187/56463041-e883a100-6407-11e9-9266-f396c495e741.png)

### git push로 Local Repository Commit 내역을 Remote Repository로 보내기

이제 다시 푸시를 해봅니다.

```cmd
git push origin master
```

![image](https://user-images.githubusercontent.com/1307187/56463046-0e10aa80-6408-11e9-8291-7f981ec4f5ea.png)

푸시가 성공적으로 동작함을 알 수 있습니다.

### Github에서 Commit 내역 살펴보기

이제 깃허브 프로젝트의 `Code`탭으로 가서 `Commits`를 클릭해서 봅니다.

![image](https://user-images.githubusercontent.com/1307187/56463069-457f5700-6408-11e9-8c56-8d4d8839038c.png)

직접 충돌을 해결한 머지 커밋이 잘 반영되었음을 알 수 있습니다.

### Github의 Insights, Network 살펴보기
깃허브 프로젝트의 `Insights`탭 클릭, `Network` 메뉴로 들어가면 다음과 같이 합쳐진 것을 확인할 수 있습니다.

![image](https://user-images.githubusercontent.com/1307187/56463079-7d869a00-6408-11e9-9468-4b830c60d211.png)

## 4. Branch 생성해서 각자 개발, Pull Request 보내서 합치기
### 4.1 하나의 브랜치를 사용해서 공동 개발할 경우 한계
앞에서 하나의 Master 브랜치(Branch)를 가지고 작업을 할 수 있습니다만 이렇게 작업하면 몇 가지 아쉬운 점들이 발생하게 됩니다.

#### 두 명 이상 각각 별도의 기능을 개발하는경우 
두 명 이상 각각 별도의 기능을 개발하는 경우 서로 커밋, 푸쉬를 할 때마다 매번 풀(pull)을 하며 다른 사람이 수정한 코드를 가져와서 반영하며 수정해야합니다. 물론 서로의 푸시 주기가 시간 차이가 긴 경우에는 별 문제가 없습니다만 동일 시간대에 빈번하게 이루어진다면 번거로울 수 밖에 없고 또한 커밋 내역이 다른 기능들이 섞여서 한눈에 한 기능을 개발하기 위한 과정을 알아보기 힘든 문제가 있습니다.

게다가 누군가 실수로 에러가 있는 코드를 커밋하게 되면 해당 코드를 풀(pull) 해서 작업하는 경우 다른 사람도 에러가 발생하게 되서 곤란한 경우가 일어날 수 있습니다.

#### 프로젝트를 가져다 쓰고 싶어하는 사용자의 경우
그리고 외부에서 이 프로젝트를 가져다 쓰고 싶어하는 사용자가 있다고 할 때 최신의 Master 브랜치의 소스를 가져다 쓸 수가 없습니다. 개발 도중의 버전이기 때문에 버그나 에러 등 여러 문제가 있을 수 있습니다. 그렇기 때문에 프로젝트 개발자들은 따로 가져다 쓸 수 있는 소스코드를 만들어서 제공해줘야 하고 이를 위하여 별도의 시간을 투자해야만 합니다. 

그래서 위와같은 문제들을 해결하기 위해 `Branch(브랜치)`라는 기능이 만들어졌습니다. Branch는 특정 커밋 버전에 대한 책갈피(북마크) 같은 것으로 마치 C언어의 포인터처럼 특정 커밋을 나타내는 별명 같은 것입니다. 

branch 기능을 사용하면 기존 브랜치와는 별개로 커밋하며 개발해 나갈 수 있으며 필요에 따라서 branch의 변경이 자유롭습니다. 또한 한쪽 branch에 여러 커밋을 한 후 이 여러 커밋 내역을 다른 branch로 반영을 요청(Pull Request, 줄여서 PR)하는 것 가능하여 쉽게 개발한 기능을 합칠 수 있습니다. 

이렇게 개발할 경우 master branch는 외부의 가져다 쓸 사람들을 위한 안정된 버전의 branch가 되고 개발자는 각각 자신이 구현하고자 하는 목적에 맞게 branch를 만들어 개발하고 개발이 완료되면 master branch로 Pull Request를 요청하여 합치는 것이 가능해집니다.

이제 이에 대해서 실습해보기로 하겠습니다.
1. network 기능을 구현하기 위한 브랜치 생성
1. master branch에서 network branch로 변경(switch)
1. Network.php 파일을 생성, 스테이징, 커밋, 원격저장소로 푸시
1. 깃허브 사이트에서 network branch에서 master branch로 Pull Request(PR) 작성
1. master branch 관리자 입장에서 요청된 Pull Request(PR) 처리

### 4.2 새 Branch 만들기

현재 어떤 Branch가 만들어져있는지 확인하기 위해서는 다음과 같은 명령어를 실행합니다.

```cmd
git branch
```

![image](https://user-images.githubusercontent.com/1307187/56463185-a9564f80-6409-11e9-9b31-5b320f9ba094.png)

현재 master branch만 존재하며 `*`표시가 앞에 있어 현재 master branch를 사용 중이라는 것을 알 수 있습니다. 기본적으로 repository를 생성하면 master branch가 기본 branch로 만들어지고 선택됩니다.

이제 network 이라는 기능을 추가하기 위한 network branch를 

```cmd
git branch network
git branch
```

![image](https://user-images.githubusercontent.com/1307187/56463229-d8b98c00-640a-11e9-8933-d98057caafef.png)

간단하게 branch를 생성할 수 있습니다. 하지만 생성했다고 해서 branch가 자동으로 변경되는 것이 아님에 주의합니다. 또한 생성할 때 선택되어있는 branch의 커밋 버전에서 branch가 갈라져 나온다는 점도 기억해 둡시다.

### Branch 변경하기
branch를 변경하기 위해서는 `git checkout 브랜치명` 명령을 사용합니다.

```cmd
git checkout network
git branch
```

![image](https://user-images.githubusercontent.com/1307187/56463235-11f1fc00-640b-11e9-9833-df7958640f96.png)


### Network.php 파일을 생성, 스테이징, 커밋, 원격저장소로 푸시

자, 이제 Network 기능을 구현한다고 가정하고 다음과 같이 Network.php 파일을 작성합니다.

```cmd
notepad Network.php
```

![image](https://user-images.githubusercontent.com/1307187/56463258-95abe880-640b-11e9-82d9-615cb03efdaa.png)


```php
<?php
   echo "PHP 서버 정보 확인";
   phpinfo();
?>
```

![image](https://user-images.githubusercontent.com/1307187/56463256-862c9f80-640b-11e9-921c-f1e990de60ba.png)

파일을 저장하고 스테이징, 커밋을 합니다. 

```cmd
git add Network.php
git commit -m "Network 기능 구현"
```

![image](https://user-images.githubusercontent.com/1307187/56463272-cc81fe80-640b-11e9-8b9e-23d9af3879e4.png)

이제 푸시를 합니다. 다만 주의할 점이 푸시를 할 branch가 master가 아니라 network임에 주의해야 합니다. 그러면 원격 저장소에도 network branch가 생성되어 커밋 내역들이 저장되게 됩니다.

```cmd
git push origin network
```

![image](https://user-images.githubusercontent.com/1307187/56463287-14088a80-640c-11e9-9d0b-fb47b242cc86.png)

### Network Branch의 Commit 내역을 Master Branch로 Pull Request 요청 만들기

깃허브 사이트에 `Code` 탭으로 가서 `Branch`를 network로 변경해줍니다.

![image](https://user-images.githubusercontent.com/1307187/56463301-5336db80-640c-11e9-8934-52467c055577.png)

network branch로 변경하면 master branch에 없었던 Network.hp 파일이 보이는 것을 알 수 있습니다.

![image](https://user-images.githubusercontent.com/1307187/56463310-706baa00-640c-11e9-9718-f2b8db6f7aa1.png)

이제 네트워크 기능 구현이 완료되었다고 가정하고 master branch로 완성된 코드를 반영하기 위한 Pull Request를 생성해보도록 하겠습니다. 
상단의 `Pull requests` 탭을 클릭한 후 `New pull request` 버튼을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56463320-b9bbf980-640c-11e9-9e9d-5b9ffb6a2977.png)

현재 브랜치 상황 등이 보이는 것을 알 수 있습니다. 현재 master -> master 로 표시되어있는데 우측 master를 network로 변경해줍니다.

![image](https://user-images.githubusercontent.com/1307187/56463330-e1ab5d00-640c-11e9-948a-6eee7cb01295.png)

그러면 아래와 같이 network에서 master branch로 반영할 수 있는 커밋 내역들이 나타납니다. 좌측 상단의 `Create pull request` 버튼을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56463337-1a4b3680-640d-11e9-8e47-154296f6f30b.png)

그러면 아래처럼 Pull을 요청하는 메시지를 작성할 수 있으며 여기에 어떠한 기능을 구현 또는 어떠한 버그를 수정했으니 반영해달라는 내용의 글을 작성하고 `Create pull request`를 클릭합니다. master branch 담당자는 이 내용을 보고 받아들일지 고민하기 때문에 친절하게 작성하도록 합시다.

![image](https://user-images.githubusercontent.com/1307187/56463356-73b36580-640d-11e9-909c-f031cc9b1d51.png)

Pull Request을 작성해서 보냈습니다. 이제 master branch 담당자가 보고 받아들일지 판단할 것이며, 문제가 있다면 반려하고 어디를 고쳐서 다시 보내라는 등의 댓글을 달 것입니다. 만약 화면가 다르게 빨간색 메시지가 뜬다면 master branch 코드와 출동되는 부분이 있는 것으로 `git pull` 등을 사용해서 충돌되는 코드를 해결하고 다시 요청을 해야합니다. 이렇게 PR을 보내는 것을 `PR을 날렸으니(보냈으니) 받아달라'라는 표현을 사용하곤 합니다.

![image](https://user-images.githubusercontent.com/1307187/56463374-cdb42b00-640d-11e9-9041-e0dcc614b8fc.png)

### Pull Request 요청을 검토하고 받아줘서 Network Branch의 Commit 내역을 Master Branch로 적용하기
이제 master branch 담당자 입장에서 보도록 하겠습니다. 깃허브 사이트에 접속하면 Pull requests 탭에 숫자가 1이라고 표시된 것을 알 수 있습니다. `Pull requests` 탭을 클릭합니다.

![image](https://user-images.githubusercontent.com/1307187/56463395-529f4480-640e-11e9-9a86-71be388762b5.png)

어떤 고마운 사람이 네트워크 기능을 구현했다고 받아달라고 합니다. 해당 요청을 클릭해봅니다. 

![image](https://user-images.githubusercontent.com/1307187/56463399-719dd680-640e-11e9-8c44-18142920eb31.png)

이제 보내준 코드를 검토하고 문제가 없는지, 잘 동작하는지 확인해야 합니다. 별 문제가 없이 잘 돌아간다는 것을 확인했다면, 중간에 있는 `Merge pull reqeust`를 클릭하여 network에서 커밋 내역들을 master branch로 가져와서 반영합니다.

![image](https://user-images.githubusercontent.com/1307187/56463404-93975900-640e-11e9-879f-6b37c535d0c5.png)

여기서도 머지 커밋 메시지를 작성해 줍니다. 여기서는 기본 값으로 냅두고 `Confirm merge` 버튼을 클릭합니다.

 ![image](https://user-images.githubusercontent.com/1307187/56463416-d822f480-640e-11e9-9d03-b9cde131b089.png)

보라색으로 변하면서 머지가 완료되었습니다. Pull Request를 성공적으로 받아들였습니다.

![image](https://user-images.githubusercontent.com/1307187/56463431-0a345680-640f-11e9-8392-9999f58bf500.png)

### Github Commits 내역 확인하기

깃허브 `code` 탭을 클릭, master branch 인지 확인 후 `Commits`를 클릭하여 Network 기능이 구현되었는지 확인해봅니다. 잘 기능이 반영되었음을 알 수 있습니다.

![image](https://user-images.githubusercontent.com/1307187/56463452-6bf4c080-640f-11e9-8cf3-7f0b3f323540.png)

![image](https://user-images.githubusercontent.com/1307187/56463463-8fb80680-640f-11e9-81b8-ce4571b08e6a.png)

### Github의 Insights, Network 살펴보기

깃허브의 `Insights`탭, `Network` 메뉴로 들어가봅니다. 그러면 다음과 같이 branch가 나뉘어 있는 것을 알 수 있습니다.

![image](https://user-images.githubusercontent.com/1307187/56463468-be35e180-640f-11e9-8eb1-4b1dc834c344.png)

이후에도 계속 commit을 하고 pull request를 요청할 수 있습니다. 이렇게 하면 특정 기능 별로 개발해 나갈 수 있으서 Git을 유용하고 적절하게 사용할 수 있습니다.
