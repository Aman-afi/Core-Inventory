# MongoDB Atlas Setup Guide

## Step 1: Create MongoDB Atlas Account

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Click **"Try Free"** or **"Sign Up"**
3. Sign up with Google, GitHub, or email
4. Verify your email address

## Step 2: Create a New Cluster

1. After logging in, click **"Build a Database"**
2. Choose **"M0 Sandbox"** (FREE tier - 512MB)
3. Select a cloud provider and region (choose one closest to you)
4. **Cluster Name**: Keep default or change to `coreinventory-cluster`
5. Click **"Create Cluster"**

## Step 3: Configure Network Access

1. While cluster is being created, go to **"Network Access"** in the left sidebar
2. Click **"Add IP Address"**
3. Select **"Allow Access from Anywhere"** (0.0.0.0/0)
4. Click **"Confirm"**

## Step 4: Create Database User

1. Go to **"Database Access"** in the left sidebar
2. Click **"Add New Database User"**
3. **Authentication Method**: Choose **"Password"**
4. **Username**: `coreinventory` (or your preferred username)
5. **Password**: Create a strong password (save it!)
6. **Database User Privileges**: Check **"Read and write to any database"**
7. Click **"Add User"**

## Step 5: Get Connection String

1. Go back to **"Clusters"** page
2. Click **"Connect"** button for your cluster
3. Choose **"Connect your application"**
4. Select **"Node.js"** and version **"4.1 or later"**
5. Copy the connection string

## Step 6: Update Your .env File

Replace the MongoDB URI in your `.env` file:

```env
MONGODB_URI=mongodb+srv://YOUR_USERNAME:YOUR_PASSWORD@cluster0.xxxxx.mongodb.net/coreinventory?retryWrites=true&w=majority
```

Replace:
- `YOUR_USERNAME` with your database username
- `YOUR_PASSWORD` with your database password  
- `cluster0.xxxxx` with your actual cluster name from the connection string

## Step 7: Setup Your Application

1. **Install dependencies and setup database:**
```bash
cd backend
npm install
npm run setup
```

2. **Start the backend server:**
```bash
npm run dev
```

3. **Start the frontend:**
```bash
cd frontend
npm install
npm start
```

## Step 8: Test the Connection

The setup script will:
- Connect to your MongoDB Atlas cluster
- Create the `coreinventory` database
- Set up all collections and indexes
- Create sample data

If successful, you'll see:
```
✅ Connected to MongoDB successfully!
✅ Database indexes created successfully!
✅ Default admin user created:
✅ Sample warehouse created
✅ Sample products created successfully!
✅ Database setup completed successfully!
```

## Benefits of MongoDB Atlas

✅ **Free Tier**: 512MB storage - perfect for development
✅ **No Installation**: No need to install MongoDB locally
✅ **Cloud-based**: Access from anywhere
✅ **Automatic Backups**: Built-in backup and recovery
✅ **Scalable**: Easy to upgrade when needed
✅ **Secure**: Built-in security features

## Troubleshooting

### Connection Failed
1. Check your username and password in `.env`
2. Ensure IP address is whitelisted (0.0.0.0/0)
3. Verify cluster name is correct
4. Make sure your cluster is created and running

### Free Tier Limits
- **512MB storage**: Monitor your database size
- **Connection limits**: May need to optimize queries
- **Rate limiting**: Consider connection pooling for production

### Production Considerations
- Upgrade to paid tier for production
- Use environment-specific configurations
- Implement proper error handling
- Set up monitoring and alerts

## Connection String Example

Your final connection string should look like:
```
mongodb+srv://coreinventory:MySecurePassword123@cluster0.abcde.mongodb.net/coreinventory?retryWrites=true&w=majority
```

## Security Notes

⚠️ **Important**: Never commit your `.env` file to version control!
- Add `.env` to `.gitignore`
- Use different credentials for development and production
- Rotate passwords regularly
- Use IP whitelisting in production

## Next Steps

1. Test the application with your Atlas database
2. Explore the Atlas dashboard for monitoring
3. Consider setting up backups and alerts
4. Learn about Atlas features like Atlas Search and Charts

That's it! Your CoreInventory system is now running on MongoDB Atlas cloud database! 🚀
