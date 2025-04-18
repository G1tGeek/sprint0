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
![image](https://github.com/user-attachments/assets/ba0e1885-a62b-4aac-8292-5bec740402c5)

If this command returns a version (e.g., `jq-1.6`), you already have it installed.

### Ubuntu

```bash
sudo apt update
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
