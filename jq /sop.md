# Standard Operating Procedure (SOP)  
## JQ – JSON Query Processor
![image](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ4SlpZ3rtWRgb4FBiqiyWroygQEOw_jfVSsQ&s)  
---
### Author
| Created     | Version | Author        | Comment | Reviewer         |
|-------------|---------|---------------|---------|------------------|
| 17-04-2025  | V1      | Yuvraj Singh  |    Internal Review     | Siddharth Pawar  |

---

### Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#Prerequisites)  
3. [Basic Concepts of jq](#Basic-Concepts-of-jq)  
4. [jq Filters Overview](#jq-Filters-Overview)  
5. [Installation Guide](#Installation-Guide)  
   - [Check for Existing Installation](#Check-for-Existing-Installation)  
   - [Ubuntu](#Ubuntu)  
   - [RedHat](#RedHat)  
   - [macOS](#macOS)  
   - [Windows](#windows)  
6. [Example JSON Data](#Example-JSON-Data)  
7. [Basic Usage](#Basic-Usage)  
8. [Advanced Queries](#Advanced-Queries)   
9. [Contact Information](#Contact-Information)  
10. [References](#References)  

---

## Introduction

This documentation outlines the core concepts and practical value of the jq command-line tool, highlighting why it was created, what it offers, and how its features align with modern data processing and automation requirements in software development.

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

If this command returns a version (e.g., `jq-1.6`), you already have it installed.

### Ubuntu

```bash
sudo apt update
sudo apt install jq -y
```

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

---

## Basic Usage

### View Entire JSON

```bash
cat data.json | jq '.'
```

### Filter a Field

```bash
jq '.user.name' data.json
```

---

## Advanced Queries

### Access Nested Values

```bash
jq '.user.address.city' data.json
```

### Loop Over Arrays

```bash
jq '.items[] | .name' data.json
```

### Search by Index Value

#### Query:

```bash
jq '.user.roles[0]' data.json
```

#### Output:

```
"admin"
```

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
