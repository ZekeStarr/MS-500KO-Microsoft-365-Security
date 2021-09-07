# 모듈 2 - 랩 1 - 연습 1 - 조직의 ID 동기화 설정 

이 연습에서는 Adatum Corporation의 보안 관리자인 Holly Dickson의 역할을 맡아 가상화된 랩 환경에 배포되어 있는 Microsoft 365를 사용합니다. 이 랩에서는 Microsoft 365 테넌트 계정과 로컬 Active Directory 계정 간의 ID 동기화를 구현합니다.

### 작업 1 - UPN 접미사 구성

1.	LON-DC1에서 **Adatum\Administrator**와 랩 호스팅 공급자가 할당한 암호를 사용하여 로그인합니다.
2.	관리자 권한으로 Windows PowerShell을 사용하여 도메인의 UPN 접미사, 그리고 AD DS의 모든 사용자 UPN을 업데이트합니다. 도메인 이름으로는 "@zzzzzzz.onmicrosoft.com"을 적용합니다(여기서 zzzzzzz는 고유한 UPN 이름). 이렇게 하려면 다음 명령을 실행합니다(zzzzzzz는 고유한 UPN 이름으로 변경해야 함).

    	Set-ADForest -identity "adatum.com" -UPNSuffixes @{replace="zzzzzzz.onmicrosoft.com"}  
3.	이제 다음 명령을 입력합니다(zzzzzzz는 고유한 UPN 이름으로 변경해야 함). 

		Get-ADUser –Filter * -Properties SamAccountName | ForEach-Object { Set-ADUser $_ -UserPrincipalName ($_.SamAccountName + "@zzzzzzz.onmicrosoft.com" )}
4.	Windows PowerShell 프롬프트에서 다음 명령을 입력하고 Enter 키를 누릅니다.

		Set-ExecutionPolicy Unrestricted  
5.	실행 정책 변경을 확인하려면 **A**를 입력하여 모두 예를 선택하고 Enter 키를 누릅니다.
 
### 작업 2 - 디렉터리 동기화를 사용하도록 설정

1.	브라우저를 열고 `https://portal.office.com/`으로 이동합니다.   
2.	**holly@M365xZZZZZZ.onmicrosoft.com**(암호 `Pa55w.rd`)으로 로그인합니다.    
3.	**관리**를 클릭하여 Microsoft 365 관리 센터로 이동합니다.
4.	**관리자 연락처 정보 업데이트** 여부를 묻는 메시지가 표시되면 취소 단추를 클릭하여 해당 요청을 건너뜁니다.  
	**참고:** Active Directory 동기화를 활성화하는 중이라는 경고가 표시되면 일단은 무시해도 됩니다. 하지만 이렇게 하면 이 연습 뒷분에서 디렉터리 동기화를 실행할 수 없습니다. 즉, 디렉터리 동기화가 활성화될 때까지 기다려야 합니다. 그러나 경고 메시지가 표시되더라도 다음 단계는 완료할 수 있습니다.  
5.	왼쪽 탐색 영역에서 **사용자** 아이콘을 선택하고 **활성 사용자**를 선택합니다. 그런 다음 위쪽 메뉴에서 줄임표를 클릭하고 **디렉터리 동기화**를 선택합니다.   
6.	**다운로드 센터로 이동하여 Azure AD Connect 도구 받기**를 클릭합니다.   메시지가 표시되면 도구를 다운로드하여 실행합니다.
    
### 작업 3 - Azure AD Connect 실행

1.	Microsoft Azure Active Directory Connect 설치 마법사의 단계를 진행합니다. 
2.	사용 조건과 개인정보취급방침에 동의합니다.
3.	**빠른 설정 사용**을 클릭합니다.   
4.	**Azure AD에 연결** 화면에서 Office 365 관리 사용자 이름인 
**holly@M365xZZZZZZ.onmicrosoft.com**과 암호 `Pa55w.rd`를 입력하고 다음을 클릭합니다.   
5.	**AD DS에 연결** 화면에서 도메인 관리자 **ADATUM\Administrator**와 암호 `Pa55w.rd`를 입력하고 **다음**을 선택합니다.   
6.	**모든 UPN 접미사를 확인된 도메인에 일치시키지 않고 계속** 체크박스를 선택합니다. Azure AD 로그인 구성 화면에서 **다음**을 선택합니다.   
7.	**구성 준비 완료** 화면에서 **구성이 완료되면 동기화 프로세스를 시작합니다.** 체크박스에 선택 표시가 있는지 확인하고 **설치**를 선택합니다.   
8.	설치가 완료될 때까지 기다립니다(몇 분 정도 걸릴 수 있음).   
9.	**끝내기**를 선택합니다.   

### 작업 4 - 디렉터리 동기화 결과 유효성 검사 및 사용자에게 라이선스 할당 

1.	새로 만든 사용자를 확인하려면 브라우저의 주소 표시줄에 `https://portal.office.com`을 입력하여 브라우저에서 Office 365 관리 센터를 엽니다.  
2.	다음 자격 증명을 사용하여 Holly Dickson으로 로그인합니다.  사용자 이름: **holly@M365xZZZZZZ.onmicrosoft.com**, 암호: `Pa55w.rd`  
3.	**활성 사용자**로 이동합니다.  
4.	이제 로컬 Active Directory에서 동기화된 사용자 수를 확인할 수 있습니다.  새로 고침 단추를 클릭하여 페이지의 데이터를 업데이트해야 할 수도 있습니다.  Abbie Parsons를 선택합니다.  Abbie는 동기화 전에는 AD DS 도메인에만 포함되어 있었던 사용자입니다. 
5.	다음과 같이 Abbie Parsons의 제품 라이선스를 업데이트합니다. 
	- 위치 = 영국
	- 제품 라이선스 = Enterprise Mobility + Security E5
6.	**변경 내용 저장**을 클릭하여 변경 내용을 적용합니다. 창을 닫습니다.

로컬 ADATUM 사용자를 Office 365에 동기화했으며 동기화된 사용자인 Abbie Parsons에게 라이선스를 할당했습니다.

# 랩 종료  

 
