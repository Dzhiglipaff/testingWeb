# Deployment to Render

## Prerequisites
- GitHub account with this repository pushed
- Render account (free tier available at render.com)

## Quick Start

1. **Push to GitHub** (if not already done):
   ```bash
   git add .
   git commit -m "Prepare for Render deployment"
   git push origin main
   ```

2. **Deploy on Render**:
   - Go to [render.com](https://render.com)
   - Click "New +" > "Web Service"
   - Connect your GitHub account and select this repository
   - Render will auto-detect the `render.yaml` file
   - Click "Create Web Service"

## Manual Alternative (without render.yaml)
1. Create a new Web Service on Render
2. Set the build command: `pip install -r requirements.txt`
3. Set the start command: `gunicorn --bind 0.0.0.0:$PORT app:app`
4. Add environment variable: `FLASK_ENV=production`

## Database Notes
This app uses SQLite. For production with Render:
- SQLite data will NOT persist across app restarts
- Consider migrating to PostgreSQL for production reliability
- For now, the app will work but data resets on redeployment

## Troubleshooting
- Check build logs on the Render dashboard
- Ensure `Procfile`, `render.yaml`, and `requirements.txt` are in root directory
- Check environment variables in Render dashboard if app fails to start
