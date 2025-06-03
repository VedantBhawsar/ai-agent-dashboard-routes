# ai-agent-dashboard-routes

# AI Agents Dashboard API Integration

This document outlines all the API routes required for integration in the AI Agents Dashboard project.

## Authentication APIs

### User Authentication
- **POST /api/auth/login**
  - Description: Authenticate a user and generate access token
  - Request Body:
    ```json
    {
      "email": "string",
      "password": "string"
    }
    ```
  - Response:
    ```json
    {
      "token": "string",
      "user": {
        "id": "string",
        "name": "string",
        "email": "string",
        "role": "string"
      }
    }
    ```

- **POST /api/auth/signup**
  - Description: Register a new user
  - Request Body:
    ```json
    {
      "name": "string",
      "email": "string",
      "password": "string"
    }
    ```
  - Response:
    ```json
    {
      "success": true,
      "message": "User registered successfully",
      "user": {
        "id": "string",
        "name": "string",
        "email": "string"
      }
    }
    ```

- **POST /api/auth/forgot-password**
  - Description: Request password reset
  - Request Body:
    ```json
    {
      "email": "string"
    }
    ```
  - Response:
    ```json
    {
      "success": true,
      "message": "Password reset link sent to email"
    }
    ```

- **POST /api/auth/reset-password**
  - Description: Reset password with token
  - Request Body:
    ```json
    {
      "token": "string",
      "password": "string"
    }
    ```
  - Response:
    ```json
    {
      "success": true,
      "message": "Password reset successful"
    }
    ```

## Chatbot APIs

### Chatbot Management

- **GET /api/chatbots**
  - Description: Get list of all chatbots
  - Response:
    ```json
    {
      "chatbots": [
        {
          "id": "string",
          "name": "string",
          "description": "string",
          "status": "active|inactive",
          "interactions": "number",
          "model": "string",
          "createdAt": "string"
        }
      ]
    }
    ```

- **GET /api/chatbots/:id**
  - Description: Get specific chatbot details
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "interactions": "number",
      "model": "string",
      "createdAt": "string",
      "systemPrompt": "string",
      "temperature": "number",
      "maxTokens": "number",
      "enableTools": "boolean",
      "enableMemory": "boolean",
      "knowledgeBase": "string"
    }
    ```

- **POST /api/chatbots**
  - Description: Create a new chatbot
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string",
      "model": "string",
      "status": "active|inactive",
      "systemPrompt": "string",
      "temperature": "number",
      "maxTokens": "number",
      "enableTools": "boolean",
      "enableMemory": "boolean",
      "knowledgeBase": "string"
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "model": "string",
      "createdAt": "string"
    }
    ```

- **PUT /api/chatbots/:id**
  - Description: Update a chatbot
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string",
      "model": "string",
      "status": "active|inactive",
      "systemPrompt": "string",
      "temperature": "number",
      "maxTokens": "number",
      "enableTools": "boolean",
      "enableMemory": "boolean",
      "knowledgeBase": "string"
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "model": "string",
      "updatedAt": "string"
    }
    ```

- **DELETE /api/chatbots/:id**
  - Description: Delete a chatbot
  - Response:
    ```json
    {
      "success": true,
      "message": "Chatbot deleted successfully"
    }
    ```

### Chatbot Testing

- **POST /api/chatbots/:id/test**
  - Description: Test a chatbot with a message
  - Request Body:
    ```json
    {
      "message": "string",
      "conversationId": "string" // Optional, for continuity
    }
    ```
  - Response:
    ```json
    {
      "response": "string",
      "conversationId": "string"
    }
    ```

## Voice Agent APIs

### Voice Agent Management

- **GET /api/voice-agents**
  - Description: Get list of all voice agents
  - Response:
    ```json
    {
      "voiceAgents": [
        {
          "id": "string",
          "name": "string",
          "description": "string",
          "status": "active|inactive",
          "interactions": "number",
          "model": "string",
          "voice": "string",
          "createdAt": "string"
        }
      ]
    }
    ```

- **GET /api/voice-agents/:id**
  - Description: Get specific voice agent details
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "interactions": "number",
      "model": "string",
      "voice": "string",
      "createdAt": "string",
      "systemPrompt": "string",
      "temperature": "number",
      "maxTokens": "number",
      "enableTools": "boolean",
      "enableMemory": "boolean",
      "knowledgeBase": "string",
      "voiceSettings": {
        "speed": "number",
        "pitch": "number",
        "accent": "string"
      }
    }
    ```

- **POST /api/voice-agents**
  - Description: Create a new voice agent
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string",
      "model": "string",
      "voice": "string",
      "status": "active|inactive",
      "systemPrompt": "string",
      "temperature": "number",
      "maxTokens": "number",
      "enableTools": "boolean",
      "enableMemory": "boolean",
      "knowledgeBase": "string",
      "voiceSettings": {
        "speed": "number",
        "pitch": "number",
        "accent": "string"
      }
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "model": "string",
      "voice": "string",
      "createdAt": "string"
    }
    ```

- **PUT /api/voice-agents/:id**
  - Description: Update a voice agent
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string",
      "model": "string",
      "voice": "string",
      "status": "active|inactive",
      "systemPrompt": "string",
      "temperature": "number",
      "maxTokens": "number",
      "enableTools": "boolean",
      "enableMemory": "boolean",
      "knowledgeBase": "string",
      "voiceSettings": {
        "speed": "number",
        "pitch": "number",
        "accent": "string"
      }
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "model": "string",
      "voice": "string",
      "updatedAt": "string"
    }
    ```

- **DELETE /api/voice-agents/:id**
  - Description: Delete a voice agent
  - Response:
    ```json
    {
      "success": true,
      "message": "Voice agent deleted successfully"
    }
    ```

### Voice Agent Testing

- **POST /api/voice-agents/:id/test**
  - Description: Test a voice agent with a message
  - Request Body:
    ```json
    {
      "message": "string",
      "conversationId": "string" // Optional, for continuity
    }
    ```
  - Response:
    ```json
    {
      "responseText": "string",
      "responseAudioUrl": "string",
      "conversationId": "string"
    }
    ```

## Knowledge Base APIs

- **GET /api/knowledge-bases**
  - Description: Get list of all knowledge bases
  - Response:
    ```json
    {
      "knowledgeBases": [
        {
          "id": "string",
          "name": "string",
          "description": "string",
          "documentCount": "number",
          "createdAt": "string"
        }
      ]
    }
    ```

- **GET /api/knowledge-bases/:id**
  - Description: Get specific knowledge base details
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "documentCount": "number",
      "createdAt": "string",
      "documents": [
        {
          "id": "string",
          "name": "string",
          "type": "string",
          "size": "number",
          "createdAt": "string"
        }
      ]
    }
    ```

- **POST /api/knowledge-bases**
  - Description: Create a new knowledge base
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string"
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "documentCount": 0,
      "createdAt": "string"
    }
    ```

- **PUT /api/knowledge-bases/:id**
  - Description: Update a knowledge base
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string"
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "updatedAt": "string"
    }
    ```

- **DELETE /api/knowledge-bases/:id**
  - Description: Delete a knowledge base
  - Response:
    ```json
    {
      "success": true,
      "message": "Knowledge base deleted successfully"
    }
    ```

- **POST /api/knowledge-bases/:id/documents**
  - Description: Upload a document to a knowledge base
  - Request Body: Form data with file
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "type": "string",
      "size": "number",
      "createdAt": "string"
    }
    ```

- **DELETE /api/knowledge-bases/:id/documents/:documentId**
  - Description: Delete a document from a knowledge base
  - Response:
    ```json
    {
      "success": true,
      "message": "Document deleted successfully"
    }
    ```

## Workflow APIs

- **GET /api/workflows**
  - Description: Get list of all workflows
  - Response:
    ```json
    {
      "workflows": [
        {
          "id": "string",
          "name": "string",
          "description": "string",
          "status": "active|inactive",
          "createdAt": "string",
          "updatedAt": "string"
        }
      ]
    }
    ```

- **GET /api/workflows/:id**
  - Description: Get specific workflow details
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "createdAt": "string",
      "updatedAt": "string",
      "steps": [
        {
          "id": "string",
          "name": "string",
          "type": "string",
          "config": "object",
          "position": "number"
        }
      ]
    }
    ```

- **POST /api/workflows**
  - Description: Create a new workflow
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "steps": [
        {
          "name": "string",
          "type": "string",
          "config": "object",
          "position": "number"
        }
      ]
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "createdAt": "string"
    }
    ```

- **PUT /api/workflows/:id**
  - Description: Update a workflow
  - Request Body:
    ```json
    {
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "steps": [
        {
          "id": "string", // Optional for existing steps
          "name": "string",
          "type": "string",
          "config": "object",
          "position": "number"
        }
      ]
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "description": "string",
      "status": "active|inactive",
      "updatedAt": "string"
    }
    ```

- **DELETE /api/workflows/:id**
  - Description: Delete a workflow
  - Response:
    ```json
    {
      "success": true,
      "message": "Workflow deleted successfully"
    }
    ```

## Billing and Invoices APIs

- **GET /api/billing/subscription**
  - Description: Get current subscription details
  - Response:
    ```json
    {
      "id": "string",
      "plan": "string",
      "status": "active|canceled|past_due",
      "currentPeriodEnd": "string",
      "amount": "number",
      "currency": "string"
    }
    ```

- **GET /api/billing/invoices**
  - Description: Get list of all invoices
  - Response:
    ```json
    {
      "invoices": [
        {
          "id": "string",
          "amount": "number",
          "currency": "string",
          "status": "paid|pending|failed",
          "date": "string",
          "pdfUrl": "string"
        }
      ]
    }
    ```

- **GET /api/billing/invoices/:id**
  - Description: Get specific invoice details
  - Response:
    ```json
    {
      "id": "string",
      "amount": "number",
      "currency": "string",
      "status": "paid|pending|failed",
      "date": "string",
      "pdfUrl": "string",
      "items": [
        {
          "description": "string",
          "amount": "number",
          "quantity": "number"
        }
      ]
    }
    ```

- **POST /api/billing/subscription**
  - Description: Create or update subscription
  - Request Body:
    ```json
    {
      "plan": "string",
      "paymentMethodId": "string"
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "plan": "string",
      "status": "active",
      "currentPeriodEnd": "string"
    }
    ```

- **DELETE /api/billing/subscription**
  - Description: Cancel subscription
  - Response:
    ```json
    {
      "success": true,
      "message": "Subscription canceled successfully"
    }
    ```

## User Management APIs

- **GET /api/users/profile**
  - Description: Get current user profile
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "email": "string",
      "role": "string",
      "createdAt": "string"
    }
    ```

- **PUT /api/users/profile**
  - Description: Update user profile
  - Request Body:
    ```json
    {
      "name": "string",
      "email": "string"
    }
    ```
  - Response:
    ```json
    {
      "id": "string",
      "name": "string",
      "email": "string",
      "updatedAt": "string"
    }
    ```

- **PUT /api/users/password**
  - Description: Update user password
  - Request Body:
    ```json
    {
      "currentPassword": "string",
      "newPassword": "string"
    }
    ```
  - Response:
    ```json
    {
      "success": true,
      "message": "Password updated successfully"
    }
    ```

## Analytics APIs

- **GET /api/analytics/dashboard**
  - Description: Get dashboard analytics data
  - Response:
    ```json
    {
      "totalAgents": "number",
      "activeAgents": "number",
      "totalInteractions": "number",
      "interactionsToday": "number",
      "interactionsChart": [
        {
          "date": "string",
          "count": "number"
        }
      ],
      "topAgents": [
        {
          "id": "string",
          "name": "string",
          "interactions": "number"
        }
      ]
    }
    ```

- **GET /api/analytics/agents/:id**
  - Description: Get analytics for a specific agent
  - Response:
    ```json
    {
      "totalInteractions": "number",
      "interactionsToday": "number",
      "averageResponseTime": "number",
      "interactionsChart": [
        {
          "date": "string",
          "count": "number"
        }
      ],
      "topQueries": [
        {
          "query": "string",
          "count": "number"
        }
      ]
    }
    ```
