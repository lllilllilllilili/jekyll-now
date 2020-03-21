---
title: "Try creating blockchain with java"
date: 2020-03-22
categories: toy

---
#### ㅡ Try creating blockchain with java

![toy-project](https://img.shields.io/badge/toy_project-67orange?)
![java](https://img.shields.io/badge/java-jdk_13-blue?logo=java)




## Table of Contents

- [Introduction](#introduction)
- [Hash definitions, reasons for use](#hash_definitions_reasons_for_use)
- [Blockchain Principles & Issues](#blockchain_principles_&_issues)
- [Result](#result)
- [License](#license)
- [About](#about)

## Introduction
블록체인은 원장 분산 시스템으로 P2P 형식으로 노드와 사슬이 연결되어 있는 방식입니다. 1세대 블록체인 기술백서에서는 합의 알고리즘으로 동작합니다. 블록체인은 decentualize 를 실현하며, 흔히 말하는 DAPP 을 통칭 합니다. 이를 통해 중앙 집권 저장방식에서 분산화된 개인이 데이터를 저장가능합니다. 하지만, 아쉽게도 블록체인 트랜잭션을 개인이 전부 가지고 있기에는 역부족 이기 때문에 아이러니 하게도 거래소와 같은 곳에서 이러한 데이터를 관리하게 됩니다. 


## Hash_definitions_reasons_for_use

Hash는 일반적으로 암호화가 적용된 SHA-256 을 사용하며, 사용하는 이유는 객체를 구별하기 위해 사용합니다.

Hash 단독으로 사용되는 것보다 `이전해쉬 + 데이터값 + 타임스태프 + nonce` 로 조합하여 만들고 Hash Function 을 사용해 Hash를 구합니다.

## Blockchain_Principles_&_Issues

![d2](../../assets/images/blockchain/b1.png)



## Result
![d2](../../assets/images/blockchain/b2.png)

![d2](../../assets/images/blockchain/b3.png)

[code]

## license
MIT License

## About

Authored and maintained by **ingyu**


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
[code]: https://github.com/lllilllilllilili/hufs_projects/blob/master/blockchain/demoApplication.java
