# Quick Start Guide

Get your first AI model deployed in under 5 minutes.

## Prerequisites

- An OmniDeploy account ([Sign up free](https://omnideploy.info/signup))
- A trained ML model (PyTorch, TensorFlow, ONNX, etc.)

## Step 1: Create an Account

1. Go to [omnideploy.info/signup](https://omnideploy.info/signup)
2. Enter your email and create a password
3. Verify your email

## Step 2: Create a New Deployment

1. Click **"New Deployment"** in your dashboard
2. Select your cloud provider (or use OmniDeploy's infrastructure)
3. Choose your region

## Step 3: Upload Your Model

### Option A: Upload via Dashboard
1. Click **"Upload Model"**
2. Select your model file
3. OmniDeploy auto-detects the framework

### Option B: Connect Git Repository
1. Click **"Connect Repository"**
2. Authorize GitHub/GitLab
3. Select your repository
4. OmniDeploy builds and deploys automatically

## Step 4: Configure Resources

Select your compute requirements:

| Resource | Description |
|----------|-------------|
| **CPU** | 1-8 vCPUs |
| **Memory** | 1-32 GB RAM |
| **GPU** | Optional (T4, A10, A100) |

## Step 5: Deploy!

1. Click **"Deploy"**
2. Wait 30-60 seconds
3. Your model is live!

## Step 6: Test Your Endpoint

```bash
curl -X POST https://your-model.omnideploy.info/predict \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{"input": "Hello, World!"}'
```

## Next Steps

- [Set up BYOC for 30% bonus credits](./byoc.md)
- [Configure auto-scaling](./autoscaling.md)
- [Set up monitoring alerts](./monitoring.md)

---

Need help? Contact support@omnideploy.info
