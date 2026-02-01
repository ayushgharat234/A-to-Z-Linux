# CI/CD Concepts

CI/CD (Continuous Integration and Continuous Deployment) is the practice of automating the delivery of software.

---

## 1. What is CI? (Continuous Integration)

Developers merge their code changes into a central repository frequently.
*   **Automated Tests**: Every commit triggers a test suite.
*   **Goal**: Find bugs early.

## 2. What is CD? (Continuous Deployment)

Automatically release the code to production if it passes tests.
*   **Goal**: Deliver features safely and quickly.

---

## 3. The Pipeline

A pipeline is a set of steps.

1.  **Code**: You push to GitHub.
2.  **Build**: The CI server compiles the code/builds a Docker image.
3.  **Test**: Run unit tests (`npm test`, `pytest`).
4.  **Deploy**: If successful, push to the server.

---

## 4. Common Tools

### GitHub Actions
The most popular tool today. Defined in `.github/workflows/main.yml`.

**Example Workflow:**
```yaml
name: CI
on: [push]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm install
      - run: npm test
```

### Jenkins
The "grandfather" of CI tools. Extremely powerful but requires maintenance.

### GitLab CI
Integrated directly into GitLab. Uses `.gitlab-ci.yml`.

---

## Summary
*   **CI**: Test code automatically.
*   **CD**: Deploy code automatically.
*   **Pipeline**: The path from Git to Production.
