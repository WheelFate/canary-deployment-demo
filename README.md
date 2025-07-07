# Canary Deployment Demo with GitHub Pages (No Installation & Free)

This project demonstrates a simplified "canary deployment" strategy for a static website, utilizing GitHub Pages. The entire setup is achieved without any local software installations and is completely free.

## What is Canary Deployment?

Canary deployment is a technique to reduce the risk of introducing a new software version in production. A new version (the "canary") is rolled out to a small subset of users first. If it proves stable and performs well, it's then rolled out to the rest of the users. If issues arise, traffic can be quickly redirected back to the stable, old version, minimizing impact.

## Project Goal

The goal of this specific project is to illustrate the core concept of canary deployment using only GitHub's built-in features (Repositories, Branches, and GitHub Pages) to host two distinct versions of a static site (Stable and Canary) and provide a method to "promote" or "rollback" manually.

## Step-by-Step Implementation

Follow these steps to replicate the setup:

### Step 1: Create a GitHub Repository

1.  Created a new public GitHub repository named `canary-deployment-demo`.
2.  Initialized it with a `README.md` file.

### Step 2: Add Stable and Canary Website Files

Two simple HTML files were added to the `main` branch to represent our application versions:

1.  **`index.html` (Stable Version):**
    * Contains green styling and text: "Welcome to the Stable Website! Version: 1.0 (Stable)".
    * [View Stable `index.html` Code Here](https://github.com/WheelFate/canary-deployment-demo/blob/main/index.html)
2.  **`canary.html` (Canary Version):**
    * Contains blue styling and text: "Welcome to the Canary Website! Version: 1.1 (Canary)".
    * [View Canary `canary.html` Code Here](https://github.com/WheelFate/canary-deployment-demo/blob/main/canary.html)

### Step 3: Deploy the Stable Website with GitHub Pages

The `main` branch (containing the stable `index.html`) was deployed using GitHub Pages:

1.  Navigated to `Settings` -> `Pages` in the repository.
2.  Configured "Source" to `Deploy from a branch`, selected `main` as the `Branch` and `/(root)` as the folder.
3.  Clicked "Save".
4.  After a few minutes, the stable site became live at: **`https://wheelfate.github.io/canary-deployment-demo/`** (showing the green Version 1.0).

### Step 4: Deploy the Canary Website (Simulated)

To simulate the canary, a new branch was created, and its `index.html` was replaced with the canary content. GitHub Pages was then switched to deploy from this branch.

1.  Created a new branch named `canary-v1.1` from `main`.
2.  On the `canary-v1.1` branch:
    * The original `index.html` file (from the stable version) was **deleted**.
    * The `canary.html` file was **renamed to `index.html`**. This means the `canary-v1.1` branch now exclusively has the "blue" Version 1.1 as its `index.html`.
3.  Navigated back to `Settings` -> `Pages`.
4.  Changed the "Branch" source to **`canary-v1.1`** and clicked "Save".
5.  After a few minutes, the same URL **`https://wheelfate.github.io/canary-deployment-demo/`** started showing the **blue "Welcome to the Canary Website! Version: 1.1 (Canary)"**.

    *This setup demonstrates a "flip-flop" deployment on a single URL. In a true canary, traffic splitting happens at a different layer, but this simulates having a new version publicly accessible for testing.*

## How to "Promote" or "Rollback" with this Setup

### To "Promote" (make Canary the New Stable)

If the `canary-v1.1` version (blue) performs well and you want it to be your new official production:

1.  Go to the `Code` tab of your repository.
2.  Click the `canary-v1.1` branch dropdown and select `main`.
3.  Click the "Branches" tab or "Compare & pull request" button (if visible).
4.  Create a **Pull Request** to merge `canary-v1.1` into `main`.
5.  After the Pull Request is merged, `main` will contain the new code.
6.  Go back to `Settings` -> `Pages` and **switch the "Branch" source back to `main`**. Your live site will continue showing Version 1.1, but now from the `main` branch.

### To "Rollback" (revert to Previous Stable)

If the `canary-v1.1` version (blue) shows issues and you want to revert to the old stable (green):

1.  Go to `Settings` -> `Pages`.
2.  Change the "Branch" source **back to `main`** (which still contains the original green Version 1.0 `index.html`).
3.  Click "Save".
4.  After a few minutes and a hard refresh, your live site `https://wheelfate.github.io/canary-deployment-demo/` will display the green "Stable Website! Version: 1.0 (Stable)" again.

---

## Live Demo

* **Current Live Version (Canary):** [https://wheelfate.github.io/canary-deployment-demo/](https://wheelfate.github.io/canary-deployment-demo/)
    *(Note: This URL will reflect whatever branch is currently set in GitHub Pages settings.)*
