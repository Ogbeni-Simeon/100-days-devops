# 📘 Day 1 – Kubernetes Fundamentals (Personal Documentation)

## 📌 Topic: Creating a Pod in Kubernetes (KodeKloud Lab)

### 🎯 Objective
Understand what a **Pod** is and correctly create one in Kubernetes using a **YAML manifest**, ensuring strict compliance with lab requirements.

---

## 🧠 What I Learned Today

- Kubernetes is a **container orchestration platform**
- The **Pod** is the smallest unit Kubernetes deploys
- A Pod usually runs **one container**
- Kubernetes is very strict about:
  - resource names  
  - container names  
  - labels  
  - image tags  
- KodeKloud labs **do not assume intent** — everything must match exactly

---

## 🧩 Key Concepts Explained

### 🔹 Pod
A Pod is a wrapper around one or more containers.  
If the Pod dies, the container dies with it.

### 🔹 Container
The actual application running inside the Pod (Nginx in this task).

### 🔹 Image
A packaged application.  
Here, `nginx:latest` means:
- `nginx` → image name
- `latest` → image tag (must be explicitly stated)

### 🔹 Labels
Key-value pairs used for identification and grouping.

Example:
```yaml
app: nginx_app
````

---

## 🚨 Important Lesson (Why People Fail This Task)

* Using `kubectl run` auto-generates defaults
* Default container name ≠ required container name
* KodeKloud checks exact values, not “close enough”

> **Conclusion:**
> For beginner labs, manual YAML is the safest and correct approach.

---

## ✅ Task Walkthrough — The Right Way (From the Start)

### 📌 Task Requirements Recap

| Requirement    | Value             |
| -------------- | ----------------- |
| Pod name       | `pod-nginx`       |
| Container name | `nginx-container` |
| Image          | `nginx:latest`    |
| Label          | `app=nginx_app`   |
| Resource type  | Pod               |

---

## 🛠 Step 1: Create the YAML File

```bash
vi pod-nginx.yaml
```

**Explanation:**
Creates and opens a YAML file that will define the Pod.

---

## 🛠 Step 2: Write the Pod Definition (MOST IMPORTANT STEP)

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-nginx
  labels:
    app: nginx_app
spec:
  containers:
  - name: nginx-container
    image: nginx:latest
```

### Line-by-Line Explanation

* `apiVersion: v1`
  Core Kubernetes API version

* `kind: Pod`
  Resource type being created

* `metadata.name`
  Name of the Pod

* `metadata.labels`
  Label attached to the Pod

* `spec.containers`
  List of containers in the Pod

* `name: nginx-container`
  Explicit container name (required)

* `image: nginx:latest`
  Explicit image tag (required)

---

## 🛠 Step 3: Save and Exit

```text
Esc → :wq → Enter
```

---

## 🛠 Step 4: Create the Pod

```bash
kubectl apply -f pod-nginx.yaml
```

**Explanation:**
Applies the YAML manifest and creates the Pod.

---

## 🔍 Step 5: Verification (Never Skip This)

### ✔ Check Pod Status

```bash
kubectl get pods
```

Expected:

```text
pod-nginx   Running
```

---

### ✔ Inspect Pod Details

```bash
kubectl describe pod pod-nginx
```

Verify:

* Container Name → `nginx-container`
* Image → `nginx:latest`
* Label → `app=nginx_app`

---

## ✅ Final Outcome

* Pod created successfully
* Configuration matches task exactly
* No defaults used
* KodeKloud validation will pass

---

## 🧠 Day 1 Takeaway

> **In Kubernetes labs and exams:**
> ❌ Guessing intent fails
> ✅ Explicit YAML always wins

```
