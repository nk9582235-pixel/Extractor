# Your Deployment Configuration

## MongoDB Atlas Connection

Your MongoDB Atlas cluster is already set up! Here are your credentials:

**Connection String:**
```
mongodb+srv://nk9582235_db_user:Ia9NKRoQXPsM5szz@cluster0.akuzmvw.mongodb.net/?appName=Cluster0
```

**Database Name:**
```
classplus_extractor
```

---

## Quick Setup for Local Testing

### Step 1: Create .env File

Create a file named `.env` in the project root with the following content:

```bash
# Telegram Bot Configuration
BOT_TOKEN=your_telegram_bot_token_here

# MongoDB Configuration (Already Set Up!)
MONGODB_URI=mongodb+srv://nk9582235_db_user:Ia9NKRoQXPsM5szz@cluster0.akuzmvw.mongodb.net/?appName=Cluster0
DATABASE_NAME=classplus_extractor

# ClassPlus API Configuration
CLASSPLUS_BASE_URL=https://api.classplusapp.com
API_TIMEOUT=30
MAX_RETRIES=3

# Caching
CACHE_ENABLED=True
CACHE_DIR=./cache/batch_files

# Logging
LOG_LEVEL=INFO
```

### Step 2: Get Telegram Bot Token

1. Open Telegram and search for `@BotFather`
2. Send: `/newbot`
3. Follow the prompts to create your bot
4. Copy the bot token
5. Replace `your_telegram_bot_token_here` in `.env` with your actual token

### Step 3: Test Locally

```bash
# Install dependencies
pip install -r requirements.txt

# Run the bot
python telegram_bot.py
```

---

## Render.com Deployment

### Environment Variables to Set on Render

When deploying to Render.com, add these environment variables:

| Variable | Value |
|----------|-------|
| `BOT_TOKEN` | Your Telegram bot token from @BotFather |
| `MONGODB_URI` | `mongodb+srv://nk9582235_db_user:Ia9NKRoQXPsM5szz@cluster0.akuzmvw.mongodb.net/?appName=Cluster0` |
| `DATABASE_NAME` | `classplus_extractor` |
| `CACHE_DIR` | `/tmp/cache/batch_files` |
| `LOG_LEVEL` | `INFO` |

### Deployment Steps

1. **Push to GitHub:**
   ```bash
   git add .
   git commit -m "Ready for deployment"
   git push origin main
   ```

2. **Deploy on Render:**
   - Go to [render.com](https://render.com)
   - Connect your GitHub repository
   - Add the environment variables above
   - Click "Create Web Service"

3. **Wait for deployment** (2-3 minutes)

4. **Test your bot** in Telegram!

---

## MongoDB Atlas Configuration

Your MongoDB Atlas cluster is already configured with:

- ✅ **Cluster**: cluster0.akuzmvw.mongodb.net
- ✅ **User**: nk9582235_db_user
- ✅ **Database**: classplus_extractor (will be created automatically)

**Important Notes:**

1. **Network Access**: Make sure `0.0.0.0/0` is whitelisted in MongoDB Atlas
   - Go to MongoDB Atlas → Network Access
   - Add IP Address: `0.0.0.0/0` (Allow from anywhere)
   - This is required for Render.com to connect

2. **Database User**: Your user `nk9582235_db_user` should have read/write permissions
   - Go to MongoDB Atlas → Database Access
   - Verify user has "Read and write to any database" role

---

## Security Notes

⚠️ **IMPORTANT**: 

1. **Never commit `.env` file to GitHub** - It's already in `.gitignore`
2. **Keep your MongoDB password secure** - Don't share it publicly
3. **Keep your bot token secret** - Anyone with it can control your bot

The `.gitignore` file is configured to protect:
- `.env` (your local credentials)
- `cache/` (downloaded files)
- `*.log` (log files)
- `__pycache__/` (Python cache)

---

## Testing Checklist

Before deploying, verify:

- [ ] MongoDB Atlas cluster is running
- [ ] Network access allows `0.0.0.0/0`
- [ ] Database user has correct permissions
- [ ] Telegram bot created with @BotFather
- [ ] Bot token obtained
- [ ] `.env` file created locally (for testing)
- [ ] Code pushed to GitHub
- [ ] `.env` file NOT in GitHub (check .gitignore)

---

## Next Steps

1. **Get your Telegram bot token** from @BotFather
2. **Test locally** using the `.env` file
3. **Push to GitHub** (without .env file)
4. **Deploy to Render.com** with environment variables
5. **Test in Telegram**!

---

## Troubleshooting

### MongoDB Connection Issues

If you see "MongoDB connection failed":

1. Check Network Access in MongoDB Atlas
2. Verify IP `0.0.0.0/0` is whitelisted
3. Confirm password is correct in connection string
4. Test connection string format

### Bot Not Responding

If bot doesn't respond:

1. Check Render logs for errors
2. Verify `BOT_TOKEN` is set correctly
3. Make sure bot is running (check Render dashboard)
4. Test bot token with @BotFather

---

## Support

Need help? Check:
- [DEPLOYMENT.md](DEPLOYMENT.md) - Full deployment guide
- [QUICKSTART.md](QUICKSTART.md) - Quick start guide
- Render logs - For runtime errors
- MongoDB Atlas logs - For database issues

**Your MongoDB is ready! Just get your Telegram bot token and you're good to go! 🚀**
