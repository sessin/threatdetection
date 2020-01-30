+++
title = "토의"
weight = 3
pre = "<b>3.3 </b>"
+++

* * *

> 이번에는 이전 과정을 통해 실행된 공격을 AWS 보안 서비스를 이용하여 탐지하고 분석하는 내용을 다뤄보도록 하겠습니다.
  
### 소요 시간
1. 리뷰 및 토론 – 10 분
2. 질의 응답 - 10 분

### 아키텍처 개요

### 전체 실습 개요

1. CloudFormation  
두번째 CloudFormation 을 통해 2개의 EC2 인스턴스가 생성되었었습니다. 1개의 인스턴스는 공격자용도로 생성된 Malicous Host 였으며 다른 하나의 인스턴스는 침해당한 EC2 용도의 Compromized Host 였습니다. 또한, Malicious Host 가 인터넷을 사용하기 위해 사용한 Elastic IP 는 GuardDuty 의 Custom Threat IP 리스트에 등록이 되어 있었던 상태입니다.  
2. AWS 에서는 EC2 인스턴스 생성 시 Key Pair 기반의 SSH 접속 방식을 기본값으로 제공하고 있지만 일부 기업이나 조직의 경우 SSH Key Pair 관리의 불편함 등을 이유로 SSH Key Pair 기반이 아닌 암호 기반 SSH 접속을 수동으로 활성화하여 사용하고 있기도 합니다. 이런 인증 방식의 인스턴스는 Brute Force 공격에 취약하며 이와 같은 공격을 GuardDuty 를 통해 탐지하고 탐지된 정보를 이용해서 Inspector 가 해당 인스턴스를 스캔하도록 구성하였습니다.
3. 

{{%expand "계정 침해 실습에서 공격자가 사용한 AWS 자격증명의 유형은 무엇인가요?" %}} IAM Role 에서 사용하는 임시보안자격증명!.{{% /expand%}}
