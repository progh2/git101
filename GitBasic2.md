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

### Local Repository에 파일 수정히기

### Local Repository에서 파일 푸시하기(1)

### git pull로 Remote Repository의 Commit 내역을 Local Repository로 가져오기

### git push로 Local Repository Commit 내역을 Remote Repository로 보내기

### Github에서 Commit 내역 살펴보기

### Github의 Insights, Network 살펴보기


## 3. 서로 같은 파일 같은 영역 수정하기
### Remote Repository에 파일 수정하기 

### Local Repository에 파일 수정히기

### Local Repository에서 파일 푸시하기(1)

### git pull로 Remote Repository의 Commit 내역을 Local Repository로 가져오기

### 충돌 내용 해결하기

### git push로 Local Repository Commit 내역을 Remote Repository로 보내기

### Github에서 Commit 내역 살펴보기

### Github의 Insights, Network 살펴보기



## 4. Branch 생성해서 각자 개발, Pull Request 보내서 합치기
### 4.1 하나의 브랜치를 사용해서 공동 개발할 경우 한계

#### 두 명이서 각각 개발하는경우 

#### 프로젝트를 가져다 쓰고 싶어하는 사용자의 경우

### 4.2 새 Branch 만들기

```cmd
git branch
```

```cmd
git branch network
```

```cmd
git branch
```


### Branch 변경하기
```cmd
git branch 
```


```cmd
git checkout network
```


```cmd
git branch
```


### Branch로 Commit, Push 하기

```cmd
notepad Network.php
```

```php
<?php
   echo "PHP 서버 정보 확인";
   phpinfo();
?>
```

```cmd
git add Network.php
git commit -m "Network 기능 구현"
git push origin network
```


### Network Branch의 Commit 내역을 Master Branch로 Pull Request 요청 만들기

### Pull Request 요청을 검토하고 받아줘서 Network Branch의 Commit 내역을 Master Branch로 적용하기

### Github Commits 내역 확인하기

### Github의 Insights, Network 살펴보기


