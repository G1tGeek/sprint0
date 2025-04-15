
# requirements.txt Documentation
![image](https://cdn.hashnode.com/res/hashnode/image/upload/v1637422966499/jx6h36yHp.jpeg)

| Created     | Version | Author        | Comment            | Reviewer         |
|-------------|---------|---------------|---------------------|------------------|
| 14-04-2025  | V1      | Yuvraj Singh  | Internal Review     | Siddharth Pawar  |

---

## **Table of Contents**

1. [Introduction](#introduction)  
2. [Why Use `requirements.txt`](#why-use-requirementstxt)  
3. [Use Cases](#use-cases)  
4. [Dependency Versioning Best Practices](#dependency-versioning-best-practices)  
5. [Conclusion](#conclusion)  
6. [Contacts](#contacts)  
7. [References](#references)  

---

## Introduction

The `requirements.txt` file is a standard way in Python projects to define all the external packages a project depends on. It allows for easy replication of environments by listing all required dependencies that can be installed using `pip`.

---

## Why Use `requirements.txt`

| **Reason**                       | **Explanation**                                                                                      |
|----------------------------------|--------------------------------------------------------------------------------------------------------|
| **Consistency Across Environments** | Ensures everyone uses the same package versions, preventing "it works on my machine" issues.         |
| **Ease of Setup**               | Enables quick installation of dependencies using one command: `pip install -r requirements.txt`      |
| **Reliable Deployments**        | Locks package versions to prevent unexpected behavior from version upgrades.                         |
| **Simplifies Dependency Tracking** | Easier to audit, update, and manage all third-party packages in one file.                             |

---

## Use Cases

| **Scenario**             | **How `requirements.txt` Helps**                                                                 |
|--------------------------|--------------------------------------------------------------------------------------------------|
| **Development**          | New developers can install all dependencies quickly and reliably.                               |
| **CI/CD Pipelines**      | Automated systems can replicate the environment consistently for testing and deployment.        |
| **Production**           | Ensures stable and tested versions are used in live environments.                              |
| **Debugging & Reproducibility** | Helps recreate specific environments to trace and fix bugs easily.                             |

---

## Dependency Versioning Best Practices

### 1. Use Exact Version Pinning

Pin packages to exact versions to ensure stability:

\`\`\`txt
flask==2.1.3
requests==2.28.1
sqlalchemy==1.4.46
\`\`\`

---

### 2. Avoid Loose Versioning

Avoid using operators like `>=`, `<=`, or leaving versions unspecified. These can cause unexpected results due to breaking changes in newer versions.

**Not Recommended:**
\`\`\`txt
flask
requests>=2.0
\`\`\`

**Recommended:**
\`\`\`txt
flask==2.1.3
requests==2.28.1
\`\`\`

---

### 3. Separate Production and Development Dependencies

Use comments or separate files like `dev-requirements.txt` to avoid mixing dev tools with production needs.

**Example:**
\`\`\`txt
# Production
flask==2.1.3

# Development
pytest==7.2.1
black==23.1.0
\`\`\`

---

### 4. Use `pip freeze` to Lock All Installed Packages

Once your virtual environment is ready and all dependencies are installed:

\`\`\`bash
pip freeze > requirements.txt
\`\`\`

This captures **all direct and transitive dependencies**.

---

### 5. Consider Using Hashes for Security

Add hashes to ensure package integrity (typically used with tools like `pip-tools`):

\`\`\`txt
requests==2.28.1 \
    --hash=sha256:aaa... \
    --hash=sha256:bbb...
\`\`\`

---

## Conclusion

The `requirements.txt` file is more than just a list of packages—it's a tool that fosters collaboration, reduces bugs, and increases deployment reliability. By following best practices, teams can maintain cleaner, safer, and more efficient Python environments.

> “In modern Python development, `requirements.txt` is more than just a list—it’s a contract ensuring consistency across teams and systems.”  
> – *Yuvraj Singh*

---

## Contacts

| Name         | Email Address                                 |
|--------------|-----------------------------------------------|
| Yuvraj Singh | yuvraj.singh.snaatak@mygurukulam.co           |

---

## References

| **Title**                               | **Link**                                                                 |
|------------------------------------------|-------------------------------------------------------------------------|
| Official pip Documentation               | [Visit](https://pip.pypa.io/en/stable/reference/pip_install/#requirements-file-format) |
| Real Python - Requirements File          | [Visit](https://realpython.com/what-is-requirements.txt/)              |
| Best Practices for Dependency Management | [Visit](https://docs.python-guide.org/dev/virtualenvs/#requirements-files) |
