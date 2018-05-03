---
layout: post
title: "chsh PAM authentication failed 오류시 해결 방법"
date: 2018-05-02 10:20:00
lang: ko
nav: post
category: Programing
tags: [zsh, ubuntu]
---

# chsh:PAM authentication failed 오류 발생시 해결방법


1. `$ sudo vim /etc/pam.d/chsh `
2. `auth required pam_shells.so` 주석처리
3. `sudo chsh $USER -s $(which zsh)`
4. 로그 아웃, 로그인


