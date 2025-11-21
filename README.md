# 🛍️ Online Boutique - Cloud-Native Microservice

[![Stars](https://img.shields.io/github/stars/GoogleCloudPlatform/microservices-demo?style=social)](https://github.com/GoogleCloudPlatform/microservices-demo)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)

> A modern, cloud-first e-commerce application demonstrating microservices architecture and Google Cloud technologies

[Documentation](#documentation) | [Architecture](#architecture) | [Quick Start](#-quick-start)

---

## 📋 Problem Statement

Modern enterprises face significant challenges when building and deploying scalable applications:

- **Monolithic Limitations** 🏗️ - Traditional monolithic applications are difficult to scale, maintain, and deploy
- **Technology Lock-in** 🔒 - Teams struggle to use the best language/framework for each service
- **Observability Gaps** 👁️ - Lack of proper monitoring and tracing across distributed systems
- **Cloud Migration Complexity** ☁️ - Difficulty in modernizing legacy applications for cloud-native environments
- **DevOps Challenges** 🔄 - Complex CI/CD pipelines and deployment strategies

## 💡 Solution

**Online Boutique** is a comprehensive microservices demo application that addresses these challenges by showcasing:

✨ **Polyglot Microservices Architecture** - 11 independent services written in different languages (Go, C#, Node.js, Python, Java) communicating via gRPC

🚀 **Cloud-Native Best Practices** - Kubernetes-first design with container orchestration, auto-scaling, and service mesh integration

📊 **Complete Observability** - Built-in support for distributed tracing, logging, and monitoring using Cloud Operations

🔧 **Modern DevOps Workflow** - GitOps, Infrastructure as Code (Terraform), and automated deployments

🌐 **Real-World E-commerce Features** - Product catalog, shopping cart, checkout, payment processing, and recommendations

---

## 🏗️ Architecture

Online Boutique demonstrates a realistic microservices architecture with inter-service communication:

![Architecture Diagram](docs/img/architecture-diagram.png)

### Services Overview

| Service | Language | Description |
|---------|----------|-------------|
| 🎨 **frontend** | Go | HTTP server serving the web UI |
| 🛒 **cartservice** | C# | Shopping cart management with Redis |
| 📦 **productcatalogservice** | Go | Product inventory and search |
| 💱 **currencyservice** | Node.js | Real-time currency conversion |
| 💳 **paymentservice** | Node.js | Payment processing (mock) |
| 📮 **shippingservice** | Go | Shipping cost calculation |
| 📧 **emailservice** | Python | Order confirmation emails |
| ✅ **checkoutservice** | Go | Order orchestration |
| 🤖 **recommendationservice** | Python | AI-powered product recommendations |
| 📣 **adservice** | Java | Contextual advertising |
| 🔄 **loadgenerator** | Python/Locust | Realistic traffic simulation |

---

## 🛠️ Tech Stack

### Languages & Frameworks
- ![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white) **Go** - Frontend, Product Catalog, Shipping, Checkout
- ![C#](https://img.shields.io/badge/C%23-239120?style=flat&logo=c-sharp&logoColor=white) **C# / .NET** - Cart Service
- ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white) **Node.js** - Currency, Payment Services
- ![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white) **Python** - Email, Recommendation, Load Generator
- ![Java](https://img.shields.io/badge/Java-007396?style=flat&logo=java&logoColor=white) **Java** - Ad Service

### Infrastructure & Platform
- ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat&logo=kubernetes&logoColor=white) **Kubernetes** - Container orchestration
- ![GKE](https://img.shields.io/badge/GKE-4285F4?style=flat&logo=google-cloud&logoColor=white) **Google Kubernetes Engine (GKE)** - Managed Kubernetes
- ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white) **Docker** - Containerization
- ![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat&logo=terraform&logoColor=white) **Terraform** - Infrastructure as Code

### Communication & Data
- ![gRPC](https://img.shields.io/badge/gRPC-244c5a?style=flat&logo=grpc&logoColor=white) **gRPC** - Inter-service communication
- ![Protocol Buffers](https://img.shields.io/badge/Protobuf-4285F4?style=flat) **Protocol Buffers** - Service contracts
- ![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white) **Redis / Memorystore** - Session & cart storage
- ![Spanner](https://img.shields.io/badge/Spanner-4285F4?style=flat&logo=google-cloud&logoColor=white) **Cloud Spanner** - Distributed SQL database
- ![AlloyDB](https://img.shields.io/badge/AlloyDB-4285F4?style=flat&logo=google-cloud&logoColor=white) **AlloyDB** - PostgreSQL-compatible database

### Service Mesh & Observability
- ![Istio](https://img.shields.io/badge/Istio-466BB0?style=flat&logo=istio&logoColor=white) **Istio / Cloud Service Mesh** - Traffic management & security
- ![Cloud Operations](https://img.shields.io/badge/Cloud%20Operations-4285F4?style=flat&logo=google-cloud&logoColor=white) **Cloud Operations** - Monitoring, logging, tracing
- **Locust** - Performance testing

### AI/ML
- ![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat&logo=google&logoColor=white) **Gemini** - AI-powered recommendations

---

## 🔧 Tools Used

- **kubectl** - Kubernetes CLI
- **gcloud** - Google Cloud SDK
- **Helm** - Kubernetes package manager
- **Kustomize** - Kubernetes configuration management
- **Skaffold** - Local development workflow
- **Git** - Version control
- **Protocol Buffer Compiler** - protoc for gRPC definitions

---

## 🚀 Quick Start

### Prerequisites
- Google Cloud Project
- `gcloud`, `git`, and `kubectl` installed

### Deploy to GKE

```bash
# Clone the repository
git clone --depth 1 --branch v0 https://github.com/GoogleCloudPlatform/microservices-demo.git
cd microservices-demo/

# Set project and region
export PROJECT_ID=<YOUR_PROJECT_ID>
export REGION=us-central1

# Enable required APIs
gcloud services enable container.googleapis.com --project=${PROJECT_ID}

# Create GKE cluster
gcloud container clusters create-auto online-boutique \
  --project=${PROJECT_ID} --region=${REGION}

# Deploy the application
kubectl apply -f ./release/kubernetes-manifests.yaml

# Wait for pods to be ready
kubectl get pods

# Get the external IP
kubectl get service frontend-external | awk '{print $4}'
```

Visit `http://EXTERNAL_IP` in your browser! 🎉

---

## 🔮 Future Scope

### Planned Enhancements

- [ ] 🤖 **Advanced AI Integration** - Enhanced product recommendations using Vertex AI
- [ ] 🌍 **Multi-Region Deployment** - Global load balancing and geo-distribution
- [ ] 🔐 **Enhanced Security** - mTLS, OAuth2, and advanced RBAC policies
- [ ] 📱 **Mobile Application** - Native iOS/Android apps
- [ ] 🧪 **Chaos Engineering** - Resilience testing with Chaos Mesh
- [ ] 📊 **Advanced Analytics** - Real-time dashboards with BigQuery and Looker
- [ ] 🎯 **A/B Testing Framework** - Feature flags and experimentation platform
- [ ] 🔄 **GitOps Workflow** - ArgoCD/Flux integration for automated deployments
- [ ] 💬 **Event-Driven Architecture** - Pub/Sub integration for async communication
- [ ] 🌐 **Multi-Cloud Support** - AWS EKS and Azure AKS deployment guides
- [ ] 🎨 **UI/UX Improvements** - Modern frontend framework migration (React/Vue)
- [ ] 📦 **Inventory Management** - Real-time stock tracking and alerts

### Community Contributions Welcome! 🤝

We're always looking for contributions! Whether it's:
- 🐛 Bug fixes
- ✨ New features
- 📚 Documentation improvements
- 🌍 Translations
- 💡 Ideas and suggestions

---

## 📚 Documentation

- [Development Guide](docs/development-guide.md) - Local development setup
- [Deployment Variations](kustomize/) - Custom deployment configurations
- [API Documentation](protos/) - gRPC service definitions

---

## 🎬 Featured Demos & Talks

- 🎤 [KubeCon EU 2019 - Istio Multicluster Gateways](https://www.youtube.com/watch?v=Example)
- 📺 [Google Cloud Next'18 - GKE On-Prem Demo](https://www.youtube.com/watch?v=Example)
- 📝 [Platform Engineering in Action with Score and Humanitec](https://example.com)
- 🔗 [Service Mesh Integration Tutorials](docs/service-mesh.md)

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

---

## 🌟 Show Your Support

If you find this project helpful, please ⭐ star this repository!

---

## 📞 Contact & Support

- 📧 Report issues on [GitHub Issues](https://github.com/GoogleCloudPlatform/microservices-demo/issues)
- 💬 Join the discussion on [Google Groups](https://groups.google.com/forum/#!forum/microservices-demo)
- 📖 Read more on [Google Cloud Blog](https://cloud.google.com/blog)

---

<div align="center">
  <strong>Built with ❤️ by Armaan</strong>
  <br/>
  <sub>Demonstrating modern cloud-native application development</sub>
</div>
