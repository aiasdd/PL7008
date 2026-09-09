---
layout: default
toc: true
lab:
  title: ILT 설정
  module: 소개
  description: 이 실습에서는 Microsoft Copilot Studio 포털에 액세스하고, 이후 실습 전반에서 사용할 환경 및 솔루션을 만듭니다.
  duration: 10분
  level: 200
  islab: true
  primarytopics:
    - Microsoft Copilot
    - Microsoft Copilot Studio
---

# 실습 환경 준비

## 실습 개요
Microsoft Copilot Studio 포털에 액세스하고, 이후 실습 전반에서 사용할 환경 및 솔루션을 만듭니다.

> [!IMPORTANT]
> 본 과정은 클래식 Copilot Studio 환경을 사용합니다 Copilot Studio 화면이 이 미션의 스크린샷과 다르게 보인다면, 오른쪽 위의 **새 환경(New Experience)** 를 꺼서 여기서 사용하는 **클래식 환경(classic experience)** 로 전환합니다.

### 실습 중 접속 URL

| 서비스/용도 | URL | 비고 |
|---|---|---|
| Power Platform 관리 센터 | [https://admin.powerplatform.microsoft.com/manage/environments](https://admin.powerplatform.microsoft.com/manage/environments) | 실습 환경 생성 및 관리 |
| Microsoft Copilot Studio | [https://copilotstudio.microsoft.com/](https://copilotstudio.microsoft.com/) | 에이전트 생성 및 관리 |
| Power Apps Maker Portal | [https://make.powerapps.com/](https://make.powerapps.com/) | Dataverse 테이블 생성 및 관리 |
| Microsoft Teams 웹 | [https://teams.cloud.microsoft/](https://teams.cloud.microsoft/) | 게시된 에이전트 및 워크플로 테스트 |
| 복지로 | [https://www.bokjiro.go.kr](https://www.bokjiro.go.kr) | 공개 웹 사이트 지식 소스 등록 |
| 국세법령정보시스템 | [https://taxlaw.nts.go.kr/](https://taxlaw.nts.go.kr/) | 공개 웹 사이트 지식 소스 등록 |

### 실습 파일 다운로드
- 실습 03 지식 관리:[경비처리 가이드](//Instructions/Labfiles/경비처리_가이드.docx) 
- 실습 03 경비 청구 테이블: [경비청구 테이블](//Instructions/Labfiles/경비청구_테이블.xlsx)

## 실습 1 - Power Platform 환경 만들기

### 작업 1.1 - Power Platform 관리 센터


실습을 시작하기 전에, 작업할 개발 환경을 만들어야 합니다.

1.  웹 브라우저를 열고 [https://admin.powerplatform.microsoft.com/manage/environments](https://admin.powerplatform.microsoft.com/manage/environments) 로 이동한 후 이 실습용 자격 증명으로 로그인합니다. 
2. 표시되는 팝업 메시지는 모두 닫습니다.
3. **환경** 페이지에서 환경을 생성합니다.

1. **+ 새로 만들기**를 선택하여 다음 설정으로 새 환경을 생성합니다:
   - **유형**: Developer
   - **지역**: **대한민국**
   - **Name**: *Student00_env* (이름 자유롭게 변경하여 입력합니다.)
   ![alt text](../../Allfiles/image-21.png)

2. **다음**을 선택합니다.

3. 다음 설정을 입력합니다:
   - **언어**: 한국어(대한민국)
   - **통화**: KRW
   - **샘플 앱 및 데이터 배포**: 예
   ![alt text](../../Allfiles/image-22.png)

4. **저장**을 선택하고 환경 상태가 **준비**가 될 때까지 기다립니다(화면 갱신을 위해 **Refresh** 버튼을 사용할 수 있습니다).
   > [!NOTE]
   > 테넌트 구성에 따라 환경 프로비저닝에는 몇 분이 소요될 수 있습니다.

   Power Platform 관리 센터에서 환경이 생성되었습니다.
   ![alt text](../../Allfiles/image-23.png)

### 작업 1.2 - 사용자 추가
1. 생성한 **환경** 을 클릭합니다.
   ![alt text](image-1.png)

2. **액세스** 하위의 **사용자:** **모두보기** 를 클릭합니다.
   ![alt text](image-2.png)

1. **+ 사용자 추가**를 클릭하여 나타나는 사용자 추가 화면에서 사용자 정보를 검색 후 선택합니다.
   ![alt text](image-3.png)
   **추가** 합니다.
   ![alt text](image-4.png)

1. 추가가 완료되면 보안 역할 관리 화면에서 **Environment Maker** 와 **Basic User** 역할을 선택하고 **저장** 을 클릭합니다.
   ![alt text](image-5.png)
   ![alt text](image-6.png)
   
   이 과정을 반복하여 사용자를 추가합니다.
   사용자에게 정상적으로 환경에 권한이 추가된 경우, [Copilot Studio](https://copilotstudio.microsoft.com/) 페이지에 접속 시 해당 환경이 **지원 환경** 하위에 표시됩니다.
   ![alt text](image-7.png)

### 작업 1.3 - 솔루션 만들기

1. Copilot Studio [https://copilotstudio.microsoft.com/](https://copilotstudio.microsoft.com/) 페이지 오른쪽 상단의 **환경 선택** 사용해 환경을 생성된 환경(Student00_env)로 전환합니다. 

   ![alt text](../../Allfiles/image-24.png)

1. 왼쪽 탐색 창에서 줄임표(**...**)를 선택한 다음 **솔루션**을 선택합니다.
   ![alt text](../../Allfiles/image-25.png)

1. *Default Solution* 및 *Common Data Services Default Solution*을 포함한 여러 솔루션이 표시되는지 확인합니다.

   ![alt text](../../Allfiles/image-26.png)

1. **+ 새 솔루션**을 선택합니다.

1. **표시 이름** 텍스트 상자에 `Lab Exercises`를 입력합니다.

1. **이름** 이 자동으로 채워졌는지 확인합니다.

1. **게시자** 드롭다운 아래의 **+ 새 게시자** 를 선택합니다.

1. **표시 이름**에 `Fabrikam`을 입력합니다.

1. **이름**에 `fabrikam`을 입력합니다.

1. **접두사**에 `fab`를 입력합니다.

   ![alt text](../../Allfiles/image-27.png)

1. **저장**를 선택합니다.

1. **게시자** 드롭다운에서 **Fabrikam (fabrikam)** 이 선택되어 있는지 확인합니다.

1. **선호하는 솔루션으로 설정** 체크박스를 선택합니다.

   > [!NOTE]
   > 이를 선호 솔루션으로 설정하면 이후 실습에서 만드는 새 자산이 기본적으로 Lab Exercises 솔루션에 추가됩니다.

   ![alt text](../../Allfiles/image-28.png)

1. **만들기**를 선택합니다.

1. **솔루션** 이 생성된것을 확인하고 뒤로 가기를 클릭하여 솔루션 화면으로 이동합니다.
![alt text](../../Allfiles/image-29.png)

1. 생성된 솔루션을 다시 한번 확인하고 브라우저를 닫습니다. 
![alt text](../../Allfiles/image-30.png)

1. **Copilot Studio** 페이지를 새로 고칩니다.
이제 작업에 사용할 Power Platform 환경과 솔루션이 준비되었습니다.

## 실습 2 - Dataverse에 테이블 만들기 
Lab03: Copilot Studio 에이전트에서 지식 관리에서 지식 소스로 사용합니다.
이 실습에서는 에이전트의 지식 소스로 사용할 Dataverse 테이블을 만듭니다.

### 작업 2.1 - 비용 청구용 테이블 만들기

1. 웹 브라우저에서 [https://make.powerapps.com/](https://make.powerapps.com/)의 **Power Apps Maker portal**로 이동하고, 필요 시 로그인합니다. 환영 메시지는 건너뜁니다.

1. 페이지 상단에서 이 실습에 사용할 환경인지 확인합니다.

   ![alt text](../../Allfiles/image-129.png)

1. **Maker portal** 왼쪽 탐색 메뉴에서 **테이블**을 선택합니다.

1. **Copilot 시작** 타일을 선택합니다.
![alt text](../../Allfiles/image-130.png)

1. **Copilot 시작** 대화 상자에서 **테이블 옵션** 아이콘을 선택하고 **단일 테이블**을 선택합니다.

   ![alt text](../../Allfiles/image-131.png)

1. *Copilot으로 빌드하려는 테이블을 설명하세요....* 텍스트 상자에 다음 프롬프트를 입력합니다:

   ```prompt
   경비 청구 내역을 저장하고 처리하는 테이블로, 경비 제목, 경비 유형(숙박, 식사, 접대비 또는 교통비), 경비 발생일, 제출일, 승인일, 청구 금액, 승인 금액 및 경비 상태(제출됨, 검토 중, 승인됨, 거부됨)를 포함합니다.
   ```
   ![alt text](../../Allfiles/image-132.png)
1. **생성**을 선택합니다.
  
    > [!NOTE]
    > 생성된 테이블 스키마는 이 실습 스크린샷과 약간 다를 수 있습니다. 열 이름 또는 형식의 사소한 차이는 정상입니다.

1. 테이블이 생성됩니다. 테이블 이름을 메모해 둡니다.

   ![alt text](../../Allfiles/image-133.png)

1. **저장 후 종료**를 선택하고, 다시 **저장 후 종료**를 선택합니다.
![alt text](../../Allfiles/image-134.png)