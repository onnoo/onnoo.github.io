---
title: "맥 파워포인트 수식 자동변환이 안될 때"
date: 2022-02-10
categories:
  - troubleshooting
tags:
  - powerpoint
  - mac
---

파워포인트 수식 작성 시 백슬래시 단축어가 자동 변환이 되지 않는 경우 해결 방법



파워포인트에서는 다음과 같이 텍스트 상자에 수식을 삽입할 수 있습니다.

<p align="center">
<img src="https://user-images.githubusercontent.com/29935117/153537205-f746a5c4-2fb8-4fd2-a69f-7ad8141f2293.png" style="zoom: 50%"/>
</p>


수식 안에 특수 기호를 입력하기 위해서는, 상단 수식 탭의 기호 팔레트에서 선택하여 넣거나 아래 예시와 같이 백슬래시와 함께 입력하는 방법이 있습니다.


<p align="center">
<img src="https://user-images.githubusercontent.com/29935117/153537512-0b464418-daf3-47c9-b986-a714e2b690a6.png" style="zoom: 50%; margin-left:" />
</p>



어느 순간, 맥 파워포인트에서 저 백슬래시를 자동으로 기호로 변환해 주지 않는 문제가 발생했습니다. 이 문제를 해결하기 위한 방법을 남겨두려고 합니다.



# 문제 상황

파워포인트 환경설정에서 자동 고침 옵션을 건드리면 수식에서 백슬래시 자동 변환이 동작하지 않습니다. 체크박스를 원래대로 돌려놓아도 해당 문제를 해결되지 않았습니다.

<p align="center">
<img src="https://user-images.githubusercontent.com/29935117/153539044-9e60bab3-a86a-4ae3-b7d3-c30fc487128b.png" style="zoom: 50%" />
</p>


# 해결 방법

파워포인트 Preference 설정을 초기화하는 방법으로 해결할 수 있었습니다. **자동 고침 옵션 외에 설정하신 부분이 있다면, 백업해두시는 것을 권장합니다.**

Preference 초기화를 위해 맥 터미널에서 다음 두 폴더를 삭제합니다.

```bash
rm -rf ~/Library/Containers/com.microsoft.Powerpoint
rm -rf ~/Library/Group\ Containers/UBF8T346G9.Office
```



이후 파워포인트 또는 오피스 프로그램을 실행 시 다음과 같이 초기화된 상태를 볼 수 있습니다.

<p align="center">
<img src="https://user-images.githubusercontent.com/29935117/153539641-00cd18be-f194-426f-8a64-269c50c90551.png" style="zoom: 50%" />
</p>
라이센스 확인 이후, 정상적으로 수식 자동 변환이 해결된 것을 확인합니다.

<p align="center">
<img src="https://user-images.githubusercontent.com/29935117/153540145-67f15b67-d968-405c-b88c-a7e2674acca7.png" style="zoom: 50%" />
</p>

## 참고

[https://answers.microsoft.com/en-us/msoffice/forum/all/symbol-replacement-in-powerpoint-2016-mac-equation/6623d873-62eb-403b-a0fc-472fb5fe2de3](https://answers.microsoft.com/en-us/msoffice/forum/all/symbol-replacement-in-powerpoint-2016-mac-equation/6623d873-62eb-403b-a0fc-472fb5fe2de3)
