# Standard Operating Procedure (SOP)  
## JQ – JSON Query Processor
![image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ4SlpZ3rtWRgb4FBiqiyWroygQEOw_jfVSsQ&s)  
---
### Author
| Created     | Version | Author        | Modifed | Comment           | Reviewer         |
|-------------|---------|---------------|-------|------------|------------------|
| 17-04-2025  | V1.1      | Yuvraj Singh | 18-04-2025 | Internal Review   | Siddharth Pawar  |
| 18-04-2025  | V2     | Yuvraj Singh  |  |   L0 Review     | Naveen Haswani  |

---

### Table of Contents
1. [Introduction](#introduction)
2. [Why Use `jq`?](#why-use-jq)
3. [Features](#features)
4. [Prerequisites](#prerequisites)  
5. [Basic Concepts of jq](#basic-concepts-of-jq)  
6. [jq Filters Overview](#jq-filters-overview)  
7. [Installation Guide](#installation-guide)  
   - [Check for Existing Installation](#check-for-existing-installation)  
   - [Ubuntu](#ubuntu)  
   - [RedHat](#redhat)  
   - [macOS](#macos)  
   - [Windows](#windows)  
8. [Example JSON Data](#example-json-data)  
9. [Basic Usage](#basic-usage)  
10. [Advanced Queries](#advanced-queries)
11. [Conclusion](#conclusion)  
12. [Contact Information](#contact-information)  
13. [References](#references)  

---

## Introduction

This documentation outlines the core concepts and practical value of the jq command-line tool, highlighting why it was created, what it offers, and how its features align with modern data processing and automation requirements in software development.

---

## Why Use `jq`?

In modern development and operations workflows, JSON has become the de facto data interchange format—used across APIs, configuration files, logging systems, and CI/CD pipelines. However, working with raw JSON data through traditional shell utilities like `grep`, `awk`, or `sed` often results in complex, error-prone scripts.

## Features

This is where `jq` becomes indispensable:

> - **Purpose-Built for JSON**: Unlike generic text processors, `jq` understands JSON structure and offers precise control over data extraction, transformation, and formatting.
> - **Efficient & Lightweight**: It is a fast, command-line-based tool that can be used in pipelines, cron jobs, and automation scripts without requiring additional dependencies.
> - **Powerful Query Language**: With features like filtering, mapping, nesting, conditionals, and arithmetic operations, `jq` simplifies complex JSON manipulations.
> - **Ideal for Automation**: Its ability to work seamlessly in scripts makes it a favorite in DevOps, SRE, and backend development environments.

---

## Prerequisites

- Basic understanding of JSON format  
- Terminal or Command Line Interface access  
- Internet access for installation (if not already installed)

---

## Basic Concepts of jq

- `jq` parses JSON and applies filters to transform or extract information.
- It is designed to work like `sed` or `awk` but for JSON files.
- Filters are written using a concise query language.

---

## jq Filters Overview

| Filter Example | Description                        |
|----------------|------------------------------------|
| `.`            | Identity filter (returns input)    |
| `.key`         | Access a specific key in the JSON  |
| `.[index]`     | Access array item by index         |
| `|`            | Pipe result to next filter         |

---

## Installation Guide

### Check for Existing Installation

Before installing, check if `jq` is already present:

```bash
jq --version
```
![image](https://github.com/user-attachments/assets/ba0e1885-a62b-4aac-8292-5bec740402c5)

If this command returns a version (e.g., `jq-1.6`), you already have it installed.

### Ubuntu
> Update your system 
> - [Ubuntu Basic System Commands](https://github.com/snaatak-Downtime-Crew/Documentation/blob/durgesh_scrums_3/common_stack/operating_system/ubuntu/sop/commoncommands/README.md#1-basic-system-commands)
```bash
sudo apt install jq -y
```
![image](https://github.com/user-attachments/assets/a03f59b7-09cb-4c40-9a96-d897e00845cb)


![image](https://github.com/user-attachments/assets/2cfce514-70b5-426e-8a2f-8951b4a88035)

### RedHat

```bash
sudo yum install epel-release -y
sudo yum install jq -y
```

### macOS

```bash
brew install jq
```

### Windows

- Download the `.exe` file from the [official GitHub releases](https://github.com/stedolan/jq/releases)
- Add the directory containing the `.exe` to your system’s `PATH` environment variable

---

## Example JSON Data

Save the following content in a file called `data.json` for practice:

```json
{
  "user": {
    "name": "Alice",
    "roles": ["admin", "editor"],
    "age": 30,
    "address": {
      "city": "New York",
      "zip": "10001"
    }
  },
  "items": [
    {"id": 1, "name": "Item One"},
    {"id": 2, "name": "Item Two"}
  ]
}
```
![image](https://github.com/user-attachments/assets/6ce30a9a-3f01-4313-aed0-eb9425f2e46a)

---

## Basic Usage

### View Entire JSON

```bash
cat data.json | jq '.'
```
![image](https://github.com/user-attachments/assets/559b24f4-8ff8-4580-b58f-d5193974c0cd)

### Filter a Field

```bash
jq '.user.name' data.json
```
![image](https://github.com/user-attachments/assets/9b28d42b-3a56-4f42-8177-facc26df5ec3)

---

## Advanced Queries

### Access Nested Values

```bash
jq '.user.address.city' data.json
```
![image](https://github.com/user-attachments/assets/38aa411d-b038-480c-9c99-9693025cfbf5)

### Loop Over Arrays

```bash
jq '.items[] | .name' data.json
```
![image](https://github.com/user-attachments/assets/390601ae-ae3c-4f76-b494-99580d00cabc)


### Search by Index Value

#### Query:

```bash
jq '.user.roles[0]' data.json
```
![image](https://github.com/user-attachments/assets/7b319199-c581-4c54-aee2-014827748901)


---
## Conclusion 

`jq` bridges the gap between human-readable JSON and machine-level automation needs—allowing for cleaner, scalable, and more maintainable workflows.

---
## Contact Information

| Name         | Email Address                                 |
|--------------|-----------------------------------------------|
| Yuvraj Singh | yuvraj.singh.snaatak@mygurukulam.co           |

---

## References
| **Title**                        | **Link**                                        |
|----------------------------------|-------------------------------------------------|
| Official jq Manual | [Visit](https://stedolan.github.io/jq/manual/)  |
| jq GitHub Releases | [Visit](https://github.com/stedolan/jq/releases)  |
| jq Cheatsheet | [Visit](https://lzone.de/cheat-sheet/jq)  |
