# Advanced Cloud Engineer Project: EC2 + Docker Compose + Nginx + PostgreSQL

## Project Goal
This project demonstrates creating a fully working AWS EC2 instance with a contarized web application and database. It shows understanding of infrastructure, conterization, networking, and security.

## Components
- **AWS EC2**: Ubuntu 24.04. LTS, ts3.micro, Security (SHH, HTTP, HTTPS)
- **Docker & Docker Compose**: Nginx, PostgreSQL
- **Monitoring**: Optional CloudWatch Dashboard for CPU, Memory, Network
- **Documentation & Screenshots**: Console screenshots and browser view

## Steps

- **Launch EC2 instance** with Ubuntu 24.04 LTS and securty groups
- **Connect via SSH**:
```bash
ssh -i my-key.pem ubuntu@<Public_IP>
```

## 3. Install Docker & Docker Compose
sudo apt update
sudo apt install -y docker.io docker-compose
sudo systemctl enable --now docker
sudo usermod -aG docker ubuntu

## 4. Create docker-compose.yml
```yaml
version: "3"
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
  db:
    image: postgres:15
    environment:
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypass
    volumes:
      - pgdata:/var/lib/postgresql/data

volumes:
  pgdata:
```

## 5. Run the application
```bash
docker-compose up -d
docker ps
```
## 6. Check in browser: http://<Public_IP> -> Nginx page.
## 7. Optional monitoring: CloudWatch dashboard
## 8. Screenshots for documentation: see /screenshots folder.