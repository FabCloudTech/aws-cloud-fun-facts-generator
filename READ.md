# ☁️AWS Cloud Fun Facts Generator

A tiny serverless app: API Gateway → Lambda returns a random AWS fun fact.

## 🧠 How it works 
API Gateway exposes an HTTP endpoint. When you call it, a Lambda function runs and returns a fun fact as JSON. Logs go to CloudWatch. (If I add DynamoDB later, it will store facts there.)

## 🚀 Run it (simple)
1) Deploy the Lambda + API (follow steps in this repo).
2) Test with curl or your browser using the API Gateway URL.

## 🏗️ Architecture 
![Architecture](docs/screenshots/01-architecture-stage-1.png)

# 🟨Stage 1- Lambda + API Gateway Integration
This stage connects the Lambda to an API Gateway endpoint  and validates that it returns  data successfully.

## 🔧 Proof of Stage 1 (console screenshots)
- Lambda Config: ![Lambda](docs/screenshots/02-lambda-config.png)
- Lambda Code: ![Lambda](docs/screenshots/03-lambda-code.png)
- Lambda Test: ![Lambda](docs/screenshots/04-lambda-test-success.png)
- API Gateway: ![Routes](docs/screenshots/05-api-gateway-config.png)
- API Gateway Routes: ![Routes](docs/screenshots/06-api-gateway-routes.png)
- API Stage : ![Stage](docs/screenshots/07-api-stage-url.png)
- API Test:![Stage](docs/screenshots/08-api-test-success.png)

## 🧩What I learned
- How to connect API Gateway to Lambda and a deploy a working endpoint.
- How to test an API Invoke URL.
- Practiced secure documentation by redacting sensitive ARNs.
---

---

## ⚡ Stage 2 – DynamoDB Integration  

This stage connects **AWS Lambda** to **Amazon DynamoDB**, allowing the app to fetch fun facts dynamically instead of relying on hardcoded data.  
✅ Confirmed: the API successfully returns a random AWS fun fact stored in DynamoDB.  

---

### 🧩 Architecture (Stage 2)
**Flow:**  
User → API Gateway (`/funfact`) → Lambda Function → DynamoDB Table (`CloudFacts`)

![Stage 2 Architecture](docs/screenshots/09-stage2-architecture.png)

---

### 🧾 Step-by-Step Implementation  

**🪶 Step 1 – Create DynamoDB Table**  
Configured a new table named **CloudFacts** with the partition key `FactID (String)`.  
![DynamoDB Create Table](docs/screenshots/09-dynamodb-create-table.png)

---

**🪶 Step 2 – Confirm Table Creation**  
Table activated successfully and ready for data input.  
![DynamoDB Table Created](docs/screenshots/10-dynamodb-table-created.png)

---

**🪶 Step 3 – Add Items (Fun Facts)**  
Inserted multiple items with attributes `FactID` and `FactText`.  
![Create Item](docs/screenshots/11-dynamodb-create-item.png)

---

**🪶 Step 4 – Verify Items in Table**  
Confirmed that all AWS fun facts were stored correctly in DynamoDB.  
![Items List](docs/screenshots/12-dynamodb-items-list.png)

---

**🪶 Step 5 – Attach IAM Policy to Lambda Role**  
Granted the function read-only access to DynamoDB using the `AmazonDynamoDBReadOnlyAccess` managed policy.  
![IAM Policy](docs/screenshots/13-iam-dynamodb-policy.png)

---

**🪶 Step 6 – Update Lambda Code**  
Replaced previous static code with Python (boto3) logic to query DynamoDB and return a random fact.  
![Lambda Code](docs/screenshots/14-lambda-dynamodb-code.png)

---

**🪶 Step 7 – Test Lambda Function**  
Deployed and executed successfully — the function retrieved a random fact.  
![Lambda Test Success](docs/screenshots/15-lambda-test-success.png)

---

**🪶 Step 8 – Verify API Endpoint Deployment**  
API Gateway endpoint created successfully and integrated with the Lambda function.  
![API Endpoint Success](docs/screenshots/16-api-endpoint-success.png)

---

**🪶 Step 9 – Test Endpoint in Browser**  
Hit the live endpoint and received a working response from DynamoDB — the fun fact displays perfectly 🎉  
![API Test Output](docs/screenshots/17-api-test-output.png)

---

### 🧾 Example Output
```json
{"fact": "EC2 was one of the first AWS services to change IT forever."}




