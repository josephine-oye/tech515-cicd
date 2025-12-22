## Where it fits in Job 1

The **webhook belongs to Job 1**, because:

* Job 1 is triggered by **GitHub pushes**
* Job 2 and Job 3 are triggered by **upstream jobs**, not GitHub

---

## Markdown section to add: *GitHub Webhook*


## GitHub Webhook

A GitHub webhook is used to automatically trigger Job 1 whenever code is pushed to the repository.

### Why a webhook is used

- Enables continuous integration
- Removes the need for manual builds
- Ensures tests run immediately after every push

---

### GitHub Webhook Configuration

In the GitHub repository:

1. Go to **Settings → Webhooks → Add webhook**
2. Payload URL:
```

http://<jenkins-url>/github-webhook/

```
3. Content type:
```

application/json

```
4. Select:
- **Just the push event**
5. Click **Add webhook**

---

### Jenkins Configuration

In **Job 1 → Configure → Build Triggers**:

Enable:

```

GitHub hook trigger for GITScm polling

```

This allows Jenkins to receive events directly from GitHub.

---

## Why this is important to include

This shows:

* You understand **event-driven CI**
* You didn’t rely on polling
* Your pipeline is **automated end-to-end**

---

## Summary (what your Job 1 now documents)

Your Job 1 doc now covers:

* Job creation
* GitHub project linking
* SSH-based SCM
* Node environment
* Test execution
* Discard old builds
* **Webhook-triggered CI**
