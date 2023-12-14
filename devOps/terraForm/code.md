https://developer.hashicorp.com/terraform/tutorials?product_intent=terraform

get Started -> AWS -> install TerraForm
 
``` bash
brew tap hashicorp/tap  
*해쉬코프 제공하는 패키지 저장소 등ㅗ

brew install hashicorp/tap/terraform
*테라폼 설ㅣ
```
Write 인프라 코드 작성 - HCL(Hashicorp Configuration Language)언어로 작성
plan 인프라 코드 검증  - 
Apply 인프라 코드 적용


terraform init ->
```
.terraform
.terraform.lock.hcl
파일 생성
[.terraform]->main.tf파일에 명시된 프로바이더나 모듈의 캐시와 데이터를 보관
[.terraform.lock.hcl]->팀에서 협업하거나 ci/cd할떄 필요한 구성요소 해당 워크스페이스에서 사용하는 프로바이더들의 해쉬섬을 체크하고 버전을 라킹 작업자가 동일한 버전의 동일한 코드 위해 사용한다
```