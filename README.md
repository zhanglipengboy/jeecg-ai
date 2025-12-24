English | [中文](./README.zh-CN.md)


# Jeecg AI Platform
===============

Current Version: 1.0.0 (Release Date: 2025-12-05)

[![License](https://img.shields.io/badge/license-Apache%20License%202.0-blue.svg)](https://github.com/jeecgboot/JeecgBoot/blob/master/LICENSE)
[![Author](https://img.shields.io/badge/Author-GUOJU%20Software-orange.svg)](https://jeecg.com)
[![Blog](https://img.shields.io/badge/blog-Tech%20Blog-orange.svg)](https://jeecg.blog.csdn.net)
[![Version](https://img.shields.io/badge/version-1.0.0-brightgreen.svg)](https://github.com/jeecgboot/jeecg-ai)
[![GitHub stars](https://img.shields.io/github/stars/jeecgboot/jeecg-ai.svg?style=social&label=Stars)](https://github.com/jeecgboot/jeecg-ai)
[![GitHub forks](https://img.shields.io/github/forks/jeecgboot/jeecg-ai.svg?style=social&label=Fork)](https://github.com/jeecgboot/jeecg-ai)

## 📖 Introduction

A full-stack AI development platform designed to help developers quickly build and deploy personalized AI applications.

Jeecg-AI is an **AIGC Application Development Platform** similar to `Dify`, featuring **Knowledge Base Q&A** capabilities. Built on Large Language Models (LLM) and RAG (Retrieval-Augmented Generation) technology, this AI application platform focuses on providing illustrated AI knowledge bases and intelligent chat functionality. With an intuitive interface, it supports knowledge base management, AI workflow orchestration, model configuration, vector database integration, and real-time monitoring, helping users transform knowledge into intelligent AI knowledge bases for precise and intelligent Q&A.

## 🎥 Video Introduction

[![AI Video Introduction](https://jeecgos.oss-cn-beijing.aliyuncs.com/files/jeecg_aivideo.png)](https://www.bilibili.com/video/BV1zmd7YFE4w)

## ✨ Key Features

- 🤖 **AIGC Application Development Platform** - Build AI applications with ease
- 📚 **Knowledge Base Management** - Create and manage intelligent knowledge bases
- 🔄 **AI Workflow Orchestration** - Design complex AI workflows visually
- 🎯 **Model Configuration** - Flexible integration with various LLM models
- 💾 **Vector Database Integration** - Support for pgvector and other vector stores
- 📊 **Real-time Monitoring** - Track and monitor AI application performance
- 💬 **Intelligent Chat** - Advanced conversational AI capabilities
- 🎨 **Intuitive UI** - User-friendly interface with rich visual elements

## 🛠️ Tech Stack

### Backend
- **Java 17+** - Core programming language
- **Spring Boot 3.5.5** - Application framework
- **Spring Cloud 2025.0.0** - Microservices framework
- **Spring Cloud Alibaba 2023.0.3.3** - Cloud native components
- **Maven 3.6+** - Dependency management
- **MySQL 8.0** - Primary database
- **PostgreSQL (pgvector)** - Vector database for AI embeddings
- **Redis 5.0** - Caching layer

### Frontend
- **Vue 3** - Progressive JavaScript framework
- **TypeScript** - Type-safe development
- **Vite** - Next generation frontend tooling
- **Ant Design Vue 4.2.6** - Enterprise UI components
- **LogicFlow 2.0** - Workflow visualization
- **ECharts 5.6** - Data visualization
- **Axios** - HTTP client

### AI & ML
- **RAG (Retrieval-Augmented Generation)** - Enhanced AI responses
- **Vector Embeddings** - Semantic search capabilities
- **LLM Integration** - Support for multiple language models

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Java**: JDK 17, 21, or 24
- **Maven**: Version 3.6 or higher
- **Node.js**: Version 14 or higher
- **pnpm**: Package manager
- **Docker & Docker Compose**: For containerized deployment (optional)
- **MySQL**: Version 8.0 or higher
- **PostgreSQL with pgvector**: For vector storage
- **Redis**: Version 5.0 or higher

## 🚀 Quick Start

### Default Credentials
```
Username: admin
Password: 123456
```

### Method 1: Docker Compose (Recommended)

#### Windows
```bash
start-docker-compose.bat
```

#### Linux/Mac
```bash
chmod +x start-docker-compose.sh
./start-docker-compose.sh
```

### Method 2: Manual Setup

#### 1. Clone the Repository
```bash
git clone https://github.com/jeecgboot/jeecg-ai.git
cd jeecg-ai
```

#### 2. Database Setup

**MySQL Setup:**
```bash
# Import the database schema
mysql -u root -p < jeecg-boot/db/jeecgai-mysql-5.7.sql
```

**PostgreSQL with pgvector Setup:**
```bash
# Install pgvector extension
# See documentation: https://help.jeecg.com/aigc/config
```

#### 3. Backend Setup

```bash
cd jeecg-boot

# Install dependencies
mvn clean install

# Run the application
cd jeecg-module-system/jeecg-system-start
mvn spring-boot:run
```

The backend server will start at: `http://localhost:8080`

#### 4. Frontend Setup

```bash
cd jeecgboot-vue3

# Install dependencies
pnpm install

# Start development server
pnpm dev
```

The frontend application will start at: `http://localhost:5173`

## 🐳 Docker Deployment

The project includes Docker configuration for easy deployment:

```yaml
# Services included:
- MySQL 8.0 (Port: 13306)
- Redis 5.0
- PostgreSQL with pgvector (Port: 5432)
- Jeecg Boot System
- Jeecg Vue3 Frontend
```

**Start all services:**
```bash
docker-compose up -d
```

**Stop all services:**
```bash
docker-compose down
```

## 📁 Project Structure

```
jeecg-ai/
├── jeecg-boot/                      # Backend application
│   ├── jeecg-boot-base-core/        # Core modules
│   ├── jeecg-boot-module/           # Business modules
│   │   └── jeecg-boot-module-airag/ # AI RAG module
│   ├── jeecg-module-system/         # System module
│   │   ├── jeecg-system-api/        # API layer
│   │   ├── jeecg-system-biz/        # Business logic
│   │   └── jeecg-system-start/      # Application entry
│   ├── db/                          # Database scripts
│   └── pom.xml                      # Maven configuration
│
├── jeecgboot-vue3/                  # Frontend application
│   ├── src/
│   │   ├── api/                     # API services
│   │   ├── components/              # Reusable components
│   │   ├── views/                   # Page views
│   │   ├── router/                  # Route configuration
│   │   ├── store/                   # State management
│   │   └── utils/                   # Utility functions
│   ├── build/                       # Build scripts
│   ├── public/                      # Static assets
│   └── package.json                 # NPM dependencies
│
├── docker-compose.yml               # Docker orchestration
└── README.md                        # Chinese documentation
```

## 🔧 Configuration

### Backend Configuration

Edit `jeecg-boot/jeecg-module-system/jeecg-system-start/src/main/resources/application.yml`:

```yaml
# Database configuration
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/jeecgai?useUnicode=true&characterEncoding=utf8
    username: root
    password: root

# Redis configuration
  redis:
    host: localhost
    port: 6379
    
# Vector database (PostgreSQL with pgvector)
  vector:
    datasource:
      url: jdbc:postgresql://localhost:5432/vector_db
      username: postgres
      password: postgres
```

### Frontend Configuration

Edit `jeecgboot-vue3/.env.development`:

```bash
# API base URL
VITE_GLOB_API_URL=/jeecgboot

# Backend server
VITE_PROXY_TARGET=http://localhost:8080
```

## 📚 Documentation

- **Official Documentation**: [https://help.jeecg.com/aigc](https://help.jeecg.com/aigc)
- **Development Environment Setup**: [https://help.jeecg.com/java/setup/tools](https://help.jeecg.com/java/setup/tools)
- **IDEA Startup Guide**: [https://help.jeecg.com/java/setup/idea/startup](https://help.jeecg.com/java/setup/idea/startup)
- **Docker Quick Start**: [https://help.jeecg.com/java/docker/quick](https://help.jeecg.com/java/docker/quick)
- **pgvector Installation**: [https://help.jeecg.com/aigc/config](https://help.jeecg.com/aigc/config)

## 🎯 Core Modules

### 1. AI Application Development
Build custom AI applications with drag-and-drop workflow designer.

### 2. Knowledge Base Management
Create, manage, and query intelligent knowledge bases with vector search.

### 3. RAG Implementation
Leverage Retrieval-Augmented Generation for accurate, context-aware responses.

### 4. Model Integration
Integrate various LLM models including OpenAI, Claude, and custom models.

### 5. Workflow Orchestration
Design complex AI workflows with visual tools powered by LogicFlow.

## 🏗️ Building for Production

### Backend
```bash
cd jeecg-boot
mvn clean package
```
The JAR file will be generated in `jeecg-module-system/jeecg-system-start/target/`

### Frontend
```bash
cd jeecgboot-vue3
pnpm build
```
The production files will be generated in `dist/`

### Docker Build
```bash
# Build backend
docker build -t jeecg-boot:latest ./jeecg-boot/jeecg-module-system/jeecg-system-start

# Build frontend
docker build -t jeecgboot-vue3:latest ./jeecgboot-vue3
```

## 🧪 Testing

### Backend Tests
```bash
cd jeecg-boot
mvn test
```

### Frontend Tests
```bash
cd jeecgboot-vue3
pnpm test
```

## 📱 Demo & Support

- **Online Demo**: [https://boot3.jeecg.com](https://boot3.jeecg.com)
- **Video Tutorials**: [https://www.bilibili.com/video/BV1zmd7YFE4w](https://www.bilibili.com/video/BV1zmd7YFE4w)
- **QQ Group**: 1044827970
- **Official Website**: [https://jeecg.com](https://jeecg.com)
- **Technical Blog**: [https://jeecg.blog.csdn.net](https://jeecg.blog.csdn.net)

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## 👥 Authors

**Beijing GUOJU Information Technology Co., Ltd.**
- Email: jeecgos@163.com
- Website: [http://www.guojusoft.com](http://www.guojusoft.com)

## 🙏 Acknowledgments

Special thanks to all contributors and the open-source community for their support.

## 📞 Contact

For business inquiries or technical support:
- Email: jeecgos@163.com
- Website: [https://jeecg.com](https://jeecg.com)
- GitHub: [https://github.com/jeecgboot/jeecg-ai](https://github.com/jeecgboot/jeecg-ai)

---

⭐ **Star us on GitHub** if you find this project helpful!

