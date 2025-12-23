# Configuring SSH authentication between Github and Jenkins

**_DIAGRAM_**
![alt text](images/IMG_3CF1DF59235B-1.jpeg)

## Generate an SSH Key Pair

First, an SSH key pair must be generated locally.

1. Open **Git Bash** and go to the `.ssh` directory:

   ```
   cd ~/.ssh
   ````

2. Generate a new SSH key pair using the following command:

   ```bash
   ssh-keygen -t rsa -b 4096 -C "youremail@example.com"
   ```

### Important Notes

* Press **Enter twice** when prompted for a passphrase (no passphrase is used)
* Provide a **custom name** for the key pair when prompted (e.g. `josephine-jenkins-2-github-key`)

This command generates:

* A **private key** (used by Jenkins)
* A **public key** (added to GitHub)


## View the Public Key

To display the contents of the public key file, run:

```
cat josephine-jenkins-2-github-key.pub
```

Copy the full output — this will be added to GitHub in the next step.


## Configure SSH Key in GitHub

1. Log in to **GitHub**
2. Go to the repository containing the application
3. Then go to:

```
Settings → Deploy Keys → Add deploy key
```

4. Enter:

   * **Title**: A descriptive name (e.g. `josephine-jenkins-2-github-key`)
   * **Key**: Paste the contents of the public key file
5. Enable:
   * **Allow write access**
6. Click **Add key**

This allows Jenkins to authenticate securely with the repository.


## Add SSH Key to Jenkins

When creating or configuring a Jenkins job:

1. Scroll to **Source Code Management**
2. Select **Git**


### Configure Repository Access

* Repository URL (SSH format):

```
git@github.com:josephine-oye/tech515-app-cicd-jenkins.git
```

* Under **Credentials**, click **Add**


### Add Private Key to Jenkins

In the credentials window:

1. Select **Kind**:

   ```
   SSH Username with private key
   ```
2. Enter:

   * **Username**: A descriptive name (e.g. `josephine-jenkins-2-github-key`)
   * **Private Key**: Select **Enter directly**
3. Paste the contents of the **private key file**
4. Click **Add**

Once added, select this credential from the dropdown list.


## Final Configuration

* Ensure the correct credential is selected
* Set the branch specifier to:

```
*/dev
```

Jenkins can now securely authenticate with GitHub using SSH.


## Summary

* SSH keys provide secure, passwordless authentication
* GitHub stores the public key
* Jenkins stores the private key
* Jenkins can now clone and interact with the repository securely
* This setup is essential for CI/CD pipelines that require automation
