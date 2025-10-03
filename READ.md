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
- Lambda config: ![Lambda](docs/screenshots/02-lambda-config.png)
- Lambda code: ![Lambda](docs/screenshots/02b-lambda-code.png)
- API routes: ![Routes](docs/screenshots/03-api-gateway-routes.png)
- API stage URL: ![Stage](docs/screenshots/04-api-gateway-stage-url.png)
- Logs success: ![Logs](docs/screenshots/05-cloudwatch-logs-success.png)

## What I learned
- Wiring API Gateway to Lambda
- Using CloudWatch Logs to debug
- Keeping IAM least-privilege
