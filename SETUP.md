# CoreInventory Setup Guide

## Prerequisites

1. **Node.js** (v14 or higher)
2. **MongoDB Atlas Account** (FREE cloud database)
3. **npm** or **yarn**

## Step 1: Setup MongoDB Atlas (Cloud Database)

### Create MongoDB Atlas Account
1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Click **"Try Free"** and sign up
3. Verify your email address

### Create Free Cluster
1. Click **"Build a Database"**
2. Choose **"M0 Sandbox"** (FREE - 512MB)
3. Select cloud provider and region closest to you
4. Click **"Create Cluster"**

### Configure Access
1. **Network Access**: Add IP address **"0.0.0.0/0"** (Allow from anywhere)
2. **Database User**: Create user with username `coreinventory` and a strong password
3. **Permissions**: Grant **"Read and write to any database"**

### Get Connection String
1. Go to **Clusters** → **Connect** → **"Connect your application"**
2. Select **Node.js** driver
3. Copy the connection string

## Step 2: Configure Backend

1. **Navigate to backend directory:**
```bash
cd backend
```

2. **Update .env file with your Atlas connection:**
```env
MONGODB_URI=mongodb+srv://your_username:your_password@cluster0.xxxxx.mongodb.net/coreinventory?retryWrites=true&w=majority
```

3. **Install dependencies:**
```bash
npm install
```

4. **Setup the database:**
```bash
npm run setup
```

This will:
- Connect to your MongoDB Atlas cluster
- Create the `coreinventory` database
- Set up all necessary collections and indexes
- Create a default admin user
- Add sample data (warehouse and products)

5. **Start the backend server:**
```bash
npm run dev
```

The backend will run on `http://localhost:5000`

## Step 3: Setup Frontend

1. **Open a new terminal and navigate to frontend directory:**
```bash
cd frontend
```

2. **Install dependencies:**
```bash
npm install
```

3. **Start the frontend development server:**
```bash
npm start
```

The frontend will run on `http://localhost:3000`

## Step 4: Login to the Application

1. Open your browser and go to `http://localhost:3000`
2. You'll be redirected to the login page
3. **Login with default admin credentials:**
   - Email: `admin@coreinventory.com`
   - Password: `admin123`

## Default Data Created

### Admin User
- Email: `admin@coreinventory.com`
- Password: `admin123`
- Role: `admin`

### Sample Warehouse
- Name: `Main Warehouse`
- Code: `WH001`

### Sample Products
1. Steel Rods (SR001) - 100 pieces
2. Cement Bags (CB001) - 250 bags
3. Power Drill (PD001) - 15 units
4. Safety Helmet (SH001) - 75 pieces
5. Paint Bucket (PB001) - 30 buckets

## Why MongoDB Atlas?

✅ **FREE Tier**: 512MB storage - perfect for development
✅ **No Installation**: No need to install MongoDB locally
✅ **Cloud-based**: Access from anywhere
✅ **Automatic Backups**: Built-in backup and recovery
✅ **Scalable**: Easy to upgrade when needed
✅ **Secure**: Built-in security features

## Troubleshooting

### MongoDB Atlas Connection Issues
1. Check your username and password in `.env`
2. Ensure IP address is whitelisted (0.0.0.0/0)
3. Verify cluster name is correct
4. Make sure your cluster is created and running

### Setup Script Issues
1. Verify the connection string is correct
2. Check that the cluster is not paused
3. Ensure your user has proper permissions

### Port Already in Use
If port 5000 is already in use, change it in the `.env` file:
```
PORT=5001
```

### Frontend Not Loading
1. Make sure the backend is running first
2. Check that both servers are running in separate terminals
3. Verify the proxy setting in `frontend/package.json`

## OTP Testing

The system uses console-based OTP for testing. When you register a new user:
1. Check the backend terminal for the OTP message
2. Use that OTP to verify your email

## Production Deployment

For production:
1. Change the `JWT_SECRET` in `.env`
2. Set up a real email service for OTP
3. Upgrade to paid Atlas tier if needed
4. Configure proper security settings

## Next Steps

1. Create additional users with different roles
2. Add more warehouses and products
3. Test creating receipts, deliveries, and adjustments
4. Explore the Atlas dashboard for monitoring

## Support

If you encounter any issues:
1. Check the MongoDB Atlas setup guide: `MONGODB_ATLAS_SETUP.md`
2. Verify your Atlas cluster is running
3. Check the console for error messages
4. Make sure both backend and frontend are running

## Atlas Dashboard Features

Once connected, you can:
- View your data in the Atlas dashboard
- Monitor database performance
- Set up alerts and backups
- Use Atlas Search for advanced queries
- Create charts and visualizations
