# BYOC (Bring Your Own Cloud)

Deploy to your own cloud accounts and get **30% bonus credits**.

## What is BYOC?

BYOC allows you to connect your existing AWS, GCP, or Azure accounts to OmniDeploy. Your models run in YOUR infrastructure, giving you:

- ✅ **Full data control** - Data never leaves your cloud
- ✅ **30% bonus credits** - Reduced costs
- ✅ **Compliance** - Meet regulatory requirements
- ✅ **Existing discounts** - Use your cloud credits/savings plans

## Supported Cloud Providers

| Provider | Status | Setup Time |
|----------|--------|------------|
| AWS | ✅ Supported | 5 minutes |
| Google Cloud | ✅ Supported | 5 minutes |
| Azure | ✅ Supported | 5 minutes |
| DigitalOcean | ✅ Supported | 3 minutes |

## How to Connect AWS

### Step 1: Create IAM Role

1. Go to AWS Console → IAM → Roles
2. Click **"Create Role"**
3. Select **"Another AWS Account"**
4. Enter OmniDeploy's Account ID: `123456789012`
5. Enable **"Require external ID"**
6. Enter the External ID from your OmniDeploy dashboard

### Step 2: Attach Policies

Attach these managed policies:
- `AmazonEC2FullAccess`
- `AmazonS3FullAccess`
- `AmazonECRFullAccess`

### Step 3: Connect in OmniDeploy

1. Go to **Dashboard → Cloud Accounts**
2. Click **"Connect AWS"**
3. Enter your Role ARN
4. Click **"Verify & Connect"**

## How to Connect GCP

### Step 1: Create Service Account

```bash
gcloud iam service-accounts create omnideploy \
  --display-name="OmniDeploy Service Account"
```

### Step 2: Grant Permissions

```bash
gcloud projects add-iam-policy-binding YOUR_PROJECT \
  --member="serviceAccount:omnideploy@YOUR_PROJECT.iam.gserviceaccount.com" \
  --role="roles/compute.admin"
```

### Step 3: Download Key

```bash
gcloud iam service-accounts keys create key.json \
  --iam-account=omnideploy@YOUR_PROJECT.iam.gserviceaccount.com
```

### Step 4: Upload to OmniDeploy

1. Go to **Dashboard → Cloud Accounts**
2. Click **"Connect GCP"**
3. Upload your `key.json`
4. Click **"Verify & Connect"**

## How to Connect Azure

### Step 1: Create Service Principal

```bash
az ad sp create-for-rbac --name "OmniDeploy" \
  --role contributor \
  --scopes /subscriptions/YOUR_SUBSCRIPTION_ID
```

### Step 2: Note Credentials

Save the output:
- `appId` (Client ID)
- `password` (Client Secret)
- `tenant` (Tenant ID)

### Step 3: Connect in OmniDeploy

1. Go to **Dashboard → Cloud Accounts**
2. Click **"Connect Azure"**
3. Enter your credentials
4. Click **"Verify & Connect"**

## BYOC Benefits

| Benefit | Without BYOC | With BYOC |
|---------|--------------|-----------|
| Credits per ₹100 | 100 | 130 (+30%) |
| Data location | OmniDeploy cloud | Your cloud |
| Compliance | Standard | Your compliance |

## FAQ

**Q: Is my data secure with BYOC?**
A: Yes! Your data never leaves your cloud account. OmniDeploy only orchestrates deployments.

**Q: Can I use reserved instances?**
A: Yes! BYOC uses your existing cloud resources, including reserved instances and savings plans.

**Q: What if I disconnect BYOC?**
A: Your deployments continue running. You can migrate to OmniDeploy infrastructure anytime.

---

Need help setting up BYOC? Contact support@omnideploy.info
