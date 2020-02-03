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

* * *

### 전체 실습 리뷰

#### 1. CloudFormation  
1. 첫번째 CloudFormation 을 통해 탐지 및 분석의 토대가 되는 환경을 구성하였습니다. 또한 준비 과정에서 GuardDuty 와 Security Hub 를 활성화함으로써 위협이나 침입이 발생하였을 경우 탐지할 수 있는 준비를 하였습니다. 두번째 CloudFormation 을 통해 2개의 EC2 인스턴스가 생성되었었습니다. 1개의 인스턴스는 공격자용도로 생성된 Malicous Host 였으며 다른 하나의 인스턴스는 침해당한 EC2 용도의 Compromized Host 였습니다. 또한, Malicious Host 가 인터넷을 사용하기 위해 사용한 Elastic IP 는 GuardDuty 의 Custom Threat IP 리스트에 등록이 되어 있었던 상태입니다.  
2. AWS 에서는 EC2 인스턴스 생성 시 Key Pair 기반의 SSH 접속 방식을 기본값으로 제공하고 있지만 일부 기업이나 조직의 경우 SSH Key Pair 관리의 불편함 등을 이유로 SSH Key Pair 기반이 아닌 암호 기반 SSH 접속을 수동으로 활성화하여 사용하고 있기도 합니다. 이런 인증 방식의 인스턴스는 Brute Force 공격에 취약하며 이와 같은 공격을 GuardDuty 를 통해 탐지하고 탐지된 정보를 이용해서 Inspector 가 해당 인스턴스를 스캔하도록 구성하였습니다.

* * *
#### 2. 공격
1. 공격자의 공격은 BruteForce 공격을 통해 인스턴스가 침해되고 자격증명이 침해되는 것을 가정하여 진행되었습니다.

* * *
#### 3. 탐지 및 분석
1. 실제 고객이 사용할 수 있는 탐지 및 분석 솔루션은 다양하겠지만 이 실습에서는 GuardDuty 를 통해 1차 위협을 탐지하고 Security Hub 및 Inspector 와 같은 보안 서비스를 통해 좀 더 자동화된 분석 작업을 수행하도록 구성하였습니다.
2. 탐지된 위협에 대한 분석은 CloudWatch Insight 나 CloudTrail 혹은 ElasticSearch 와 같은 서비스 등을 통하여 수행될 수 있습니다.

* * *

### Quick Questions
{{% notice info %}}
 정답을 보시려면 ">" 로 시작하는 질문을 클릭하시면 됩니다.
{{% /notice %}}

{{%expand "계정 침해 실습에서 공격자가 사용한 AWS 자격증명의 유형은 무엇인가요?" %}} IAM Role 에서 사용하는 임시보안자격증명!{{% /expand%}}  

{{%expand "인스턴스 침해 대응에서 Security Gruop 의 SSH 관련 정책을 삭제하여도 관리자가 외부에서 접근이 가능한 이유는?" %}} Systems Manager 의 Session Manager 는 Systems Manager Agent 를 이용하여 SSH 접속 환경을 제공합니다!{{% /expand%}}  

{{%expand "AWS 의 다양한 보안 솔루션과 3rd 보안 솔루션을 통합하여 모니터링하고 경보를 발생하도록 구성할 수 있는 AWS 서비스는?" %}} AWS Security Hub!{{% /expand%}}