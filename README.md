# terraform-class · Terraform으로 AWS 네트워크 구성하기

> AWS Cloud School 수업 실습. 콘솔에서 손으로 만들던 VPC 환경을 Terraform 코드로 만들고 지웁니다.

## 만드는 것

```
VPC 10.250.0.0/16
├─ Public Subnet  (2a, 2c) ── Internet Gateway
├─ Private Subnet (2a, 2c) ── NAT Gateway (EIP)
├─ Bastion Subnet (2a)
├─ EC2 (t2.micro) + Security Group
├─ Route53 Hosted Zone + ACM 인증서 (DNS 검증)
└─ S3 Bucket
```

| 파일 | 내용 |
|---|---|
| `00.variables.tf`, `01.provider.tf` | 변수, AWS 프로바이더 |
| `02.vpc.tf` ~ `06.routingtable.tf` | VPC, 서브넷, IGW, NAT, 라우팅 테이블 |
| `01.securitygroup.tf`, `02.ec2.tf` | 보안 그룹, EC2 |
| `07.acm.tf`, `08.route53.tf`, `09.s3.tf` | 인증서, DNS, S3 |

## 실행

```bash
terraform init
terraform plan
terraform apply
terraform destroy   # 실습이 끝나면 비용이 나오지 않게 삭제
```
