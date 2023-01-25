---
title: "sed 명령어를 이용해서 개행 문자 치환하기"
date: 2023-01-25
categories:
  - utils
tags:
  - macos
---

Mac OS에서 sed 명령어를 이용해서 개행 문자 치환하기



옵시디언과 같은 텍스트 에디터로 편집한 문서를 github 마크다운으로 옮길 때, 개행 처리에 신경을 써야할 때가 있다. 개행을 위해서 명시적으로 스페이스 두 번 혹은 `<br>` 태그를 입력해야 한다.



이를 터미널 명령어를 이용하여 처리하고자 다음 명령어를 사용한다.

```bash
sed -e ':a' -e 'N' -e '$!ba' -e 's/\n/  \n/g' out.txt | pbcopy
```



`| pbcopy` 는 stdout을 자동으로 클립보드로 복사해 준다. 다른 문자열로 치환하려면 `'s/\n/{str}/g'` 부분을 수정하자.



출처 : https://stackoverflow.com/a/1252191
