# 📘 Day 2 – Kubernetes Fundamentals (Personal Documentation)

## 📌 Topic: Creating a Deployment in Kubernetes (KodeKloud Lab)

---

## 🎯 Objective

Understand what a **Deployment** is in Kubernetes and correctly create one to manage an application declaratively using a YAML manifest.

---

## 🧠 What I Learned Today

- A **Deployment** is a higher-level Kubernetes object
- Deployments manage **Pods automatically**
- They provide:
  - self-healing
  - scalability
  - rolling updates
- Unlike standalone Pods, Deployments ensure applications remain running
- Kubernetes is strict about:
  - API versions
  - selectors
  - matching labels
- Explicit image tags are important to avoid validation failures

---

## 🧩 Key Concepts Explained 

### 🔹 Deployment
A Deployment defines the **desired state** of an application and ensures Kubernetes maintains that state.

If a Pod dies, the Deployment:
- detects it
- creates a replacement automatically

---

### 🔹 Replica
Specifies how many identical Pods should be running at any given time.

Example:
```yaml
replicas: 1
````

---

### 🔹 Selector

Used by the Deployment to identify which Pods it manages.

Selectors **must match** the labels in the Pod template.

---

## 📋 Task Requirements

| Requirement     | Value          |
| --------------- | -------------- |
| Deployment name | `nginx`        |
| Image           | `nginx:latest` |
| Resource type   | Deployment     |

---

## 🛠 Step 1: Create the Deployment YAML File

```bash
vi nginx-deployment.yaml
```

This file defines exactly how the Deployment should be created.

---

## 🛠 Step 2: Write the Deployment Definition

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
```

---

## 🔍 Explanation of Key Sections

* `apiVersion: apps/v1`
  Specifies the correct API for Deployments

* `kind: Deployment`
  Declares the Kubernetes resource type

* `metadata.name`
  Sets the Deployment name as required

* `replicas`
  Number of Pods to run

* `selector.matchLabels`
  Defines which Pods the Deployment controls

* `template.metadata.labels`
  Labels applied to Pods created by the Deployment

* `containers.name`
  Name of the container inside the Pod

* `image: nginx:latest`
  Explicit image and tag (required by task)

---

## 🛠 Step 3: Apply the Deployment

```bash
kubectl apply -f nginx-deployment.yaml
```

This command tells Kubernetes to create the Deployment exactly as defined.

---

## 🔍 Step 4: Verification

### ✔ Check Deployment Status

```bash
kubectl get deployments
```

Expected output:

```text
nginx   1/1   1   1   Running
```

---

### ✔ Check Pods Created by the Deployment

```bash
kubectl get pods
```

You should see a Pod with a generated name similar to:

```text
nginx-xxxxxxxxxx-xxxxx
```

---

## ✅ Final Outcome

* Deployment created successfully
* Pod managed automatically by Kubernetes
* Image tag explicitly defined
* Configuration matches task requirements exactly

---

## 🧠 Day 2 Takeaway

> **Pods run applications,
> Deployments manage Pods.**
