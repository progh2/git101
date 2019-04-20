# Git으로 협업하기
 
## 1. 서로 다른 파일 추가, 수정하기
### Local Repository에 파일 추가히기

### Remote Repository에 파일 추가하기 

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


