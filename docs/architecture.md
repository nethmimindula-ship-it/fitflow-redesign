# FitFlow System Architecture

## Overview

FitFlow uses a scalable layered architecture that supports cross-platform access, secure user management, AI-powered recommendations, nutrition tracking, social features and real-time communication.

## Technology Stack

- Frontend: Flutter
- Backend: NestJS
- AI Service: Python FastAPI
- Database: PostgreSQL
- Authentication: AWS Cognito
- Cache: Redis
- Real-Time Communication: WebSockets
- File Storage: AWS S3

## High-Level Architecture

```text
                    ┌─────────────────────┐
                    │   Flutter Frontend  │
                    │   iOS / Android/Web │
                    └──────────┬──────────┘
                               │
                         REST / WebSocket
                               │
                    ┌──────────▼──────────┐
                    │    NestJS Backend   │
                    │      API Layer      │
                    └──────┬─────┬────────┘
                           │     │
              ┌────────────┘     └─────────────┐
              │                                │
     ┌────────▼────────┐              ┌────────▼────────┐
     │   PostgreSQL    │              │   Redis Cache   │
     │ Application Data│              │ Performance     │
     └─────────────────┘              └─────────────────┘
                           │
                    ┌──────▼─────────┐
                    │ FastAPI AI     │
                    │ AI Microservice│
                    └──────┬─────────┘
                           │
                    AI Recommendations

                    ┌─────────────────┐
                    │    AWS S3       │
                    │ Images / Files  │
                    └─────────────────┘

                    ┌─────────────────┐
                    │   AWS Cognito   │
                    │ Authentication  │
                    └─────────────────┘
