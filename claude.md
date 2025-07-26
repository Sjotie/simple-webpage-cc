# Railway Project Information

## Project Details
- **Project Name**: simple-webpage-cc
- **Project ID**: 2cd33e9b-83fe-4530-9436-eb863ee1322c
- **Environment**: production (ID: d408a5dd-9e52-45e9-af15-d22f07f19e88)

## Service Details
- **Service Name**: simple-webpage-service
- **Service ID**: 6950ee7d-e4b3-4472-87d3-98578a1e48cb
- **Domain**: https://simple-webpage-service-production.up.railway.app
- **Region**: us-west1

## Configuration
- **Build Command**: npm install
- **Start Command**: npm start
- **Builder**: RAILPACK (as specified in railway.json)

## Deployment Notes
This is a simple Node.js/Express website that serves static files. The project uses:
- Express.js for the web server
- Static file serving for HTML, CSS, and JavaScript files
- Railway's automatic port detection (PORT environment variable)

To deploy updates to this project, use the Railway CLI:
```bash
railway link 2cd33e9b-83fe-4530-9436-eb863ee1322c
railway up
```