# OpenStack
  # 오픈스택에 대한 소개
  오픈스택은 물리적인 네트워크 서버를 가상머신과 가상 네트워크로 만들고 관리하는 역할을 한다.  
  오늘날의 OpenStack은 가상 머신 뿐아니라 베어메탈, 컨테이너까지 다룰 수 있는 클라우드 인프라의 기반이 되어가고 있다.  
  # 오픈스택의 구성도
  ![image](https://user-images.githubusercontent.com/86049096/169686265-8ac66c8b-418a-4fb5-be11-4e6e0354660b.png)
  6개의 핵심 컴포넌트와 30개의 부가적인 컴포턴트로 이루어져있다.  
  주 역할이 infrastructure를 만드는 역할이다보니 컴퓨팅/스토리지/네트워크/하드웨어가 핵심컴포넌트가 된다.  
  오토스케일, 템플릿기반의 인스턴스 생성등을 지원하기 위한 orchestration 관련 컴포넌트 그리고 빌링 모니터링을 지원하기 위한 프로젝트들이 융합되어 서비스된다.  
  # Upstream에서 오픈스택을 개발하는 방법
  **Devstack**
    오픈스택 환경을 쉽게 구성해주는 도구로 오픈스택 개발자들의 개발 환경/테스트 환경으로 주로 쓰인다.  
    참조-https://docs.openstack.org/devstack/latest/
   **코드 리뷰**
    오픈스택은 코드 리뷰로 Gerrit을 사용하며 CI도구로 ZuuL을 사용하고 있다.  
    Core Contributor의 +2점수를 받으면 머지가 가능하다.  
    Gerrit-https://review.opendev.org
   **이슈 관리**
    ubuntu에서 사용하는 launchpad를 사용하여 관리하다가 최근에 storyboard로 이전중이다.  
   **회의록 / 의견 공유**
    오픈스택 커뮤니티에서 논의되는 모든 내용은 etherpad에 기록하고 공개한다.  
   **PTG(Project Team Gathering)**
    6개월마다 오픈스택 개발자들이 팀별로 모여 다음 릴리즈에 포함될 안건을 논의하는 기간이다.  
    ![image](https://user-images.githubusercontent.com/86049096/169686678-c6bf5ca1-1dfd-4a84-a08b-10a3f5540bb8.png)
   **IRC / Mailing List**
    상시 대화 채널로 IRC를 사용한다.  
    ![image](https://user-images.githubusercontent.com/86049096/169686720-26a69d07-7c12-4d46-b96d-c754690af31b.png)
    OpenStack-discuss Mailing List를 통해 오픈스택의 모든 내용을 공유하고 기록한다.  
    IRC의 지난 내용도 모두 기록하며 누구나 논의 기록을 되돌아 볼 수 있다.  
    ![image](https://user-images.githubusercontent.com/86049096/169686741-c95e62ab-6bfb-48a3-994f-3898d68191dd.png)
