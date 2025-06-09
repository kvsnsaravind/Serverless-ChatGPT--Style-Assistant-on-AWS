# Serverless ChatGPT-Style Assistant on AWS

## Overview

This project implements a scalable, serverless chatbot leveraging **AWS Bedrock** and **Cohere’s LLM** for real-time language generation. It uses AWS Lambda and API Gateway to provide a RESTful interface for conversational AI without managing servers or infrastructure.

## Features

* **Serverless Architecture:** Runs entirely on AWS Lambda, ensuring automatic scaling and low maintenance.
* **Real-Time Language Generation:** Integrates Cohere’s large language models via AWS Bedrock for natural, fluent responses.
* **REST API:** Exposes a simple POST endpoint for sending user messages and receiving AI-generated replies.
* **Lightweight and Extensible:** Easy to extend with additional AWS services like DynamoDB or Cognito for context and authentication.

## Architecture

```
User -> API Gateway -> AWS Lambda -> AWS Bedrock (Cohere LLM) -> Lambda -> API Gateway -> User
```

## Setup Instructions

1. **Create AWS Lambda Function:**

   * Use Python 3.9+ runtime.
   * Paste the provided Lambda handler code.
   * Configure environment variables:

     * `BEDROCK_API_URL`: Your AWS Bedrock endpoint URL.
     * `BEDROCK_API_KEY`: API key or credentials for Bedrock.
     * `COHERE_MODEL_ID`: Cohere model identifier (default: `cohere-command-xlarge`).

2. **Create API Gateway:**

   * Create a REST API.
   * Configure a POST method to trigger the Lambda function.
   * Enable CORS if calling from browsers.

3. **Deploy and Test:**

   * Deploy the API.
   * Use tools like curl or Postman to send POST requests with JSON payloads:

     ```json
     {
       "message": "Hello, how are you?"
     }
     ```
   * Receive responses with AI-generated replies.

## Example Request

```bash
curl -X POST https://your-api-url/prod/chat \
-H "Content-Type: application/json" \
-d '{"message": "Tell me a joke"}'
```

## Future Improvements

* Add session management to maintain conversation context.
* Integrate AWS Cognito for secure user authentication.
* Implement streaming responses if supported by AWS Bedrock.
* Add monitoring and logging using CloudWatch.

## Technologies Used

* AWS Lambda
* AWS API Gateway
* AWS Bedrock
* Cohere Large Language Models
* Python 3.9+
* Requests library
---

## Steps involved
1. **Create an AWS Lambda function** with Python 3.9 or later runtime.
2. Set environment variables:

   * `BEDROCK_API_URL` — your AWS Bedrock inference endpoint URL.
   * `BEDROCK_API_KEY` — your API key or IAM credentials.
   * `COHERE_MODEL_ID` — the model you want to use from Bedrock (e.g., `"cohere-command-xlarge"`).
3. Create an **API Gateway** REST API with a POST method integrated to this Lambda function.
4. Deploy the API and use the endpoint to send JSON payloads like `{"message": "Hello, how are you?"}`.
5. The response JSON will contain the generated text under `"reply"`.

---


