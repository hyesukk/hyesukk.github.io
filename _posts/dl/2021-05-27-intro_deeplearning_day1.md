---
title:  "딥러닝 입문 1일차" 
excerpt: 딥러닝을 소개합니다

categories:
  - 'dl'
tags:
  - AI
  - DL
  - python
  - book

toc: true
toc_sticky: true

date: 2021-05-27
last_modified_at: 2021-06-03

---

# 01. 인공지능

* strong AI
  + 사람과 구분이 안 될 정도로 강한 성능을 가진 인공지능
  + 현재 개발되지 않은 방법론
  + 영화 속에서 등장하는 비서 시스템 등

* weak AI
  + 특정 영역에서 작업을 수행하는 인공지능
  + 지금까지 발전을 거듭하고 있는 인공지능 기술
  + 자율 주행 자동차, 인공지능 스피커

* 머신러닝, 딥러닝, 인공지능의 관계

> 인공지능 > 머신러닝 > 딥러닝


# 02. 머신러닝 소개

* 기계 학습 (Machine Learning)

* 머신러닝은 스스로 규칙을 수정한다
  + "학습" 및 "훈련"
    - 데이터의 규칙을 컴퓨터 스스로 찾아내는 것
    - 규칙을 스스로 찾아 수정하는 과정

* 머신러닝의 학습 방식
  + supervised learning
    -  훈련 데이터(입력과 target 또는 labeled)를 이용하여 모델을 학습
    -  기존의 데이터를 이용하여 모델을 학습 시켜 새로운 입력에 대해 예측
    -  단점 : 훈련 데이터 의존도가 높아 잘못되거나 적은 훈련 데이터로 잘못된 모델이 생성될 수 있다
  + unsupervised learning
    -  target이 없는 데이터로 모델을 학습
    -  clustering
    -  비지도학습은 다루지 않음
  + reinforcement learning
    -  agent를 훈련시켜 수행에 대한 보상과 현재 상태를 부여
    -  agent의 목표는 최대한 많은 보상을 받는 것
    -  Q-learning, SARSA, DQN

* 규칙
  + 가중치와 절편 

> 1.5 (가중치)  + x (입력) + 0.1 (절편) = y (target)

* 모델은 머신러닝의 수학적 표현입니다
  + 훈련 데이터로 학습된 머신러닝 알고리즘
  + 모델 파라미터 : 가중치와 절편

* 손실 함수로 모델의 규칙을 수정한다
  + 최적화 알고리즘을 이용하여 손실 함수의 최솟값을 찾는다

# 03. 딥러닝 소개

* 딥러닝
  + 인공신경망으로 구성

* 딥러닝은 머신러닝이 처리하기 어려운 데이터를 더 잘 처리한다
  + '인지'와 관련된 문제를 머신러닝보다 더 잘 해결함
  + 딥러닝 : 이미지/영상, 음성/소리, 텍스트/번역 등의 비정형 데이터
  + 머신러닝 : 데이터베이스, 레코드 파일, 엑셀/csv 등에 담긴 정형데이터
