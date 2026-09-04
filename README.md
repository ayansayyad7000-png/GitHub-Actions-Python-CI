<div align="center">

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=700&size=28&duration=2200&pause=650&color=2088FF&center=true&vCenter=true&repeat=true&width=900&lines=GitHub+Actions+Python+CI;Workflow+%E2%86%92+Jobs+%E2%86%92+Tests+%E2%86%92+Build;CI%2FCD+Practical+by+Ayan+Sayyad" alt="GitHub Actions Python CI animated header" />

# ⚙️ GitHub Actions Python CI Practical

### Beginner-Friendly Step-by-Step Notes by Ayan Sayyad

![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)
![YAML](https://img.shields.io/badge/YAML-Workflow-CB171E?style=for-the-badge&logo=yaml&logoColor=white)
![Level](https://img.shields.io/badge/Level-Beginner%20Friendly-238636?style=for-the-badge)

**Workflows • Jobs • Triggers • Python CI • Tests • Artifacts • Cache • Slack Notifications**

</div>

---

## 🚀 Start Here

Follow this repository from top to bottom. Do not jump between sections.

```text
First Workflow
      ↓
Multi-Line Commands
      ↓
Using Actions
      ↓
Multiple Jobs
      ↓
Sequential Jobs
      ↓
Multiple Triggers
      ↓
Skip CI
      ↓
Python CI
      ↓
Unit Tests
      ↓
Artifacts
      ↓
Dependency Cache
      ↓
Build + Test + Notify
```

---

## 📚 Practical Index

| # | Topic | Main Goal |
|---:|---|---|
| 01 | Creating First Workflow | Create and run your first workflow |
| 02 | Multi Line Shell Commands | Run multiple commands in one step |
| 03 | Using Actions | Use actions from GitHub Marketplace |
| 04 | Running Multiple Jobs | Run more than one job |
| 05 | Sequential Jobs | Run one job after another |
| 06 | Multiple Triggers | Run on manual trigger and push |
| 07 | Skipping a Workflow | Skip CI for a commit |
| 08 | Python CI | Run Python in GitHub Actions |
| 09 | Running Test Cases | Run unit tests automatically |
| 10 | Job Artifacts | Build and upload output files |
| 11 | Dependency Cache | Speed up dependency installation |
| 12 | Build, Test & Notify | Add Slack notification to CI |

---

## 1. Creating First Workflow

### Step 1
Open your GitHub repository.

### Step 2
Open the `Actions` tab.

### Step 3
Click `Setup a workflow yourself`.

### Step 4
In VS Code, install the `GitHub Actions` plugin and sign in to GitHub.

### Step 5
Create this folder in your project:

```text
.github/workflows
```

### Step 6
Inside this folder, create a workflow file:

```text
my-actions.yml
```

### Step 7
Add this code:

```yaml
name: my-workflow
on: workflow_dispatch
jobs:
  first-job:
    runs-on: ubuntu-latest
    steps:
      - name: first-step
        run: echo "Hello World"
      - name: second-step
        run: echo "This is the second step"
```

### Step 8
Commit and push:

```bash
git add .
git commit -m "Add first workflow"
git push
```

### Step 9
Open the `Actions` tab on GitHub and check the workflow.

---

## 2. Running Multi Line Shell Commands

### Step 1
Keep this code in `my-actions.yml`:

```yaml
name: my-workflow
on: workflow_dispatch
jobs:
  first-job:
    runs-on: ubuntu-latest
    steps:
      - name: first-step
        run: |
          echo "Hello World"
          echo "This is the second step"
```

### Step 2
Commit and push:

```bash
git add .
git commit -m "Add multiline commands"
git push
```

### Step 3
Check the result in the GitHub `Actions` tab.

---

## 3. Using Actions

### Step 1
Add the checkout action to the workflow:

```yaml
name: my-workflow
on: workflow_dispatch
jobs:
  first-job:
    runs-on: ubuntu-latest
    steps:
      - name: first-step
        run: echo "Hello World"
      - name: github checkout
        uses: actions/checkout@v6
```

### Step 2
Commit and push:

```bash
git add .
git commit -m "Use checkout action"
git push
```

### Step 3
Check the GitHub `Actions` tab.

GitHub Actions Marketplace:

```text
https://github.com/marketplace?type=actions
```

---

## 4. Running Multiple Jobs

### Step 1
Create two jobs in the workflow:

```yaml
name: my-workflow
on: workflow_dispatch
jobs:
  first-job:
    runs-on: ubuntu-latest
    steps:
      - name: first-step
        run: echo "Hello World"
      - name: second-step
        uses: actions/checkout@v6

  second-job:
    runs-on: ubuntu-latest
    steps:
      - name: test-step
        run: echo "This is a test step"
      - name: test-code
        uses: actions/checkout@v6
```

### Step 2
Commit and push:

```bash
git add .
git commit -m "Add multiple jobs"
git push
```

### Step 3
Check both jobs in the GitHub `Actions` tab.

---

## 5. Running Multiple Jobs - Sequential

### Step 1
Use `needs` to run the second job after the first job:

```yaml
name: my-workflow
on: workflow_dispatch
jobs:
  first-job:
    runs-on: ubuntu-latest
    steps:
      - name: first-step
        run: echo "Hello World"
      - name: second-step
        uses: actions/checkout@v6

  second-job:
    needs: first-job
    runs-on: ubuntu-latest
    steps:
      - name: test-step
        run: echo "This is a test step"
      - name: test-code
        uses: actions/checkout@v6
```

### Step 2
Commit and push:

```bash
git add .
git commit -m "Run jobs sequentially"
git push
```

### Step 3
Check the GitHub `Actions` tab.

---

## 6. Running Multiple Triggers

### Step 1
Use both manual and push triggers:

```yaml
name: my-workflow
on: [workflow_dispatch, push]
jobs:
  first-job:
    runs-on: ubuntu-latest
    steps:
      - name: first-step
        run: echo "Hello World"
      - name: second-step
        uses: actions/checkout@v6

  second-job:
    needs: first-job
    runs-on: ubuntu-latest
    steps:
      - name: test-step
        run: echo "This is a test step"
      - name: test-code
        uses: actions/checkout@v6
```

### Step 2
Commit and push:

```bash
git add .
git commit -m "Add multiple triggers"
git push
```

### Step 3
Check the GitHub `Actions` tab.

---

## 7. Skipping a Workflow

### Step 1
Make any change in the project.

### Step 2
Run these commands:

```bash
git add .
git commit -m "Comment added [skip ci]"
git push
```

### Step 3
Check GitHub. The workflow will be skipped.

---

## 8. Python CI

### Step 1
Create a new Python project.

### Step 2
Initialize Git:

```bash
git init
```

### Step 3
Use this project structure:

```text
Python-CI/
├── calculator.py
├── test_calculator.py
└── .github/
    └── workflows/
        └── my-actions.yml
```

### Step 4
Create `calculator.py`:

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

if __name__ == "__main__":
    print("2 + 3 =", add(2, 3))
    print("10 - 4 =", subtract(10, 4))
    print("3 * 5 =", multiply(3, 5))
```

### Step 5
Create `my-actions.yml`:

```yaml
name: Python-CI
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v6
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.12'
      - name: Show Python version
        run: python --version
```

### Step 6
Commit and push:

```bash
git add .
git commit -m "Add Python CI"
git push
```

### Step 7
Check the GitHub `Actions` tab.

---

## 9. Running Test Cases

### Step 1
Create `test_calculator.py`:

```python
import unittest
from calculator import add, subtract, multiply

class TestCalculator(unittest.TestCase):
    def test_add_two_positive_numbers(self):
        self.assertEqual(add(2, 3), 5)

    def test_add_negative_and_positive_number(self):
        self.assertEqual(add(-1, 4), 3)

    def test_subtract_numbers(self):
        self.assertEqual(subtract(10, 4), 6)

    def test_multiply_numbers(self):
        self.assertEqual(multiply(3, 5), 15)

if __name__ == "__main__":
    unittest.main()
```

### Step 2
Update the workflow:

```yaml
name: Python-CI
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v6
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.12'
      - name: Show Python version
        run: python --version
      - name: Run tests
        run: python -m unittest discover -s . -p "test_*.py"
```

---

## 10. Job Artifacts

### Step 1
Use this project structure:

```text
Python-CI/
├── calculator.py
├── test_calculator.py
├── requirements.txt
├── pyproject.toml
└── .github/
    └── workflows/
        └── my-actions.yml
```

### Step 2
Create `pyproject.toml`:

```toml
[build-system]
requires = ["setuptools>=61.0"]
build-backend = "setuptools.build_meta"

[project]
name = "simple-calculator"
version = "1.0.0"
description = "A simple calculator project"
requires-python = ">=3.9"

[tool.setuptools]
py-modules = ["calculator"]
```

### Step 3
Create `requirements.txt`:

```text
black==24.10.0
flake8==7.1.1
build==1.2.2.post1
```

### Step 4
Use this workflow:

```yaml
name: Python CI
on: push
jobs:
  lint:
    name: Lint
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v6
      - name: Set up Python and restore pip cache
        uses: actions/setup-python@v6
        with:
          python-version: "3.12"
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          python -m pip install -r requirements.txt
      - name: Check formatting with Black
        run: black --check .
      - name: Run Flake8
        run: flake8 .

  test:
    name: Test
    runs-on: ubuntu-latest
    needs: lint
    steps:
      - name: Checkout repository
        uses: actions/checkout@v6
      - name: Set up Python and restore pip cache
        uses: actions/setup-python@v6
        with:
          python-version: "3.12"
      - name: Run unit tests
        run: python -m unittest discover -v

  build:
    name: Build
    runs-on: ubuntu-latest
    needs: test
    steps:
      - name: Checkout repository
        uses: actions/checkout@v6
      - name: Set up Python and restore pip cache
        uses: actions/setup-python@v6
        with:
          python-version: "3.12"
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          python -m pip install -r requirements.txt
      - name: Build Python package
        run: python -m build
      - name: Upload build files
        uses: actions/upload-artifact@v4
        with:
          name: python-package
          path: dist/
```

---

## 11. Dependency Cache

### Step 1
Add cache to the Python setup:

```yaml
- name: Set up Python
  uses: actions/setup-python@v6
  with:
    python-version: "3.12"
    cache: pip
    cache-dependency-path: requirements.txt
```

### Step 2
Keep the install commands the same:

```yaml
- name: Install linting tools
  run: |
    python -m pip install --upgrade pip
    python -m pip install -r requirements.txt
```

### Step 3
Use cache in the build job also:

```yaml
- name: Set up Python
  uses: actions/setup-python@v6
  with:
    python-version: "3.12"
    cache: pip
    cache-dependency-path: requirements.txt
```

---

## 12. Full CI Pipeline - Build, Test & Notify

### Step 1
Create a Slack channel for alerts.

### Step 2
Create a Slack App:

```text
Apps -> Add Apps -> App Directory -> Manage -> Build -> Create An App
```

### Step 3
Select `From a Blank app`.

App Name:

```text
GitHub CI Notifications
```

### Step 4
Select your workspace and create the app.

### Step 5
Enable `Incoming Webhooks` in Slack settings and select the channel.

### Step 6
Copy the Webhook URL.

### Step 7
Go to your GitHub repository:

```text
Settings -> Secrets and Variables -> Actions -> New repository secret
```

Secret name:

```text
SLACK_WEBHOOK
```

Paste the Webhook URL and save it.

### Step 8
Add Slack notification to the workflow:

```yaml
name: Python-CI
on: push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v6
      - name: Set up Python
        uses: actions/setup-python@v7
        with:
          python-version: '3.12'
      - name: Show Python version
        run: python --version
      - name: Run Tests
        run: python -m unittest discover -s . -p "test_*.py"
      - name: Notify Slack
        if: always()
        continue-on-error: true
        uses: rtCamp/action-slack-notify@v2
        env:
          SLACK_WEBHOOK: ${{ secrets.SLACK_WEBHOOK }}
          SLACK_COLOR: ${{ job.status }}
          SLACK_TITLE: "Python-CI"
          SLACK_MESSAGE: "Workflow '${{ github.workflow }}' finished with status '${{ job.status }}' on branch '${{ github.ref_name }}'. Commit: '${{ github.sha }}'. Triggered by '${{ github.actor }}'."
```

---

## ✅ Final Commands

Use these commands after every change:

```bash
git add .
git commit -m "Update GitHub Actions practical"
git push
```

Then open:

```text
Repository -> Actions
```

and check the workflow.

---

<div align="center">

<img src="https://readme-typing-svg.herokuapp.com?font=JetBrains+Mono&weight=600&size=16&duration=1900&pause=600&color=A371F7&center=true&vCenter=true&repeat=true&width=760&lines=Write+Workflow+%E2%86%92+Push+%E2%86%92+Run+%E2%86%92+Check;Learn+CI%2FCD+One+Step+at+a+Time" alt="GitHub Actions footer animation" />

**Ayan Sayyad**  
GitHub Actions · Python · CI/CD · DevOps

</div>