# Technical Documentation

This section provides a detailed **technical overview** of the **Food Recipe Web Application**, focusing on its **AWS architecture**, **data flow**, **authentication and authorization**, and **tech stack choices**.  
It extends the documentation created on **Day 2**, ensuring a complete understanding of both design and implementation.

# 4.  Architecture Overview

The application follows a **MERN stack deployment model** on AWS infrastructure.  
User requests are routed through **Route 53 (DNS)** to the EC2 instance via an **Elastic IP**, where NGINX handles request forwarding, SSL termination, and static file serving.  
The backend is managed using **PM2**, ensuring process stability, while persistent data is stored securely in **MongoDB Atlas (Free M0 cluster)**.

---

<!-- ## 4.1 AWS Deployment Diagram

```mermaid
flowchart TD
    %% --- User Layer ---
    A[Internet Users<br>(Browser Requests)]

    %% --- DNS Layer ---
    A -->|Access yourdomain.com| B[Route 53 (DNS)]
    B -->|Resolves to Elastic IP (1.2.3.4)| C[AWS EC2 Instance<br>(t2.micro - Free Tier)]

    %% --- EC2 Infrastructure ---
    subgraph C[AWS EC2 Instance<br>Elastic IP: 1.2.3.4]
        direction TB

        %% --- Web Server Layer ---
        subgraph N[NGINX<br>Port 80 / 443]
            N1[• Reverse Proxy<br>• SSL/TLS Termination<br>• Static & Image File Serving]
        end

        %% --- Application Layer ---
        N --> F[Frontend (React Build)<br>Route: /<br>Served from dist/]
        N --> B[Backend (Node.js + Express)<br>Route: /api<br>Port: 5000]

        %% --- File Upload Layer ---
        B --> U[Multer File Uploads<br>/backend/public/images<br>Stored Recipe Images]
        U -->|Served via /images/| N

        %% --- Process Management ---
        B --> P[PM2 Process Manager<br>Auto-Restart + Monitoring]
    end

    %% --- External Services ---
    C --> D[(MongoDB Atlas<br>Free M0 Cluster - 512MB)]
    C --> CW[(Optional: AWS CloudWatch<br>Logs & Metrics)]

``` -->
