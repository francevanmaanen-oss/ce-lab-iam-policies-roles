# Lab Solution: IAM Policies and Roles

**Student Name:** France
**Date:** 21 April 2026
**Lab Completion Time:** ___________ minutes

---

## Part 1: Understanding IAM Policy Structure

### Task 1: Policy Components Explanation

**Explain each component in your own words:**

**Version:**
```
This is the date of when the policy was last updated. _____________________________________________________________
_____________________________________________________________
```

**Statement:**
```
It is the main container for the policy logic. Includes multiple individual permissions._____________________________________________________________
_____________________________________________________________
```

**Sid:**
```
This is the main idea of the logic behind the policy. What does it entail? _____________________________________________________________
_____________________________________________________________
```

**Effect:**
```
This is how the policy will be understood if it explicitly grants access or not. _____________________________________________________________
_____________________________________________________________
```

**Action:**
```
This defines what action that needs to be provided access to._____________________________________________________________
_____________________________________________________________
```

**Resource:**
```
This is where it identifies the specific object the policy covers._____________________________________________________________
_____________________________________________________________
```

---

## Part 2: Custom IAM Policies Created

### S3 Read-Only Policy

**Policy Name:** S3-ReadOnly-SpecificBucket

**Bucket Name Used:** bobsbucketnl

**Policy JSON:**
```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "ListSpecificBucket",
			"Effect": "Allow",
			"Action": [
				"s3:ListBucket"
			],
			"Resource": "arn:aws:s3:::bobsbucketnl"
		},
		{
			"Sid": "ReadObjectsInBucket",
			"Effect": "Allow",
			"Action": [
				"s3:GetObject",
				"s3:GetObjectVersion"
			],
			"Resource": "arn:aws:s3:::bobsbucketnl/*"
		}
	]
}
```

**Screenshot 1: S3 Custom Policy**
![S3 Policy](screenshots/01-s3-policy.png)

---

### EC2 Start/Stop Policy

**Policy Name:** EC2-StartStop-Only

**Policy ARN:** ___________________________

**Screenshot 2: EC2 Custom Policy**
![EC2 Policy](screenshots/02-ec2-policy.png)

---

### CloudWatch Logs Write Policy

**Policy Name:** CloudWatch-Logs-Write-Only

**Policy ARN:** arn:aws:logs:*:*:log-group:/aws/*

**Screenshot 3: CloudWatch Logs Policy**
![CloudWatch Policy](screenshots/03-cloudwatch-policy.png)

---

## Part 3: Policy Attachments

### Policy Attached to User

**User Name:** alice

**Policy Attached:** S3-ReadOnly-SpecificBucket

**Attachment Method:** X Console

**CLI Command (if used):**
```bash
_____________________________________________________________
_____________________________________________________________
```

**Screenshot 4: Policy Attached**
![Policy Attachment](screenshots/04-policy-attached.png)

---

## Part 4: IAM Roles Created

### EC2 Service Role

**Role Name:** EC2-S3-ReadOnly-Role

**Role ARN:** arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess

**Trusted Entity:** ___________________________

**Attached Policies:**
1. AmazonS3ReadOnlyAccess

**Trust Relationship JSON:**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "ec2.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

**Screenshot 5: EC2 Service Role**
![EC2 Role](screenshots/05-ec2-role.png)

---

### Lambda Execution Role

**Role Name:** Lambda-Basic-Execution-Role

**Role ARN:** ___________________________

**Attached Policies:**
1. AWSLambdaBasicExecutionRole
2. CloudWatch-Logs-Write-Only

**Screenshot 6: Lambda Role**
![Lambda Role](screenshots/06-lambda-role.png)

---

### Cross-Account Access Role

**Role Name:** CrossAccount-ReadOnly-Role

**Role ARN:** ___________________________

**External Account ID:** ___________________________

**External ID:** unique-external-id-123
**Attached Policies:**
1. ReadOnlyAccess

**Screenshot 7: Cross-Account Role**
![Cross-Account Role](screenshots/07-cross-account-role.png)

---

## Part 5: Policy Testing

### Policy Simulator Results

**Policy Tested:** ___________________________

**Test Results:**

| Action | Expected Result | Actual Result | Pass/Fail |
|--------|----------------|---------------|-----------|
| s3:GetObject | Allowed | | ☐ Pass ☐ Fail |
| s3:PutObject | Denied | | ☐ Pass ☐ Fail |
| s3:DeleteObject | Denied | | ☐ Pass ☐ Fail |
| ec2:StartInstances | | | ☐ Pass ☐ Fail |
| ec2:TerminateInstances | | | ☐ Pass ☐ Fail |

**Screenshot 8: Policy Simulator**
![Policy Simulator](screenshots/08-policy-simulator.png)

---

### AWS CLI Testing

**Test 1: S3 List Bucket**
```bash
# Command:

# Output:
_____________________________________________________________
_____________________________________________________________

# Result: ☐ Success ☐ Access Denied
```

**Test 2: S3 Upload File**
```bash
# Command:

# Output:
_____________________________________________________________
_____________________________________________________________

# Result: ☐ Success ☐ Access Denied (Expected)
```

**Test 3: S3 Download File**
```bash
# Command:

# Output:
_____________________________________________________________
_____________________________________________________________

# Result: ☐ Success ☐ Access Denied
```

---

## Part 6: Least Privilege Implementation

### Custom Policy with Conditions

**Policy Name:** ___________________________

**Condition Type Used:** ☐ IP Address ☐ Time Window ☐ MFA ☐ Other: _______

**Policy JSON:**
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        
      ],
      "Resource": "",
      "Condition": {
        
      }
    }
  ]
}
```

**Rationale for this policy:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

---

## Part 7: Troubleshooting

### Issue Encountered (if any)

**Issue Description:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

**Commands Used to Diagnose:**
```bash
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

**Resolution:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

**Screenshot 9: Troubleshooting Output**
![Troubleshooting](screenshots/09-troubleshooting.png)

---

## Reflection Questions

### 1. Why are IAM roles preferred over access keys for EC2 instances?

**Your answer:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

### 2. Explain the principle of least privilege and how you applied it in this lab.

**Your answer:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

### 3. What is the difference between identity-based and resource-based policies?

**Your answer:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

### 4. When would you use an explicit "Deny" in a policy?

**Your answer:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

### 5. Describe a scenario where you'd use conditions in IAM policies.

**Your answer:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

---

## Summary of Resources Created

**IAM Policies:**
1. ___________________________  (ARN: ___________________________)
2. ___________________________  (ARN: ___________________________)
3. ___________________________  (ARN: ___________________________)

**IAM Roles:**
1. ___________________________  (ARN: ___________________________)
2. ___________________________  (ARN: ___________________________)
3. ___________________________  (ARN: ___________________________)

**Users Modified:**
1. ___________________________

---

## Cleanup Confirmation

- [ ] Detached all custom policies from users
- [ ] Deleted custom IAM policies
- [ ] Detached policies from roles
- [ ] Deleted test IAM roles
- [ ] Verified no resources remain

**Cleanup Commands:**
```bash
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

---

## Self-Assessment

**Rate your understanding (1-5):**

| Concept | Before Lab | After Lab | Improvement |
|---------|-----------|-----------|-------------|
| IAM Policy Structure | ___/5 | ___/5 | +___ |
| Custom Policy Creation | ___/5 | ___/5 | +___ |
| IAM Roles | ___/5 | ___/5 | +___ |
| Service Roles | ___/5 | ___/5 | +___ |
| Trust Relationships | ___/5 | ___/5 | +___ |
| Policy Testing | ___/5 | ___/5 | +___ |
| Least Privilege | ___/5 | ___/5 | +___ |
| Troubleshooting IAM | ___/5 | ___/5 | +___ |

---

## Instructor Verification

**Instructor Name:** ___________________________

**Date Reviewed:** ___________________________

**All policies validated:** ☐ Yes ☐ No

**Roles properly configured:** ☐ Yes ☐ No

**Comments:**
```
_____________________________________________________________
_____________________________________________________________
_____________________________________________________________
```

**Grade/Status:** ___________________________

---

**Lab Status:** ☐ Complete ☐ Needs Revision

**Submission Date:** ___________________________
