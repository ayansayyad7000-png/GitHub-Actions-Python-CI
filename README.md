# GitHub Actions Practical - ayansayyad

## 1. Creating First Workflow

### Step 1
GitHub repository open karo.

### Step 2
`Actions` tab open karo.

### Step 3
`Setup a workflow yourself` par click karo.

### Step 4
VS Code me `GitHub Actions` plugin install karo aur GitHub se sign in karo.

### Step 5
Project me folder banao:

```text
.github/workflows
```

### Step 6
Is folder ke andar workflow file banao:

```text
my-actions.yml
```

### Step 7
File me ye code likho:

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
Commit aur push karo:

```bash
git add .
git commit -m "Add first workflow"
git push
```

### Step 9
GitHub me `Actions` tab open karke workflow check karo.

---

## 2. Running Multi Line Shell Commands

### Step 1
`my-actions.yml` me ye code rakho:

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
Commit aur push karo:

```bash
git add .
git commit -m "Add multiline commands"
git push
```

### Step 3
GitHub ke `Actions` tab me result check karo.

---

## 3. Using Actions

### Step 1
Workflow me checkout action add karo:

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
Commit aur push karo:

```bash
git add .
git commit -m "Use checkout action"
git push
```

### Step 3
GitHub me `Actions` tab check karo.

GitHub Actions Marketplace:

```text
https://github.com/marketplace?type=actions
```

---

## 4. Running Multiple Jobs

### Step 1
Workflow me do jobs banao:

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
Commit aur push karo:

```bash
git add .
git commit -m "Add multiple jobs"
git push
```

### Step 3
GitHub `Actions` tab me dono jobs check karo.

---

## 5. Running Multiple Jobs - Sequential

### Step 1
Second job ko first job ke baad run karne ke liye `needs` use karo:

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
Commit aur push karo:

```bash
git add .
git commit -m "Run jobs sequentially"
git push
```

### Step 3
GitHub `Actions` tab me check karo.

---

## 6. Running Multiple Triggers

### Step 1
Manual aur push dono triggers use karo:

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
Commit aur push karo:

```bash
git add .
git commit -m "Add multiple triggers"
git push
```

### Step 3
GitHub `Actions` tab me check karo.

---

## 7. Skipping a Workflow

### Step 1
Koi change karo.

### Step 2
Ye commands chalao:

```bash
git add .
git commit -m "Comment added [skip ci]"
git push
```

### Step 3
GitHub par check karo. Workflow skip hoga.

---

## 8. Python CI

### Step 1
New Python project banao.

### Step 2
Git initialise karo:

```bash
git init
```

### Step 3
Project structure:

```text
Python-CI/
├── calculator.py
├── test_calculator.py
└── .github/
    └── workflows/
        └── my-actions.yml
```

### Step 4
`calculator.py`:

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
`my-actions.yml`:

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
Commit aur push karo:

```bash
git add .
git commit -m "Add Python CI"
git push
```

### Step 7
GitHub `Actions` tab me check karo.

---

## 9. Running Test Cases

### Step 1
`test_calculator.py`:

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
Workflow update karo:

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
Project structure:

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
`pyproject.toml`:

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
`requirements.txt`:

```text
black==24.10.0
flake8==7.1.1
build==1.2.2.post1
```

### Step 4
Workflow:

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
Python setup me cache add karo:

```yaml
- name: Set up Python
  uses: actions/setup-python@v6
  with:
    python-version: "3.12"
    cache: pip
    cache-dependency-path: requirements.txt
```

### Step 2
Install commands same rahenge:

```yaml
- name: Install linting tools
  run: |
    python -m pip install --upgrade pip
    python -m pip install -r requirements.txt
```

### Step 3
Build job me bhi cache use karo:

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
Slack me alerts ke liye channel banao.

### Step 2
Slack App banao:

```text
Apps -> Add Apps -> App Directory -> Manage -> Build -> Create An App
```

### Step 3
`From a Blank app` select karo.

App Name:

```text
GitHub CI Notifications
```

### Step 4
Workspace select karo aur app create karo.

### Step 5
Slack settings me `Incoming Webhooks` enable karo aur channel select karo.

### Step 6
Webhook URL copy karo.

### Step 7
GitHub repository me jao:

```text
Settings -> Secrets and Variables -> Actions -> New repository secret
```

Secret name:

```text
SLACK_WEBHOOK
```

Webhook URL paste karke save karo.

### Step 8
Workflow me Slack notification add karo:

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

## Final Commands

Har change ke baad ye commands use karo:

```bash
git add .
git commit -m "Update GitHub Actions practical"
git push
```

Phir GitHub me:

```text
Repository -> Actions
```

open karke workflow check karo.
