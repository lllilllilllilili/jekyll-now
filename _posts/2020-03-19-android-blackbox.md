---
title: "Simple black box (Recording, Play function)"
date: 2020-03-19
categories: portfolio

---
#### ㅡ Simple black box (Recording, Play function)

![version](https://img.shields.io/badge/version-0.0.1-orange?)
![android](https://img.shields.io/badge/android-3.4.2-blue?logo=android)
![java](https://img.shields.io/badge/java-java jdk 13-yellow?logo=java)


## Table of Contents

- [Introduction](#introduction)
- [Prerequisite](#prerequisite)
- [Development](#development)
  - [Install](#install)
  - [Testing](#testing)
  - [Commit](#commit)
- [Result](#result)
- [License](#license)
- [About](#about)

## Introduction
MediaRecorder를 이용해서 녹화 및 재생하는 앱을 작성합니다. 이때, 녹화화면에 위도,경도,속도를 표시하고 compass를 이용해서 방향을 나타냅니다. array_list를 생성해서 녹화 시작시 시작위도, 경도와 녹화종료시 끝위도, 경도를 녹화된 파일과 함께 SQLite에 저장후, array_list의 item을click시 녹화된 영상과 시작위도, 경도 그리고 끝위도, 경도가 재생되는 앱을 작성합니다. 

## Prerequisite

Must run in terminal in the fedora environment.

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

<center><img src="../../assets/images/android/a1.png" width="300" height="300"></center>
<center>(Initial screen)</center>

<center><img src="../../assets/images/android/a2.png" width="300" height="300"></center>
<center>GPS is loaded at first start.</center>


<center><img src="../../assets/images/android/a3.png" width="300" height="300"></center>
<center>If you move from the current location after recording, you can check the latitude, longitude, and speed values.</center>

<center><img src="../../assets/images/android/a4.png" width="300" height="300"></center>
<center>The file is saved in the current time format when recording is stopped.</center>

<center><img src="../../assets/images/android/a5.png" width="300" height="300"></center>
<center>Shows the saved list after recording.</center>

<center><img src="../../assets/images/android/a6.png" width="300" height="300"></center>
<center>When you play a saved recording, the information is displayed on the right side of the progressive bar below.</center>


<iframe width="640" height="360" src="https://www.youtube.com/watch?v=1L3viy_noBQ" frameborder="0" gesture="media" allowfullscreen=""></iframe>

## code
[code]

## license
MIT License

## About

Authored and maintained by **ingyu**


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[code]: https://github.com/lllilllilllilili/hufs_projects/blob/master/OperatingSystem/Heart%20rate%20measurement.c