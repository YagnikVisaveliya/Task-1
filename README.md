# nodejs-demo-app 🚀

![Docker Pulls](https://img.shields.io/docker/pulls/yagnik0167/nodejs-demo-app)
![Version](https://img.shields.io/badge/version-1.0.0-blue)

> Automated CI/CD pipeline that builds, tests, and ships a Docker image to DockerHub on every push.

---

## ⚙️ CI/CD Pipeline

Every push to `main` triggers this automated flow:

---

## 🐳 Docker Versioning

| Tag       | Description            |
|-----------|------------------------|
| `latest`  | Always the newest build |
| `v1.0.0`  | Stable release          |
| `v2.0.0`  | Feature update          |

> Each push auto-generates a new versioned image — old versions are never deleted.

---

## 🔁 GitHub Actions Workflow

```yaml
on:
  push:
    branches: [main]

jobs:
  build-and-deploy:
    steps:
      - Checkout Code
      - Install & Test        # npm test (13 tests)
      - Build Docker Image    # :latest + :vX.X.X
      - Push to DockerHub     # yagnik0167/nodejs-demo-app
```

---

**DockerHub →** [yagnik0167/nodejs-demo-app](https://hub.docker.com/r/yagnik0167/nodejs-demo-app)  
**Author →** [@yagnik0167](https://github.com/yagnik0167)
