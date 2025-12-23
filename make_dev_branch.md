# Making a dev branch

## Branching Strategy (dev and main)

A two-branch strategy was used for this CI/CD pipeline:

- `dev` – active development branch
- `main` – stable production-ready branch

Developers make changes and push code to the `dev` branch.  
Code is **never pushed directly to `main`**.

This allows all changes to be tested before they are merged and deployed.


## Creating the dev Branch

The `dev` branch was created locally and pushed to GitHub using the following commands:

```
git checkout -b dev
git push -u origin dev
```

Once created, all development work was carried out on the `dev` branch.

## How the dev Branch Is Used in the Pipeline

* **Job 1 (CI Test)** runs when code is pushed
* **Job 2 (CI Merge)** merges tested code from `dev` into `main`
* **Job 3 (CD Deploy)** deploys the updated application

This ensures that only tested and approved code reaches the production environment.
