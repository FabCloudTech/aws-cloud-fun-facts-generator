# AWS Cloud Fun Facts Generator

A tiny serverless app: API Gateway → Lambda returns a random AWS fun fact.

## How it works (1 paragraph)
API Gateway exposes an HTTP endpoint. When you call it, a Lambda function runs and returns a fun fact as JSON. Logs go to CloudWatch. (If I add DynamoDB later, it will store facts there.)

## Run it (simple)
1) Deploy the Lambda + API (follow steps in this repo).
2) Test with curl or your browser using the API Gateway URL.

## Architecture (picture)
![Architecture](docs/screenshots/01-architecture.png)

## Proof (console screenshots)
- Lambda Config: ![Lambda](docs/screenshots/02-lambda-config.png)
- Lambda Code: ![Lambda](docs/screenshots/03-lambda-code.png)
- Lambda Test: ![Lambda](docs/screenshots/04-lambda-test-success.png)
- API Gateway: ![Routes](docs/screenshots/05-api-gateway-config.png)
- API Gateway Routes: ![Routes](docs/screenshots/06-api-gateway-routes.png)
- API Stage : ![Stage](docs/screenshots/07-api-stage-url.png)
- API Test:![Logs](docs/screenshots/08-api-test-success.png)

## What I learned
- Wiring API Gateway to Lambda
- Using CloudWatch Logs to debug
- Keeping IAM least-privilege
