---
title: Python Pyqt5 설치
author: 전규범
date: 2020-10-26 00:55:00 +0800
categories: [python, pyqt5]
tags: [python, pyqt5]
toc: false
---

Linux에서 PyQt5 설치 시

```terminal
pip3 install pyqt5


만 입력하면 다음과 같은 에러를 보인다.

```terminal
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, webgl, xcb.

Aborted (core dumped)
```

apt를 이용하여 python의 pyqt를 설치하면 해당 문제를 해결할 수 있다.
```terminal
sudo apt install python-pyqt5
sudo apt install python3-pyqt5
```


참고
1. https://starseeker711.tistory.com/128