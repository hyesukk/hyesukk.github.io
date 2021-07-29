---
title:  "개발 환경 설정하기"
excerpt: 개발 tools

categories:
  - 'dev_utils'
tags:
  - dev_utils  
  - setup

toc: true
toc_sticky: true

date: 2021-07-30
last_modified_at: 2021-07-30
---

* raspberry pi os format 후 세팅 기념ㅠㅠㅠㅠㅠ
* 필요 시, 추가 및 수정 예정...

# utils 

* vim
    + 이전 vim_settings 포스팅 [참고](https://hyesukk.github.io/dev_utils/vim_settings/)
* tmux
    + 세션 내 마우스 스크롤 기능
        - default : ctrl + b +[ 및 q
        - custom : ~/.tmux.conf

```
sudo apt-get install -y vim tmux
```

* tmux custom

```
vi ~/.tmux.conf

# 마우스 이용 가능
set -g mouse on
# 마우스 스크롤 사용하기
set -g terminal-overrides 'xterm*:smcup@:rmcup@'
```

# Configuration Management

* git과 tig 설치

* git 설정

```
sudo apt-get install -y git-all tig

git config --global user.name (hyesukk)
git config --global user.mail

# commit editor를 vim으로 변경

git config --global core.editor "vim"

# git commit message template

vi ~/.gitmessage.txt

----
[type] : [category] title

# 상세 내용은 아래에 작성


# ================================================
# git blog / coding test repo는 type 생략
# Type List
# new   : 신규 기능
# fix   : 버그
# style : 공백, 괄호, lint 등 코드랑 상관 없는 수정
# docs  : 문서
# test  : 테스트
# etc   : makefile 수정 / 3rdparty 추가 등
----

git config --global commit.template ~/.gitmessage.txt

```

* tig설정
    + ~/.tigrc 필요 시, 

# compile / build

* build-essential 설치 (gcc, g++, make, perl 등등)
    + gcc g++ 버전 업 (8.3 이라 변경 안함)

```
sudo apt-get install -y build-essential

dpkg -l 로 설치된 버전 확인 (gcc / g++)

pi@raspberrypi:~ $ gcc --version
gcc (Raspbian 8.3.0-6+rpi1) 8.3.0
Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

pi@raspberrypi:~ $ dpkg -l | grep gcc
ii  gcc                                    4:8.3.0-1+rpi2                          armhf        GNU C compiler
ii  gcc-4.9-base:armhf                     4.9.4-2+rpi1+b19                        armhf        GCC, the GNU Compiler Collection (base package)
ii  gcc-5-base:armhf                       5.5.0-8                                 armhf        GCC, the GNU Compiler Collection (base package)
ii  gcc-6-base:armhf                       6.5.0-1+rpi1+b1                         armhf        GCC, the GNU Compiler Collection (base package)
ii  gcc-7-base:armhf                       7.3.0-19                                armhf        GCC, the GNU Compiler Collection (base package)
ii  gcc-8                                  8.3.0-6+rpi1                            armhf        GNU C compiler
ii  gcc-8-base:armhf                       8.3.0-6+rpi1                            armhf        GCC, the GNU Compiler Collection (base package)
ii  libgcc-8-dev:armhf                     8.3.0-6+rpi1                            armhf        GCC support library (development files)
ii  libgcc1:armhf                          1:8.3.0-6+rpi1                          armhf        GCC support library

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 20 
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 40
```


# bash 수정하기

* Workspace 생성하기

```
mkdir Workspace
```

* bash 수정하기

```
vi ~/.bash_aliases

아래 내용 추가하기
---------------------------------------------------------
alias vibash='vi ~/.bash_aliases'
alias reso='source ~/.bashrc'

alias dv='cd ~/Workspace'
---------------------------------------------------------

source ~/.bashrc
```

# font

* 네이버 나눔체 사용 중

```
sudo apt install fonts-nanum fonts-nanum-coding -y
```