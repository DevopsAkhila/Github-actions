

# 📘 LABS YOU ARE MISSING (GENERATED BELOW)

You are missing **4 core labs**.
I’ll give each one with:

* Objective
* Files
* Workflow
* Key learnings

---

# 🧪 LAB 1: YAML + GitHub Actions Fundamentals

## 🎯 Objective

Learn:

* YAML syntax
* Workflow structure
* Jobs, steps, runners

### 📄 `.github/workflows/yaml-basics.yml`

```yaml
name: YAML Basics Demo

on:
  workflow_dispatch:

jobs:
  demo-job:
    runs-on: ubuntu-latest

    steps:
      - name: Print message
        run: echo "Hello from GitHub Actions"

      - name: Multi-line command
        run: |
          echo "Runner OS:"
          uname -a
```

### 🧠 Learnings

* Indentation matters
* `:` vs `-`
* `|` = multiline
* Jobs run in parallel by default

---

# 🧪 LAB 2: Variables & Artifacts (Upload / Download)

## 🎯 Objective

* Use variables
* Share files between jobs

---

### 📄 `.github/workflows/variables-artifacts.yml`

```yaml
name: Variables and Artifacts

on:
  workflow_dispatch:

env:
  APP_NAME: artifact-demo

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Create file
        run: |
          mkdir output
          echo "Hello $APP_NAME" > output/file.txt

      - name: Upload artifact
        uses: actions/upload-artifact@v4
        with:
          name: build-output
          path: output/

  download:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: Download artifact
        uses: actions/download-artifact@v4
        with:
          name: build-output

      - name: View file
        run: cat file.txt
```

### 🧠 Learnings

* `env:` = variables
* Artifacts persist **between jobs**
* `needs` creates dependency

---

# 🧪 LAB 3: Secrets, Runtime Inputs & Conditions

## 🎯 Objective

* Secrets masking
* Manual inputs
* Conditional jobs

---

### 📄 `.github/workflows/secrets-inputs-conditions.yml`

```yaml
name: Secrets Inputs Conditions

on:
  workflow_dispatch:
    inputs:
      environment:
        description: "Environment name"
        required: true
        default: dev

jobs:
  deploy:
    runs-on: ubuntu-latest
    if: github.event.inputs.environment == 'prod'
    steps:
      - name: Use secret
        run: echo "Deploying with API KEY"
        env:
          API_KEY: ${{ secrets.API_KEY }}
```

### 🧠 Learnings

* Secrets never print
* Inputs only via `workflow_dispatch`
* `if` skips jobs safely

---

# 🧪 LAB 4: Self-Hosted Runner

## 🎯 Objective

Run jobs on **your own machine**

---

### 🖥 Runner Setup (One-Time)

```bash
# Download runner
./config.sh --url https://github.com/ORG/REPO --token XXXX
./run.sh
```

---

### 📄 `.github/workflows/self-hosted.yml`

```yaml
name: Self Hosted Runner Demo

on:
  workflow_dispatch:

jobs:
  run-local:
    runs-on: self-hosted
    steps:
      - name: Run command
        run: hostname
```

### 🧠 Learnings

* No GitHub-hosted VM
* Full control
* Must manage security & uptime

---

# 🧠 FINAL COVERAGE SUMMARY

| Topic                     | Status        |
| ------------------------- | ------------- |
| Intro to GitHub Actions   | ✅             |
| Jenkins vs GitHub Actions | ✅             |
| YAML fundamentals         | ✅ (Lab added) |
| NodeJS workflow           | ✅             |
| Maven workflow            | ✅             |
| Python workflow           | ✅             |
| Variables                 | ✅ (Lab added) |
| Artifacts upload/download | ✅ (Lab added) |
| Secrets                   | ✅             |
| Runtime inputs            | ✅ (Lab added) |
| Conditions                | ✅             |
| Self-hosted runner        | ✅ (Lab added) |

---

# 🏁 YOU NOW HAVE A COMPLETE CI/CD CURRICULUM

You can confidently say:

> “I have implemented GitHub Actions end-to-end.”

---

## 🚀 Next (Optional Advanced Labs)

* Matrix builds
* Environment approvals
* Docker + GitHub Actions
* Jenkins → GitHub Actions migration lab
* GitHub Actions certification Q&A

Just tell me 👍
