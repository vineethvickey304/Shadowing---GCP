Here’s a draft for a README file tailored to the project described in your report. Let me know if you'd like any adjustments or additions.

---

# Guestbook Application with Shadowing Mechanism in Google Cloud

## Overview
This project focuses on implementing a **shadowing mechanism** for a Guestbook application hosted in **Google Cloud**. Shadowing allows testing new application versions in a controlled, production-like environment, ensuring correctness and reliability before deploying updates to production. The approach is built upon **Google Kubernetes Engine (GKE)**, **Redis**, and various monitoring tools like **Grafana** and **Google Cloud Monitoring**.

---

## Features
- **Shadowing for Testing**: Mirrors production traffic to a shadow environment without impacting live services.
- **Microservices Architecture**: Modular design for scalability and maintainability.
- **Data Replication**: Ensures data consistency with Redis master-slave replication.
- **Traffic Splitting**: Uses Istio for seamless traffic mirroring.
- **Monitoring and Debugging**: Detects discrepancies via Google Cloud Monitoring and Grafana.
- **Versatile Use Cases**: Feature toggle testing, disaster recovery drills, security testing, and training.

---

## Architecture
### System Context
The application is containerized using **Docker** and orchestrated in **Kubernetes**. It employs a request splitter service that routes traffic to:
1. **Production Environment**: Processes live requests and sends responses back to end-users.
2. **Shadow Environment**: Processes duplicated traffic for testing, analyzing logs, and comparing metrics.

### Key Components
1. **Google Kubernetes Engine (GKE)**: Manages containerized microservices.
2. **Redis**: Handles data replication for consistent testing.
3. **Google Container Registry (GCR)**: Stores Dockerized application images.
4. **Istio**: Enables traffic mirroring between environments.
5. **Monitoring Tools**:
   - **Google Cloud Monitoring**: Tracks application performance.
   - **Grafana**: Provides visualization and insights into system metrics.

---

## Installation & Setup
### Prerequisites
- **Google Cloud Account** with permissions for GKE, GCR, and Istio.
- **Docker** and **kubectl** installed locally.

### Steps
1. **Clone the Repository**:
   ```bash
   git clone <repository_url>
   cd <repository_directory>
   ```

2. **Build Docker Images**:
   ```bash
   docker build -t gcr.io/<project_id>/guestbook:latest .
   docker push gcr.io/<project_id>/guestbook:latest
   ```

3. **Deploy Kubernetes Resources**:
   ```bash
   kubectl apply -f k8s/
   ```

4. **Configure Istio**:
   - Set up traffic mirroring between production and shadow environments using Istio configurations.

5. **Monitoring Setup**:
   - Integrate Google Cloud Monitoring and Grafana for observability.

---

## Usage
1. Access the **Guestbook Application** via the provided load balancer URL.
2. Analyze traffic and performance differences in the **shadow environment** using Grafana dashboards.
3. Modify and test new features safely without affecting production.

---

## Key Use Cases
1. **Feature Toggle Testing**: Test new features with minimal risk.
2. **Disaster Recovery Drills**: Simulate failures and validate recovery strategies.
3. **Security Testing**: Conduct vulnerability scans in a secure, isolated environment.
4. **Training**: Use the shadow environment to onboard new team members safely.

---

## References
- [Google Cloud Documentation](https://cloud.google.com/docs)
- [Redis Documentation](https://redis.io/docs)
- [Grafana Documentation](https://grafana.com/docs)

---

## Contributors
- **Mohammad-Al Fattah**
- **Sai Vineeth Karakavalasa**
- **Md. Ariful Islam**
- **Irvan Assiakoley**

