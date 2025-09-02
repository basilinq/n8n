# Deploy n8n to Render - Complete Guide

## 🚀 Quick Setup (5 minutes)

### Step 1: Prepare Your Repository

1. **Commit your changes** to GitHub:
   ```bash
   git add .
   git commit -m "Add Render deployment configuration"
   git push origin main
   ```

### Step 2: Deploy to Render

1. **Go to [Render.com](https://render.com)**
2. **Sign up/Login** with your GitHub account
3. **Click "New +" → "Web Service"**
4. **Connect your GitHub repository**
5. **Configure the service:**

#### Basic Settings:
- **Name**: `n8n` (or your preferred name)
- **Environment**: `Node`
- **Region**: Choose closest to you
- **Branch**: `main`
- **Root Directory**: Leave empty

#### Build & Deploy:
- **Build Command**: `pnpm install && pnpm build`
- **Start Command**: `pnpm start`

#### Environment Variables:
Add these in the Render dashboard:

```
NODE_ENV=production
N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=admin
N8N_BASIC_AUTH_PASSWORD=your-secure-password-here
N8N_ENCRYPTION_KEY=your-32-character-encryption-key-here
N8N_HOST=your-app-name.onrender.com
N8N_PORT=10000
N8N_PROTOCOL=https
WEBHOOK_URL=https://your-app-name.onrender.com/
N8N_RUNNERS_ENABLED=true
DB_SQLITE_POOL_SIZE=10
N8N_BLOCK_ENV_ACCESS_IN_NODE=false
```

### Step 3: Deploy

1. **Click "Create Web Service"**
2. **Wait for deployment** (5-10 minutes)
3. **Access your n8n** at `https://your-app-name.onrender.com`

## 🔧 Alternative: Using render.yaml (Recommended)

I've created a `render.yaml` file for you. This makes deployment even easier:

1. **Update the render.yaml file**:
   - Replace `your-app-name` with your desired app name
   - Replace `your-secure-password-here` with a strong password
   - Replace `your-32-character-encryption-key-here` with a 32-character key

2. **Deploy**:
   - Go to Render.com
   - Click "New +" → "Blueprint"
   - Connect your GitHub repo
   - Render will automatically detect the `render.yaml` file
   - Click "Apply"

## 🔑 Generate Secure Keys

### Generate Encryption Key:
```bash
# Run this in your terminal
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
```

### Generate Password:
Use a password manager or generate a strong password:
- At least 12 characters
- Mix of letters, numbers, and symbols
- Example: `MySecureN8nPass123!`

## 🌐 Custom Domain (Optional)

1. **In Render dashboard**:
   - Go to your service
   - Click "Settings" → "Custom Domains"
   - Add your domain

2. **Update DNS**:
   - Add a CNAME record pointing to your Render URL
   - Example: `n8n.yourdomain.com` → `your-app-name.onrender.com`

3. **Update environment variables**:
   ```
   N8N_HOST=n8n.yourdomain.com
   WEBHOOK_URL=https://n8n.yourdomain.com/
   ```

## 📊 Monitoring & Management

### Check Deployment Status:
- **Render Dashboard**: Shows build logs and deployment status
- **Service URL**: Access your n8n instance
- **Logs**: View real-time logs in Render dashboard

### Common Commands:
- **Restart service**: Render dashboard → "Manual Deploy"
- **View logs**: Render dashboard → "Logs" tab
- **Update environment**: Render dashboard → "Environment"

## 🛡️ Security Best Practices

1. **Use strong passwords** for basic auth
2. **Generate unique encryption keys**
3. **Enable HTTPS** (automatic on Render)
4. **Regular backups** of your workflows
5. **Monitor access logs**

## 💰 Render Pricing

- **Free Tier**:
  - 750 hours/month
  - Sleeps after 15 minutes of inactivity
  - Perfect for personal use

- **Starter Plan** ($7/month):
  - Always-on service
  - Better for production use

## 🚨 Troubleshooting

### Common Issues:

1. **Build Fails**:
   - Check build logs in Render dashboard
   - Ensure all dependencies are in package.json
   - Verify Node.js version compatibility

2. **Service Won't Start**:
   - Check start command: `pnpm start`
   - Verify environment variables
   - Check logs for error messages

3. **Can't Access n8n**:
   - Verify the service URL
   - Check if service is running (not sleeping)
   - Verify basic auth credentials

### Getting Help:
- **Render Support**: Built-in chat support
- **n8n Community**: [community.n8n.io](https://community.n8n.io)
- **Documentation**: [docs.n8n.io](https://docs.n8n.io)

## 🎯 Next Steps

1. **Deploy to Render** using the steps above
2. **Test your n8n instance** at the provided URL
3. **Create your first workflow**
4. **Set up custom domain** (optional)
5. **Configure backups** for your workflows

Your n8n will be live and accessible from anywhere! 🎉
