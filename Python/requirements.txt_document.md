
# requirements.txt  Documentation
![image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTSyVrRrhYDmUdt6QBsDkve4SneCW2cFnKk17Rf4HZ10_U2Z1XgfpBopH2OmXj1qjfo9g&usqp=CAU)

## **Author**
| Created     | Version | Author        | Modifed | Comment           | Reviewer         |
|-------------|---------|---------------|-------|------------|------------------|
| 15-04-2025  | V1.1      | Yuvraj Singh | 17-04-2025 | Internal Review   | Siddharth Pawar  |
| 17-04-2025  | V2.1     | Yuvraj Singh  | 23-04-2025 |   L0 Review     | Naveen Haswani  |
| 23-04-2025  | V3     | Yuvraj Singh  |  |   L1 Review     | Deepak Nishad |
| 27-04-2025  | V4.1     | Yuvraj Singh  | 03-05-2025 |   L2 Review     | Naveen Verma |

---

## **Table of Contents**

1. [Introduction](#introduction)
2. [What is `requirements.txt`](#what-is-requirementstxt)
3. [Why Use `requirements.txt`](#why-use-requirementstxt)
4. [How to Create and Use `requirements.txt`](#how-to-create-and-use-requirementstxt)
5. [Use Cases](#use-cases)  
6. [Best Practices](#best-practices)  
7. [Syntax of `requirements.txt`](#syntax-of-requirementstxt)
8. [Difference Between pip with `requirements.txt` and pip for single module](#difference-between-pip-with-requirementstxt-and-pip-for-single-module)
9. [Conclusion](#conclusion)  
10. [Contacts](#contacts)  
11. [References](#references)  

---

## Introduction

This guide provides a comprehensive overview of the requirements.txt file in Python projects—its purpose, advantages, best practices, and syntax. By understanding and using this file effectively, developers can ensure consistent environments, simplify dependency management, and improve reliability across development, testing, and production stages.

---

## What is `requirements.txt`

The `requirements.txt` file is a plain text file used in Python projects to list all the dependencies (i.e., external packages and libraries) required for the project to run. It provides a centralized and version-controlled way to declare the exact versions of packages, ensuring consistency across development, testing, and production environments. By maintaining this file, teams can reproduce environments reliably and manage third-party packages efficiently.

---

## Why Use `requirements.txt`

| **Reason**                       | **Explanation**                                                                                      |
|----------------------------------|--------------------------------------------------------------------------------------------------------|
| **Consistency Across Environments** | Ensures everyone uses the same package versions, preventing "it works on my machine" issues.         |
| **Ease of Setup**               | Enables quick installation of dependencies using one command: `pip install -r requirements.txt`      |
| **Reliable Deployments**        | Locks package versions to prevent unexpected behavior from version upgrades.                         |
| **Simplifies Dependency Tracking** | Easier to audit, update, and manage all third-party packages in one file.                             |

---

## How to Create and Use `requirements.txt`

Creating and using a `requirements.txt` file is straightforward and plays a critical role in managing dependencies across environments.

### Step 1: Create a Virtual Environment

First, set up a virtual environment to isolate your project's dependencies.

```
python -m venv venv  
source venv/bin/activate  (on Linux/Mac)  
venv\Scripts\activate     (on Windows)
```

### Step 2: Install the Required Packages

Install the packages you need for your project using pip.

```
pip install flask  
pip install requests
```

### Step 3: Generate the `requirements.txt` File

Once all necessary packages are installed, generate the `requirements.txt` file with:

```
pip freeze > requirements.txt
```

This captures all installed packages and their exact versions into the file.

### Step 4: Share or Use the File in Other Environments

Anyone working on the same project can install all dependencies listed in `requirements.txt` using:

```
pip install -r requirements.txt
```

This ensures consistent and reproducible environments across all systems.

---

## Use Cases

| **Scenario**             | **How `requirements.txt` Helps**                                                                 |
|--------------------------|--------------------------------------------------------------------------------------------------|
| **Development**          | New developers can install all dependencies quickly and reliably.                               |
| **CI/CD Pipelines**      | Automated systems can replicate the environment consistently for testing and deployment.        |
| **Production**           | Ensures stable and tested versions are used in live environments.                              |
| **Debugging & Reproducibility** | Helps recreate specific environments to trace and fix bugs easily.                             |

---

## Best Practices

### 1. Use Exact Version Pinning

Pin dependencies to **exact versions** to avoid unexpected changes when installing packages across different environments or machines. This ensures that your application always uses the same, tested version of a package.

```
flask==2.1.3 \
requests==2.28.1 \
sqlalchemy==1.4.46 
```

> Why?
- Prevents bugs caused by newer, untested versions.
- Helps maintain consistent environments across dev, test, and prod.


---

### 2. Avoid Loose Versioning

Avoid using version specifiers like >=, <=, or leaving versions blank. Loose versioning can introduce breaking changes when packages update in the background.

**Not Recommended:** \

```
flask \
requests>=2.0 
```

**Recommended:** \

```
flask==2.1.3 \
requests==2.28.1 
```
> Risks of Loose Versioning:
- Unintended upgrades.
- Incompatibility with your codebase.
- Hidden bugs introduced by third-party changes.

---

### 3. Separate Production and Development Dependencies

Keep production dependencies clean by separating development-only tools like testing frameworks and linters. This can be done using comments in the same file or separate files like dev-requirements.txt.

**Example:** \
```
Production \
flask==2.1.3 
```

```
Development \
pytest==7.2.1 \
black==23.1.0 
```

Example using separate files:

```
requirements.txt → Production
dev-requirements.txt → Development (includes linters, formatters, test tools)
```

> Why?
- Reduces attack surface in production.
- Keeps Docker images and deployment environments minimal and secure.

---

### 4. Use `pip freeze` to Lock All Installed Packages

After setting up your virtual environment and installing required packages, use the following command to lock the current state:

```
pip freeze > requirements.txt 
```

> This includes:
- Direct dependencies (your specified packages)
- Transitive dependencies (their dependencies)

> Benefits:
- Full reproducibility of environments.
- Useful when sharing the project or deploying.

---

### 5. Consider Using Hashes for Security

To ensure package integrity and prevent tampering, add hashes to your dependencies using tools like pip-tools.

```
requests==2.28.1 \
--hash=sha256:aaa... \
--hash=sha256:bbb...
```

> Why hashes matter:
- Prevents installation of compromised or altered packages.
- Adds another layer of security in CI/CD pipelines and production.


---

## Syntax of `requirements.txt`

| **Syntax**                          | **Description**                                                   | **Example**                         |
|------------------------------------|-------------------------------------------------------------------|-------------------------------------|
| `package`                          | Installs the latest version of a package                          | `flask`                             |
| `package==version`                 | Installs the exact version                                        | `requests==2.28.1`                  |
| `package>=version`                 | Installs the specified version or newer                           | `sqlalchemy>=1.4`                   |
| `package<=version`                 | Installs the specified version or older                           | `django<=3.2`                       |
| `package~=version`                 | Compatible release — allows minor updates                         | `pandas~=1.3.0`                     |
| `-e git+URL#egg=package`           | Installs directly from a Git repo in "editable" mode              | `-e git+https://github.com/...`     |
| `--index-url <url>`                | Specifies a custom package index                                  | `--index-url https://example.com`  |
| `--find-links <path_or_url>`       | Finds packages in local/remote locations                          | `--find-links ./packages`          |
| `# comment`                        | Inline comments for readability                                   | `flask==2.1.3  # Web framework`     |
| `-r otherfile.txt`                 | Includes another requirements file (like dev-requirements.txt)   | `-r dev-requirements.txt`          |

### Example requirements.txt
```bash
flask==2.1.3 \
requests==2.28.1 \
sqlalchemy>=1.4 \
-e git+https://github.com/example/repo.git#egg=customlib \
--index-url https://pypi.org/simple \
--find-links ./local-packages 
```
---

## Difference Between pip with `requirements.txt` and pip for single module

| **Aspect**               | **`requirements.txt`**                                             | **`pip` Command**                                            |
|--------------------------|---------------------------------------------------------------------|--------------------------------------------------------------|
| **Purpose**              | Stores a list of dependencies for reuse and sharing                | Installs packages one-by-one or from a requirements file     |
| **Format**               | Plain text file listing packages and versions                     | Command-line tool for Python package installation            |
| **Usage**                | Used with `pip install -r requirements.txt`                       | Used as `pip install <package>`                             |
| **Reproducibility**      | Promotes consistent environments across systems                    | Manual installs may vary over time                           |
| **Version Control**      | Can be committed to version control for collaboration              | Pip commands are transient (used interactively)              |
| **Dependency Tracking**  | Can include pinned versions, hashes, and comments                  | Tracks only what’s installed at that moment                  |
| **Automation**           | Easily integrates with CI/CD tools for automation                  | Less structured for automation                              |

---

## Conclusion

The `requirements.txt` file is more than just a list of packages—it's a tool that fosters collaboration, reduces bugs, and increases deployment reliability. By following best practices, teams can maintain cleaner, safer, and more efficient Python environments.

---

## Contacts

| Name         | Email Address                                 |
|--------------|-----------------------------------------------|
| Yuvraj Singh | yuvraj.singh.snaatak@mygurukulam.co           |

---

## References

| **Title**                               | **Link**                                                                 |
|------------------------------------------|-------------------------------------------------------------------------|
| Official pip Documentation               | [Visit](https://pip.pypa.io/en/stable/reference/requirements-file-format/) |
| Free Code Camp How-To Guide    | [Visit](https://www.freecodecamp.org/news/python-requirementstxt-explained/)              |
| Best Practices for Dependency Management | [Visit](https://docs.python-guide.org/dev/virtualenvs/#requirements-files) |
