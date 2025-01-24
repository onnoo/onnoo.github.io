---
title: "MacOS/Linux 터미널 추천 - Kitty"
date: 2025-01-10
categories:
  - utils
tags:
  - utils
  - kitty
---

- 탭 바(tab bar) 설정
```
tab_bar_edge top  # 상단에 배치
tab_bar_min_tabs 1
tab_bar_edge top
tab_bar_style powerline  # fade, slant, separator, powerline, custom, hidden
tab_powerline_style slanted  #  angled, slanted, round
tab_title_template {title}{' :{}:'.format(num_windows) if num_windows > 1 else ''}
```

- MacOS 단축키 등록 예시: https://github.com/kovidgoyal/kitty/issues/5509#issuecomment-1250575384
```
# 탭 이동
map cmd+1 goto_tab 1
map cmd+2 goto_tab 2
map cmd+3 goto_tab 3
map cmd+4 goto_tab 4

# 클립보드
map cmd+c        copy_to_clipboard 
map cmd+v        paste_from_clipboard
map shift+insert paste_from_clipboard
```

- ubuntu에서 기본 터미널로 설정하기 ([참고](https://github.com/kovidgoyal/kitty/discussions/5599#discussioncomment-3921574))
```
gsettings set org.gnome.desktop.default-applications.terminal exec 'kitty'
```
