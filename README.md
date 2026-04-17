# 📦 PES-VCS — Version Control System from Scratch

## 📌 Overview

PES-VCS is a lightweight version control system inspired by Git, implemented in C. It tracks file changes, stores snapshots efficiently, and maintains commit history using filesystem-level concepts.

---

## 🎯 Objective

* Build a version control system from scratch
* Understand how Git internally stores data
* Implement snapshot-based tracking instead of diffs
* Apply OS and filesystem concepts practically

---

## ⚙️ How It Works

The system stores **complete snapshots** of the project instead of differences.

### Core Idea:

* Every file is hashed (SHA-256)
* Objects are stored using their hash
* Same content is stored only once (deduplication)

---

## 🧱 Object Model

### 🔹 Blob

* Stores file content
* Identified by hash

### 🔹 Tree

* Represents directories
* Maps filenames → object hashes

### 🔹 Commit

* Represents a snapshot
* Contains:

  * Tree reference
  * Parent commit
  * Author + message

---

## 🔄 Workflow

```
Working Directory → Index → Object Store → Commit → Branch (HEAD)
```

### Steps:

1. `pes add`

   * File → hashed → stored as blob
   * Entry added to index

2. `pes commit`

   * Tree created from index
   * Commit object created
   * Branch updated

3. `pes log`

   * Traverses commit history

---

## 🗂️ Directory Structure

```
.pes/
├── objects/        # All stored objects (blob/tree/commit)
├── refs/heads/     # Branch pointers
├── index           # Staging area
└── HEAD            # Current branch
```

---

## 🧩 Features

* Content-addressable storage
* File deduplication
* Tree-based directory structure
* Staging area (index)
* Commit history tracking
* CLI-based interaction

---

## 🏗️ Modules

| File     | Purpose                       |
| -------- | ----------------------------- |
| object.c | Object storage (hashing + IO) |
| tree.c   | Directory structure building  |
| index.c  | Staging area management       |
| commit.c | Commit creation & history     |
| pes.c    | Command-line interface        |

---

## 🚀 Commands

```
pes init
pes add <file>
pes status
pes commit -m "message"
pes log
```

---

## 🧪 Build & Run

```bash
make
./pes init
./pes add file.txt
./pes commit -m "Initial commit"
./pes log
```

---

## ⚠️ Development Process (Important)

The project was developed incrementally across phases:

* Phase 1: Object storage
* Phase 2: Tree construction
* Phase 3: Index (staging area)
* Phase 4: Commit system

Each phase involved:

* Implementing core functions
* Testing using provided test files
* Debugging and refining logic

⚠️ Note: Final commits include consolidated improvements and fixes across phases.

---

## 🧠 Key Concepts Learned

* Hash-based storage systems
* Filesystem-level data organization
* Snapshot-based version control
* Atomic file operations
* Linked commit structures

---

## 🎓 Conclusion

This project demonstrates how a real-world system like Git works internally by implementing its core mechanisms from scratch.

---
