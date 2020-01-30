+++
title = "공격 실행"
weight = 1
pre = "<b>2.1 </b>"
+++

* * *

> 이제 이전 단계에서 완성된 AWS 이용환경을 대상으로 해서 CloudFormation 을 이용하여 몇가지 공격을 시뮬레이션 해보도록 하겠습니다. 제공된 CloudFormation 을 실행하면 공격에 사용되는 EC2 생성과 함께 몇 가지 공격이 자동으로 실행되게 됩니다. 

### 소요 시간
1.	CloudFormation 템플릿의 내용을 살펴보고 실행하기 – 5 분
2.	위협 탐지 및 확인 - 25 분

{{% notice info %}}
CloudFormation 을 실행하기 전에 CloudFormation Code 를 확인하고 싶으시면 [여기]()를 클릭하시면 됩니다..
{{% /notice %}}


## CloudFormation 템플릿 실행
1. CloudFormation 템플릿을 실행하기 위해 [Deploy to AWS 링크](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/template?stackName=ThreatDetectionWksp-Env-Setup&templateURL=https://do-not-delete-eunsshin-workshop.s3.ap-northeast-2.amazonaws.com/threatdetection/02-attack-simulation.yml)를 클릭합니다.

    |Region|Deploy|
    |------|-----|
    |Oregon|[![Deploy to AWS](/images/deploy-to-aws.png)](https://us-west-2.console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/create/template?stackName=ThreatDetectionWksp-Env-Setup&templateURL=https://do-not-delete-eunsshin-workshop.s3.ap-northeast-2.amazonaws.com/threatdetection/02-attack-simulation.yml)|

2. "Deploy to AWS" 를 클릭하면 브라우져에서 새로운 창이나 새로운 탭이 열리면서 CloudFormation 을 실행할 수 있는 AWS Console 화면으로 자동 접속되게 됩니다.
![CloudFormation](/images/attack_formation1.png)
3. 아래의 "스택 세부 정보 지정" 설정 화면에서 CloudFormation 스택의 이름을 확인하고(수정하셔도 됩니다.) "다음"을 클릭합니다.
![CloudFormation](/images/attack_formation2.png)
4. "스택 생성" 버튼을 클릭하면 아래와 같은 화면이 나타나게 됩니다. Tag 값을 설정하시려면 원하는 Tag 값을 입력하시고 Tag 가 필요없는 경우 "다음" 버튼을 클릭합니다.
![CloudFormation](/images/attack_formation3.png)
5. 다음 화면에서 스택 생성을 위하여 사용된 템플릿의 설정값을 확인한 후 화면 하단에 있는 IAM 리소스 생성 권한 승인 항목을 체크한 후 "스택 생성" 버튼을 클릭합니다.
![CloudFormation](/images/iam_permission.png)
6. 정상적으로 진행이 되는 경우 아래와 같이 스택의 상태가 "CREATE_COMPLETE)으로 되어 있는 것을 확인하실 수 있습니다.
![CloudFormation](/images/attack_formation4.png)

> {{% button icon="fas fa-asterisk" %}}아래는 두 번째 CloudFormation 을 이용한 리소스 생성 후의 아키텍쳐입니다.{{% /button %}}

![Architecture](/images/formation_architecture1.png)
