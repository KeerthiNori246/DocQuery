# DocQuery Deployment Guide

## 🔧 Vercel Deployment Issue Fix

### Problem
When deploying DocQuery to Vercel, users see only an image or error page instead of the full Streamlit application interface.

### Root Cause
Vercel is optimized for static sites and serverless functions, while Streamlit applications require persistent server processes. This creates a compatibility issue.

### ✅ Solutions

#### Option 1: Use Recommended Platforms (Best)
Deploy DocQuery on platforms designed for persistent web applications:

1. **Heroku** (Recommended)
   ```bash
   git push heroku main
   ```
   - Uses the included `Procfile`
   - Perfect for Streamlit apps
   - Free tier available

2. **Railway**
   - Connect your GitHub repository
   - Automatic deployment
   - Great performance

3. **Render**
   - Connect GitHub repository  
   - Free tier available
   - Simple configuration

4. **Streamlit Cloud**
   - Designed specifically for Streamlit apps
   - Direct GitHub integration
   - Free for public repositories

#### Option 2: Use API on Vercel
If you must use Vercel, use the FastAPI backend instead:

1. Deploy to Vercel (API only works)
2. Access endpoints at:
   - `https://your-app.vercel.app/api/health`
   - `https://your-app.vercel.app/api/analyze`

3. Build a custom frontend that calls these APIs

#### Option 3: Hybrid Deployment
- Deploy the Streamlit app on Heroku/Railway
- Deploy API endpoints on Vercel
- Use both services together

### 🔧 Files Added for Vercel Support

1. **`vercel.json`** - Vercel configuration
2. **`index.py`** - Entry point with deployment instructions
3. **`requirements-vercel.txt`** - Minimal dependencies for Vercel
4. **`vercel_error_handler.py`** - Comprehensive Vercel error handling (71+ error codes)
5. **`VERCEL_ERROR_HANDLING.md`** - Complete error handling documentation

### 🚀 Enhanced Error Handling

DocQuery now includes comprehensive error handling for all Vercel error codes:
- **71+ error codes** supported across 9 categories
- **Automatic error detection** and mapping
- **Intelligent suggestions** for error resolution
- **Environment-aware** troubleshooting
- **Complete API coverage** for error testing and status

See [VERCEL_ERROR_HANDLING.md](VERCEL_ERROR_HANDLING.md) for complete documentation.

### 🚀 Quick Fix Implementation

The added files provide:
- Proper error handling for Vercel deployment
- Clear instructions for users
- API endpoint functionality
- Graceful fallback with helpful information

### 💡 Why This Happens

- **Streamlit**: Needs persistent WebSocket connections
- **Vercel**: Designed for stateless serverless functions
- **Solution**: Use appropriate platform or API-only approach

### 📊 Platform Comparison

| Platform | Streamlit Support | Deployment | Cost |
|----------|------------------|------------|------|
| Heroku | ✅ Excellent | `git push` | Free tier |
| Railway | ✅ Excellent | GitHub connect | Paid |
| Render | ✅ Excellent | GitHub connect | Free tier |
| Streamlit Cloud | ✅ Perfect | GitHub connect | Free |
| Vercel | ⚠️ API only | Serverless | Free |

### 🔗 Quick Links

- [Deploy to Heroku](https://devcenter.heroku.com/articles/git)
- [Deploy to Railway](https://railway.app/)
- [Deploy to Render](https://render.com/)
- [Deploy to Streamlit Cloud](https://streamlit.io/cloud)

---

**Recommendation**: Use Heroku, Railway, or Streamlit Cloud for the best DocQuery experience.