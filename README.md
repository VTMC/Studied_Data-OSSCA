# OpenStack
## 오픈스택에 대한 소개
오픈스택은 물리적인 네트워크 서버를 가상머신과 가상 네트워크로 만들고 관리하는 역할을 한다.<br>
오늘날의 OpenStack은 가상 머신 뿐아니라 베어메탈, 컨테이너까지 다룰 수 있는 클라우드 인프라의 기반이 되어가고 있다.<br>
## 오픈스택의 구성도
![image](https://user-images.githubusercontent.com/86049096/169686265-8ac66c8b-418a-4fb5-be11-4e6e0354660b.png)<br>
6개의 핵심 컴포넌트와 30개의 부가적인 컴포턴트로 이루어져있다.<br>
주 역할이 infrastructure를 만드는 역할이다보니 컴퓨팅/스토리지/네트워크/하드웨어가 핵심컴포넌트가 된다.<br>
오토스케일, 템플릿기반의 인스턴스 생성등을 지원하기 위한 orchestration 관련 컴포넌트 그리고 빌링 모니터링을 지원하기 위한 프로젝트들이 융합되어 서비스된다.<br>
## Upstream에서 오픈스택을 개발하는 방법
### Devstack
오픈스택 환경을 쉽게 구성해주는 도구로 오픈스택 개발자들의 개발 환경/테스트 환경으로 주로 쓰인다.<br>
[Devstack]:https://docs.openstack.org/devstack/latest/
### 코드 리뷰
오픈스택은 코드 리뷰로 Gerrit을 사용하며 CI도구로 ZuuL을 사용하고 있다.<br>
Core Contributor의 +2점수를 받으면 머지가 가능하다.<br>
![image](https://user-images.githubusercontent.com/86049096/169687579-499152d9-087d-4248-bf73-f709f646e4f8.png)<br>
[Gerrit]:https://review.opendev.org
### 이슈 관리
ubuntu에서 사용하는 launchpad를 사용하여 관리하다가 최근에 storyboard로 이전중이다.<br>
![image](https://user-images.githubusercontent.com/86049096/169687604-9c3a2288-1659-4953-a57c-cd7226eedcb2.png)<br>
![image](https://user-images.githubusercontent.com/86049096/169687614-722270b0-3e93-4745-a041-288d3afcb451.png)
### 회의록 / 의견 공유
오픈스택 커뮤니티에서 논의되는 모든 내용은 etherpad에 기록하고 공개한다.<br>
![image](https://user-images.githubusercontent.com/86049096/169687621-e5af6d0e-919c-4527-a93f-29f9d593e181.png)
### PTG(Project Team Gathering)
6개월마다 오픈스택 개발자들이 팀별로 모여 다음 릴리즈에 포함될 안건을 논의하는 기간이다.<br>
![image](https://user-images.githubusercontent.com/86049096/169686678-c6bf5ca1-1dfd-4a84-a08b-10a3f5540bb8.png)
### IRC / Mailing List
상시 대화 채널로 IRC를 사용한다.<br>
![image](https://user-images.githubusercontent.com/86049096/169686720-26a69d07-7c12-4d46-b96d-c754690af31b.png)<br>
OpenStack-discuss Mailing List를 통해 오픈스택의 모든 내용을 공유하고 기록한다.<br>
IRC의 지난 내용도 모두 기록하며 누구나 논의 기록을 되돌아 볼 수 있다.<br>
![image](https://user-images.githubusercontent.com/86049096/169686741-c95e62ab-6bfb-48a3-994f-3898d68191dd.png)
## 오픈스택 실습
아이피를 받아 오픈스택에 로그인한다.<br>
![image](https://user-images.githubusercontent.com/86049096/169688377-b000947e-f533-45cc-872c-3206f0e0e1d0.png)<br>
로그인하면 사용하고 있는 인스턴스의 개요를 보여주는 페이지가 나온다.<br>
![image](https://user-images.githubusercontent.com/86049096/169688465-97a82dfa-2786-4741-b279-6ac0dccf1b2b.png)<br>
인스턴스를 누르면 사용하고 있는 인스턴스들의 자세한 정보가 나타난다.<br>
![image](https://user-images.githubusercontent.com/86049096/169688550-2c25d1e3-aea2-4d78-bb66-c6d4a539407d.png)<br>
네트워크를 누르면 연결되어 있는 상태를 볼 수 있다.<br>
![image](https://user-images.githubusercontent.com/86049096/169688619-aba5ec61-fb6e-4ae8-8093-8a3ee44f4518.png)<br>
## 오픈스택 코드 분석
코드 분석을 위한 환경구성은 아래 URL을 참고한다.<br>
[참조]:https://docs.google.com/document/d/19j2D0ttj9U9mR5Z-O6kEb6xFlaslQJIkph8XtBI-AGY/edit?usp=sharing <br>
### serverlist에 created추가하기
python-openstackclient의 setup.cfg파일에는 명령어에 따른 호출 함수들이 적혀있는데 109행을 보면 
### configuration show --mask의 버그 고치기
  매개변수에 configuration show를 넣고 실행하면 다음과 같은 화면이 나온다.<br>
  ```
  +---------------------------------------------+-------------------------------+  
  | Field                                       | Value                         |  
  +---------------------------------------------+-------------------------------+  
  | additional_user_agent                       | [('osc-lib', '2.6.0')]        |  
  | api_timeout                                 | None                          |  
  | auth.project_domain_id                      | default                       |  
  | auth.project_name                           | demo                          |  
  | auth.user_domain_id                         | default                       |  
  | auth_type                                   | password                      |  
  | auth_url                                    | http://211.42.154.85/identity |  
  | baremetal_introspection_status_code_retries | 5                             |  
  | baremetal_status_code_retries               | 5                             |  
  | beta_command                                | False                         |  
  | cacert                                      | None                          |  
  | cert                                        | None                          |  
  | default_domain                              | default                       |  
  | deferred_help                               | False                         |  
  | disable_vendor_agent                        | {}                            |  
  | floating_ip_source                          | neutron                       |  
  | identity_api_version                        | 3                             |  
  | image_api_use_tasks                         | False                         |  
  | image_format                                | qcow2                         |  
  | image_status_code_retries                   | 5                             |  
  | interface                                   | public                        |  
  | key                                         | None                          |  
  | message                                     |                               |  
  | network_api_version                         | 2                             |  
  | networks                                    | []                            |  
  | object_store_api_version                    | 1                             |  
  | password                                    | secret                        |  
  | region_name                                 | RegionOne                     |  
  | secgroup_source                             | neutron                       |  
  | status                                      | active                        |  
  | timing                                      | False                         |  
  | username                                    | admin                         |  
  | verbose_level                               | 1                             |  
  | verify                                      | True                          |  
  | volume_api_version                          | 3                             |  
  +---------------------------------------------+-------------------------------+  
  ```
  출력화면을 보면 password가 secret이라고 적혀있는데 원래는 <redated>라고 마스킹되어 출력되어야 하는 항목이다.<br>
  따라서 현재 프로그램의 마스킹하는 부분에 버그가 있어 제대로 역할을 수행하지 못하는 모습이다.<br>
  코드를 따라가면 python-openstackclient\setup.cfg파일의 42행~53행에서 configuration show가 openstackclient.common의 configuration을 호출하는 모습을 볼 수 있다.<br>
  ```
  configuration_show = openstackclient.common.configuration:ShowConfiguration
  ```
  configuration.py파일의 21행에 REDACTED는 마스킹이 되었을 경우 변수를,
  ```
  REDACTED = "<redacted>"
  ```
  52행의 secret_opts는 마스킹이 되어야하는 항목을 나타낸다.
  ```
  secret_opts = ["password", "token"]
  ```
  configuration show 다음으로 위치하는 부분에 --unmask가 올 경우에는 parsed_arg.mask가 0이 되는 것으로 1이 되는 경우에 마스킹을 한다고 유추할 수 있다.<br>
  따라서 마스킹을 하는 역할을 하는 코드를 다음과 같이 추가할 수 있다.<br>
  ```
  if parsed_args.mask:
    for secret_opt in secret_opts:
        if secret_opt in info:
            info[secret_opt] = REDACTED
  ```
  이후 매개변수에 configuration show나 configuration show --unmask를 넣은 후 실행하면 정상적으로 수행하는 모습을 볼 수 있다.<br>
  ```
+---------------------------------------------+-------------------------------+
| Field                                       | Value                         |
+---------------------------------------------+-------------------------------+
| additional_user_agent                       | [('osc-lib', '2.6.0')]        |
| api_timeout                                 | None                          |
| auth.project_domain_id                      | default                       |
| auth.project_name                           | demo                          |
| auth.user_domain_id                         | default                       |
| auth_type                                   | password                      |
| auth_url                                    | http://211.42.154.85/identity |
| baremetal_introspection_status_code_retries | 5                             |
| baremetal_status_code_retries               | 5                             |
| beta_command                                | False                         |
| cacert                                      | None                          |
| cert                                        | None                          |
| default_domain                              | default                       |
| deferred_help                               | False                         |
| disable_vendor_agent                        | {}                            |
| floating_ip_source                          | neutron                       |
| identity_api_version                        | 3                             |
| image_api_use_tasks                         | False                         |
| image_format                                | qcow2                         |
| image_status_code_retries                   | 5                             |
| interface                                   | public                        |
| key                                         | None                          |
| message                                     |                               |
| network_api_version                         | 2                             |
| networks                                    | []                            |
| object_store_api_version                    | 1                             |
| password                                    | <redacted>                    |
| region_name                                 | RegionOne                     |
| secgroup_source                             | neutron                       |
| status                                      | active                        |
| timing                                      | False                         |
| username                                    | admin                         |
| verbose_level                               | 1                             |
| verify                                      | True                          |
| volume_api_version                          | 3                             |
+---------------------------------------------+-------------------------------+
  ```
