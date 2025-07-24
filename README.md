# Create-IAM-User-in-AWS-Console




---

# **Step 1: Create IAM User in AWS Console**

1. **Login to AWS Console** → **IAM service**.
2. Go to **Users** → **Add users**.
3. **User name**: e.g., `vishu`.
4. **Access type**:

   * ✅ **Programmatic access** (for AWS CLI ).
5. **Permissions**:

   * **Attach existing policies directly** → **AdministratorAccess** (for full access).
     *(For real-world, create a custom least-privilege policy).*
6. **Tags**: optional.
7. **Create user**.
8. **Download the `.csv` file** — this contains:

   * **Access Key ID** (like a username).
   * **Secret Access Key** (like a password).

---

# **Step 2: Install AWS CLI**

**Windows (using Chocolatey):**

```powershell
choco install awscli -y
aws --version
```

---

# **Step 3: Configure AWS CLI (using Access Key and Secret Key)**

```powershell
aws configure
# AWS Access Key ID: <Access Key from .csv>
# AWS Secret Access Key: <Secret Key from .csv>
# Default region: us-east-1 (or your choice)
# Default output format: json
```

Test:

```powershell
aws sts get-caller-identity
```

You should see your AWS account ID and the IAM user `atul`.

---

# **Step 4: Use IAM Credentials in GitHub Repo (For CI/CD)**

If you want to **push AWS access to GitHub Actions** (for example, deploying to S3), do **NOT** hardcode keys.
Instead:

1. Go to **GitHub → Your Repository → Settings → Secrets and variables → Actions → New repository secret**.
2. Add:

   * `AWS_ACCESS_KEY_ID` = `<your Access Key>`
   * `AWS_SECRET_ACCESS_KEY` = `<your Secret Key>`
   * (Optional) `AWS_REGION` = `us-east-1`

---

