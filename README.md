# 📦 DVC Learning Project

This repository demonstrates a simple **Data Version Control (DVC)** workflow integrated with **Git** and a local remote storage (simulated S3 directory).

The goal is to understand how data versioning works alongside code versioning.

---

## 🚀 Project Overview

* Generate data using `mycode.py`
* Store data in a `data/` directory
* Track code with **Git**
* Track data with **DVC**
* Version multiple iterations of dataset changes

---

## 🛠️ Setup Instructions

### 1. Initialize Git Repository

```bash
git init
git clone <repo_url>
```

---

### 2. Create Initial Code

* Create `mycode.py`
* Script should generate a CSV file inside a `data/` folder

Run the script:

```bash
python mycode.py
```

---

### 3. Track Initial Code with Git

```bash
git add .
git commit -m "Initial commit with data generation code"
git push
```

⚠️ At this stage, `data/` is still tracked by Git.

---

## 📊 DVC Setup

### 4. Install and Initialize DVC

```bash
pip install dvc
dvc init
```

This creates:

* `.dvc/`
* `.dvcignore`

---

### 5. Create Local Remote Storage

```bash
mkdir S3
```

---

### 6. Add Remote to DVC

```bash
dvc remote add -d myremote S3
```

---

## 📁 Data Tracking with DVC

### 7. Start Tracking Data

```bash
dvc add data/
```

If Git was tracking `data/`, remove it:

```bash
git rm -r --cached data
git commit -m "Stop tracking data with Git"
```

---

### 8. Re-add Data to DVC

```bash
dvc add data/
git add .gitignore data.dvc
git commit -m "Track data with DVC"
```

---

### 9. Push Data to Remote

```bash
dvc commit
dvc push
```

Then commit Git:

```bash
git add .
git commit -m "Data version v1"
git push
```

---

## 🔁 Data Versioning Workflow

### Version 2 (V2)

1. Modify `mycode.py` (append new data)
2. Run script:

```bash
python mycode.py
```

3. Check changes:

```bash
dvc status
```

4. Save changes:

```bash
dvc commit
dvc push
```

5. Commit in Git:

```bash
git add .
git commit -m "Data version v2"
git push
```

---

### Version 3 (V3)

Repeat the same steps:

```bash
python mycode.py
dvc status
dvc commit
dvc push
git add .
git commit -m "Data version v3"
git push
```

---

## ✅ Final Checks

```bash
git status
dvc status
```

Everything should be up-to-date.

---

## 🧠 Key Concepts Learned

* Difference between **Git tracking vs DVC tracking**
* Using `.dvc` files to track datasets
* Remote storage configuration
* Versioning datasets independently of code
* Reproducibility of data pipelines

---

## 📌 Important Notes

* Never track large data directly with Git
* `.dvc` files act as pointers to actual data
* Remote storage (S3/local) holds real data
* Git stores metadata, not the dataset itself

---

## 🔮 Next Steps

* Use real cloud storage (AWS S3, GCS, Azure)
* Add `dvc.yaml` for pipelines
* Integrate with ML experiments
* Use `dvc repro` for automation

---

## 👨‍💻 Author

**Asifur Rahman Mridul**
Aspiring AI/ML Engineer | MLOps Enthusiast

---