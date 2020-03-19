---
title: "Simple black box (Recording, Play function)"
date: 2020-03-19
categories: portfolio

---
#### ㅡ Simple black box (Recording, Play function)

![version](https://img.shields.io/badge/version-0.0.1-orange?)
![android](https://img.shields.io/badge/android-oreo-pink?logo=android)
![java](https://img.shields.io/badge/java-java jdk 10-yellow?logo=java)


## Table of Contents

- [Introduction](#introduction)
  - [Hierarchy](#hierarchy)
- [Prerequisite](#prerequisite)
- [Development](#development)
  - [Install](#install)
  - [Testing](#testing)
  - [Commit](#commit)
- [Result](#result)
- [Video](#video)
- [Code](#code)
- [License](#license)
- [About](#about)

## Introduction
MediaRecorder를 이용해서 녹화 및 재생하는 앱을 작성합니다. 이때, 녹화화면에 위도,경도,속도를 표시하고 compass를 이용해서 방향을 나타냅니다. array_list를 생성해서 녹화 시작시 시작위도, 경도와 녹화종료시 끝위도, 경도를 녹화된 파일과 함께 SQLite에 저장후, array_list의 item을click시 녹화된 영상과 시작위도, 경도 그리고 끝위도, 경도가 재생되는 앱을 작성합니다. 

### Hierarchy
```
|-- src
|  `-- DBHelper.java
|  `-- MainActivity.java
|  `-- VideoPlay.java
|  `-- init_display.java
|  `-- list_display.java
|
  ``
```

## Prerequisite

- [android studio](https://developer.android.com/studio): It's developed by the Android studio. Deploy using multiple libraries.

## Development

### Install

```bash
$ git clone https://github.com/lllilllilllilili/hufs_projects.git
```
### Testing

```bash
$ adb shell
$ am start -n com.package.name/com.package.name.ActivityName
```

### Commit

We are following [Angular's commitizen rules](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines) for formatting git commit message. This allows you to read messages that are easy to understand when looking for project history. It also uses the git commit message to generate our [CHANGELOG](/CHANGELOG.md) file.
```bash
$ npm install -g git-cz
$ git add .
$ git git-cz
$ git push
```

## Result

<center><img src="../../assets/images/android/a1.png" width="500" height="500"></center>
<center>초기 화면</center>
--- 
<br>
<center><img src="../../assets/images/android/a2.png" width="500" height="500"></center>
<center>처음시작시 GPS LOADING 합니다.</center>
--- 
<br>
<center><img src="../../assets/images/android/a3.png" width="500" height="500"></center>
<center>화시작후 현재위치에서 움직이면 위도,경도,속도 값을 확인할 수 있습니다.</center>
--- 
<br>
<center><img src="../../assets/images/android/a4.png" width="500" height="500"></center>
<center>녹화중지시 현재시간 포맷으로 파일이 저장됩니다.</center>
--- 
<br>
<center><img src="../../assets/images/android/a5.png" width="500" height="500"></center>
<center>녹화 후 저장된 리스트를 보여줍니다.</center>
--- 
<br>
<center><img src="../../assets/images/android/a6.png" width="500" height="500"></center>
<center>저장된 녹화영상을 재생하면 밑에 프로그레바와 우측에 정보가 표시됩니다.
</center>


## Video
[![Video Label](http://img.youtube.com/vi/1L3viy_noBQ/0.jpg)](https://www.youtube.com/watch?v=1L3viy_noBQ)
<center>위 img 클릭 시 영상으로 넘어갑니다. 😀</center>


## Code
[code]

## license
MIT License

## About

Authored and maintained by **ingyu**


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[code]: https://github.com/lllilllilllilili/hufs_projects/tree/master/MobileProgramming