# 모듈 8 - 랩 1 - 연습 1 - 디바이스 관리를 사용하도록 설정


이 연습에서는 Adatum Corporation의 보안 관리자인 Holly Dickson의 역할을 맡아 가상화된 랩 환경에 배포되어 있는 Microsoft 365를 사용합니다. 이 랩에서는 Intune을 통해 사용자 디바이스를 관리합니다.

이 연습에서는 Adatum이 Enterprise Mobility + Security E5 제품을 설치했는지 확인합니다. 그런 다음 테스트 사용자 계정에 라이선스가 할당되었는지 확인하고, Holly Dickson에게 라이선스를 할당합니다.

### 작업 1: Enterprise Mobility + Security 라이선스 확인 및 할당

이 작업에서는 Adatum이 Enterprise Mobility + Security E5 제품을 설치했는지 여부와 사용 가능한 라이선스 수를 확인합니다. 그런 다음 테스트 사용자 계정에 라이선스가 할당되었는지 확인하고, Holly Dickson에게 라이선스를 할당합니다.

1. 클라이언트 1 VM(LON-CL1)에는 **lon-cl1\admin** 계정으로, Microsoft 365에는 Holly Dickson(**holly@M365xZZZZZZ.onmicrosoft.com**, 암호 **Pa55w.rd**)으로 로그인되어 있는 상태여야 합니다.

2. **Microsoft Edge**에는 **Microsoft 365 관리 센터** 탭이 열려 있어야 합니다. 해당 탭이 열려 있으면 지금 선택합니다. 해당 탭이 열려 있지 않으면 **https://portal.office.com**을 입력하고 **Holly**로 로그인한 후에 **Microsoft Office 홈** 페이지에서 **관리**를 선택합니다.

3. **Microsoft 365 관리 센터**의 왼쪽 탐색 창에서 **청구**를 선택하고 그 아래에서 **라이선스**를 선택합니다.

4. **라이선스** 페이지에서 **Enterprise Mobility + Security E5**를 선택합니다.

5. **Enterprise Mobility + Security E5** 페이지의 사용자 목록 아래에서 파일럿 팀 구성원인 **Alex Wilber**, **Joni Sherman**, **Lynne Robbins**와 **MOD 관리자**에게 각각 라이선스가 할당되어 있는지 확인합니다.

    **참고:** 이러한 사용자 계정은 Office 365 테넌트의 구성원으로 작성된 것입니다. 그리고 계정 작성 프로세스에서 각 계정에 Office 365 E5 라이선스와 Enterprise Mobility + Security E5 라이선스가 할당되었습니다.

6. Enterprise Mobility + Security E5 라이선스가 할당되지 않은 사용자는 전역 관리자인 Holly Dickson입니다. 이전 랩에서 Holly의 사용자 계정을 만들 때 Office 365 E5 라이선스만 할당하라는 지침이 제시되었을 수도 있습니다. 이제 Holly에게 Enterprise Mobility + Security E5 라이선스를 할당하겠습니다.  Holly에게 Enterprise Mobility + Security E5 라이선스가 이미 있는 경우에는 다음 작업으로 넘어가면 됩니다.

    Holly에게 라이선스를 할당하려면 **+라이선스 할당**을 선택합니다.

7. **사용자에게 라이선스 할당** 페이지에서 **이름 또는 전자 메일 주소 입력** 필드를 선택하고 사용자 목록이 표시되면 **Holly Dickson**을 선택합니다.

8. **할당**을 선택합니다.

9. **Holly Dickson 님에게 라이선스를 할당했습니다.** 창을 닫습니다.

10. 이 랩의 뒷부분에서 사용할 수 있도록 클라이언트 1 VM은 열어 둡니다.

테넌트에서 사용 가능한 Enterprise Mobility + Security E5 라이선스를 확인했으며 Holly에게 EMS E5 라이선스를 할당했습니다.



# 연습 2 계속 진행
