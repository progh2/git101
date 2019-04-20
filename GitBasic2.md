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

### git pull로 Remote Repository의 Commit 내역을 Local Repository로 가져오기

### git push로 Local Repository Commit 내역을 Remote Repository로 보내기

### Github에서 Commit 내역 살펴보기

### Github의 Insights, Network 살펴보기


## 2. 서로 같은 파일의 다른 영역 수정하기
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


