# CST8918 - Assignment 01: Weather Application Overview

This project consists of containerizing a Node.js Remix weather application using Docker and orchestrating its deployment locally using a Kubernetes cluster. The application connects securely to the OpenWeather API to retrieve live weather data for Algonquin College.

---

## 📊 Live Deployment Verification

Below is the verification screenshot showing the live application running successfully on `http://localhost:8081` alongside the healthy, active state of the Kubernetes components (`namespaces`, `services`, and `pods`).

<img width="1911" height="1022" alt="lab1 the weather app" src="https://github.com/user-attachments/assets/1903d033-19e9-47fb-9f35-eb24c1912247" />

---

## 🛠️ Project Components

* **Docker Containerization:** The application is packaged into a lightweight Linux container using a custom multi-stage `Dockerfile`.
* **Docker Hub Registry:** The compiled image is hosted publicly on Docker Hub at `ruaa991/cst8918-a01-weather-app:latest`.
* **Kubernetes Orchestration:** * **Namespace:** Isolated inside the logical `cst8918` workspace.
  * **Secret:** The OpenWeather API key is kept secure using an encrypted cluster secret.
  * **Deployment:** Spawns and manages 2 identical, redundant application pods.
  * **Service:** Configured as a `LoadBalancer` mapping internal traffic to local port `8081` to bypass native Windows port conflicts.

---

## 🚀 Quick Verification Commands

To check the architecture and running components of this deployment inside the cluster, run the following commands:

```bash
# View active logical workspace
kubectl get namespaces

# View network routing routing point
kubectl get services -n cst8918

# View running application pods
kubectl get pods -n cst8918
