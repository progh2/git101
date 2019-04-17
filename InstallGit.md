# Git 설치하기
## 소개
Git은 리눅스 커널은 만든 개발자로 유명한 `리누스 토발즈`가 만든 분산형버전관리시스템(DVCS:Distributed Version Control Systems)으로 프로그램의 버전 관리 및 협업을 쉽게 할 수 있도록 도와주는 개발에 있어서 빼놓을 수 없는 유용한 도구입니다. 자세한 설명 및 원리는 [생활코딩 이공잉님의 지옥에서 온 Git](https://opentutorials.org/course/2708) 강의를 보실 것을 추천드립니다.

> ![image](https://user-images.githubusercontent.com/1307187/56108814-b8ac4780-5f88-11e9-9a47-28f46d0ea755.png)
> 리눅스 토발즈(Linus Torvalds) 🥇 

> [Linus Torvalds를 집 근처에서 만나다...](https://kldp.org/node/96360)  <-- 읽어보세요. 😀 

## 설치 파일 다운로드
> ![image](https://user-images.githubusercontent.com/1307187/56108664-04aabc80-5f88-11e9-9b97-cafa14c24221.png)
> [Git 공식 사이트](https://git-scm.com/) 로 들어가서 Git 설치 파일을 다운로드 합니다. 사이트에 접속하면 브라우져 정보를 통해서 사용하는 운영체제 버전에 맞는 설치 파일을 바로 다운로드 할 수 있도록 우측에 링크가 준비되어 있습니다. `Download x.x.x for ***` 버튼을 클릭하여 다운로드 하도록 합니다. 
> Git 공식 홈페이지 : https://git-scm.com/  🎁 

> ![image](https://user-images.githubusercontent.com/1307187/56108895-222c5600-5f89-11e9-8f6b-e3db5edbfb96.png)
> 버튼을 클릭하면 위 화면으로 넘어가면서 자동적으로 파일 다운로드가 시작됩니다. 만약 다운로드가 진행이 되지 않는다면 `click here` 링크를 클릭하면 다운로드가 됩니다. 화면에 보면 `Git for Windows Portable` 이란 단어가 있는데, `Portable`은 `휴대용의`란 의미로 가지고 다닐 수 있다는 뜻입니다. 또한 바로 뒤이어서 나오는 `thumbdrive` 라는 표현이 나오는데, 우리가 흔히 생각하는 `USB 드라이브` 또는 `USB Memory`를 의미하는 것으로 외국에서는 `USB 드라이브`라는 말을 사용하지 않습니다. 만약 여러분이 Git 사용 매니아라서 설치 없이도 항상 USB에 git을 넣고 다니면서 사용하고 싶다면 이 포터블 버전을 다운받아서 여러분의 USB에 넣어두고 사용하면 됩니다. 💘 📝 

## 설치하기 
> ![image](https://user-images.githubusercontent.com/1307187/56109109-13926e80-5f8a-11e9-90bf-fa77a7ea4a65.png)
> 자, 이제 Git을 설치하기 위해 설치 파일을 `우측 마우스 클릭`하여 나오는 `컨텍스트 메뉴`에서 `관리자 권한으로 실행`을 클릭하여 실행해줍니다. 그냥 실행해도 되지만 그러면 화면이 껌뻑이면서 관리자 권한이 필요하다는 화면이 나타날 것입니다. 그런 경우에는 `예`를 클릭해줍니다. 

> ![image](https://user-images.githubusercontent.com/1307187/56109175-3755b480-5f8a-11e9-987c-5a915e5aa6e2.png)
>  설치 첫 화면입니다. 이 프로그램은 GNU 라이센스를 사용한다는 내용이 나옵니다.GNU 라이센스는 알아두면 훌륭한 라이센스로 관심있는 사람은 아래 링크로 들어가서 관련 문서들을 읽어봅시다. `Next`를 누릅니다.
> *  [성당과 시장](https://wiki.kldp.org/wiki.php/DocbookSgml/Cathedral-Bazaar-TRANS)
> * [GNU 라이센스 검색 글 목록들](https://www.google.com/search?q=GNU+%EB%9D%BC%EC%9D%B4%EC%84%BC%EC%8A%A4&rlz=1C1NHXL_koKR839KR839&oq=GNU+%EB%9D%BC%EC%9D%B4%EC%84%BC%EC%8A%A4&aqs=chrome..69i57.1458j0j1&sourceid=chrome&ie=UTF-8)

> ![image](https://user-images.githubusercontent.com/1307187/56109228-99161e80-5f8a-11e9-932a-feeace6d864c.png)
> Git 설치 옵션이 나타납니다. 특별히 수정할 것이 없다면 기본 선택된 것으로 냅두고 `Next`를 누릅니다.
>
> **옵션 설명**
> * Additional icons - 추가 아이콘 (바탕화면 등) 여부
> * Windows Explorer integration - 윈도우 파일탐색기의 컨텍스트 메뉴(오른쪽 마우스 클릭) 추가 여부
> * Git LFS(Large File Support) - 대용량 파일 지원 여부
> * Associate .git* configuration files with default text editor - .git으로 시작하는 설정 파일들을 기본 문서 편집기로 연결할지 여부
> * Associate .sh files to be run with Bash - .sh 확장자를 가진 파일을 깃과 같이 설치되는 Bash쉘로 연결할지 여부 
> * Use a True Type font in all console windows - 트루타입 판토를 모든 콘솔창에서 사용할지 여부
> * Check daily for Git for Windows updates - 매일 윈도우용 Git 업데이트를 확인할지 여부

> ![image](https://user-images.githubusercontent.com/1307187/56109234-9e736900-5f8a-11e9-94d2-5a8185e6d212.png)
> Git에서 설정파일 수정이나 메시지 등을 작성할 때 사용할 기본 문서편집기(에디터)를 선택합니다. 전통적으로 Vim 에디터가 선택되어 있습니다. Visual Studio Code 등이 설치되어 있다면 변경할 수 있습니다. 여기서는 기본 값으로 두고 `Next`를 누릅니다.

> ![image](https://user-images.githubusercontent.com/1307187/56109244-a6cba400-5f8a-11e9-8be8-1d8163160f30.png)
> HTTPS 연결을 할 때 사용할 라이브러리를 선택합니다. 기본 값으로 두고 `Next`를 누릅니다.

> ![image](https://user-images.githubusercontent.com/1307187/56109249-aaf7c180-5f8a-11e9-8f7b-6b531dd07b08.png)
> 행의 끝문자(개행문자) 변환에 대해서 설정합니다. 체크아웃 할 때는 윈도우 스타일로, 커밋 할 때는 유닉스 스타일 개행문자로 저장하는 방식이 기본 값으로 선택되어 있습니다. `Next`를 누릅니다.

> ![image](https://user-images.githubusercontent.com/1307187/56109256-ae8b4880-5f8a-11e9-9de9-b3a49b3a9400.png)
> Git Bash에서 사용할 터미널 에뮬레이터를 선택합니다. MinTTY가 기본 터미널로 선택되어 있습니다. `Next`를 누릅니다.

> ![image](https://user-images.githubusercontent.com/1307187/56109259-b21ecf80-5f8a-11e9-84b9-039e3a2d25f6.png)
> Git 추가 옵션을 설정합니다. `Next`를 누릅니다.
>
> ** 옵션 설명 **
> * Enable file system caching - 성능향상을 위해 캐시 사용
> * Enable Git Credential Manager - 인증을 위하여 Git Credential Manager for Windows 사용
> * Enable symbolic links - 심볼릭 링크 사용

> ![image](https://user-images.githubusercontent.com/1307187/56109293-e1354100-5f8a-11e9-9ca9-071237735189.png)
> 설치가 완료되었습니다. 이렇게 설치나 설정을 도와주는 프로그램을 ~~Wizard(마법사/도우미)라고 이름을 붙이곤 합니다. 릴리즈 노트를 보고싶지 않다면 체크를 해제합니다. `Finish` 버튼을 누릅니다.
>
> **옵션 설명**
> * Launch Git Bash - 설치 프로그램 종료 후 Git Bash를 실행합니다. Git Bash는 윈도우에서 리눅스의 배시쉘과 Git을 쓸 수 있도록 해주는 프로그램입니다. 윈도우 터미널 대신 사용할 수 있으며 많은 윈도에서 사용할 수 없는 기본 리눅스 명령어를 사용할 수 있습니다.
> * View Release Notes - 프로그램을 만들고 배포(릴리즈) 할 때는 해당 버전의 특징, 한계, 주의점 등등의 내용을 담고있는 파일을 같이 포함하곤 합니다. 이번에 설치한 Git의 버전에 해당하는 릴리즈 노트를 엽니다.

Git 설치가 완료되었습니다.

