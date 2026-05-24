# AWS Cloud Infrastructure Monitoring

A hands-on cloud infrastructure project built on AWS Free Tier,
covering server deployment, monitoring, alerting, and log storage
— same stack used in real Data Center Operations environments.

---

## What I Built

Launched a Linux server on AWS EC2, configured IAM permissions
following least-privilege principles, set up a CPU usage alarm
that sends an email alert when load exceeds 80%, and created an
S3 bucket for centralized log storage — all in the Mumbai region.

---

## Services & Configuration

**EC2**
- Instance: t2.micro (Amazon Linux 2023)
- Region: ap-south-1 (Mumbai)
- Instance ID: i-091306ad19d60263f
- Public IP: 3.110.44.186

**IAM**
- Role: Dco-CloudWatch-Role
- Policy: CloudWatchAgentServerPolicy
- Principle: No hardcoded credentials, service role only

**CloudWatch**
- Alarm: DCO-CPU-Alert
- Metric: CPUUtilization
- Threshold: > 80% for 5 consecutive minutes
- Action: SNS email notification to ops inbox

**S3**
- Bucket: dco-logs-sarthak
- Region: ap-south-1
- Purpose: Centralized log storage and retention
- 
EC2 Instance (DCO-Server)
|
└── IAM Role (CloudWatch access)
|
└── CloudWatch Alarm (CPU > 80%)
|
├── SNS → Email Alert
└── S3 → dco-logs-sarthak
  ---

## Screenshots

**EC2 Instance — Launched**


![EC2](Screenshot%20(7)

.png)

**IAM Role — Created & Attached**


![IAM](Screenshot%20(8)

.png)

**EC2 Running + IAM Attached**


![EC2-IAM](Screenshot%20(10)

.png)

**CloudWatch Alarm — Active**


![CloudWatch](Screenshot%20(11)

.png)

**S3 Bucket — Created**


![S3](Screenshot%20(12)

.png)

## What I Learned

Setting up monitoring from scratch made it clear why IAM roles
matter more than access keys — no credentials to rotate or leak.
CloudWatch alarms with SNS take maybe 10 minutes to configure
but give you real visibility into what your server is doing.
S3 as a log sink is cheap and reliable for small-scale setups.

---

## Cost

Entire project runs on AWS Free Tier.
EC2 t2.micro: 750 hrs/month free.
S3: 5 GB free.
CloudWatch: 10 alarms free.

## Architecture
