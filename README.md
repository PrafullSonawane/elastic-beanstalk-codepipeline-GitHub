# Elastic Beanstalk CI/CD Pipeline (GitHub → CodePipeline → Elastic Beanstalk)

This repository demonstrates a CI/CD setup where changes pushed to GitHub are automatically deployed to AWS Elastic Beanstalk using AWS CodePipeline (with optional CodeBuild).

---

## Project Summary
- **Repository Name:** elastic-beanstalk-CICDpipeline-GitHub  
- **Local Folder:** D:\GitHub\AWS\CICD  
- **Purpose:** Automate deployments from GitHub to Elastic Beanstalk using CodePipeline.

---

## Architecture

```
  +-----------+         +----------------+        +-------------------+
  | Developer |  push   |  GitHub Source |  --->  |  AWS CodePipeline |
  | (local PC)|-------->|  (this repo)   |        +-------------------+
  +-----------+         +----------------+                 |
                                                            v
                                               +-------------------------+
                                               | (Optional) AWS CodeBuild|
                                               |   Build & package app   |
                                               +-------------------------+
                                                            |
                                                            v
                                               +-------------------------+
                                               | AWS Elastic Beanstalk   |
                                               |  (Environment / App)    |
                                               +-------------------------+
                                                            |
                                                    Live Web Application
```

**Flow:** Developer commits → GitHub triggers CodePipeline → (CodeBuild builds) → Elastic Beanstalk deploys → New version live.

---

## Repo Contents
- `index.php` / `index.html` → Application code hosted by Elastic Beanstalk  
- `buildspec.yml` (optional) → Build instructions for CodeBuild  
- `screenshots/` → Pipeline and Elastic Beanstalk environment screenshots  
- `README.md` → Project documentation  
- `.env.example` → Placeholder for environment variables (never commit real `.env`)

---

## Deployment Steps
1. Commit and push code to GitHub.  
2. CodePipeline detects changes and runs automatically.  
3. (Optional) CodeBuild builds artifacts.  
4. Elastic Beanstalk deploys the latest version.  
5. Application available via EB environment URL or custom domain.

---

## Best Practices
- Do not commit secrets (use `.env`, AWS Secrets Manager, or Parameter Store).  
- Use IAM roles with least privileges.  
- Enable rolling updates and health checks in Elastic Beanstalk.  
- Store screenshots in `/screenshots` and link them in this README.

---

## Screenshots
Place screenshots inside `/screenshots` folder:  
- CodePipeline stages  
- CodeBuild logs  
- Elastic Beanstalk environment health  
- Final deployed app

---

## Author
Created by **Prafull Sonawane**
