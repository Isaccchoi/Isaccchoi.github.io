---
layout: post
title: "MacDown Terminal로 특정 파일 실행 시키기"
date: 2018-01-12 21:51:00
lang: en
nav: post
category: Programing
tags: [Markdown, MacDown]
---

# MacDown Terminal로 특정 파일 실행시키기

## Bash Command 추가

자기 bash환경에 맞춰서 엽니다.

**zsh 사용시**

```
>>> vi ~/.zshrc
```

**bash 사용시**

```
>>> vi ~/.bash_profile
```
하기 값을  입력합니다.

```bash

macdown() {
    "$(mdfind kMDItemCFBundleIdentifier=com.uranusjr.macdown | head -n1)/Contents/SharedSupport/bin/macdown" $@
}

```

> 참조 링크:[https://github.com/MacDownApp/macdown/issues/506#issuecomment-287744745](https://github.com/MacDownApp/macdown/issues/506#issuecomment-287744745)
