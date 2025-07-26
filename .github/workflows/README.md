# GitHub Actions Guide

This folder contains GitHub Actions workflows for CI/CD and automation. Here's what each workflow does and how to use them.

## 🚀 Quick Start

### Setting up Railway Deployment

1. **Get your Railway Token**:
   - Go to [Railway Dashboard](https://railway.app/account/tokens)
   - Create a new token
   - Copy the token value

2. **Add the token to GitHub**:
   - Go to your GitHub repository
   - Navigate to Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Name: `RAILWAY_TOKEN`
   - Value: Paste your Railway token
   - Click "Add secret"

3. **Push to main branch** and watch the magic happen!

## 📁 Workflow Files

### 1. `deploy.yml` - Main CI/CD Pipeline
**What it does**: Tests your code and deploys to Railway
- ✅ Runs on every push to main
- ✅ Tests on Node.js 18 and 20
- ✅ Automatically deploys if tests pass
- ✅ Runs on pull requests (test only, no deploy)

### 2. `hello-world.yml` - Simplest Example
**What it does**: Basic workflow structure demo
- 👋 Prints "Hello, World!"
- 📅 Shows current date/time
- ℹ️ Displays workflow information
- 🎯 Can be manually triggered

### 3. `schedule-example.yml` - Automated Tasks
**What it does**: Runs tasks on a schedule
- ⏰ Runs every Monday at 9 AM UTC
- 🧹 Example of cleanup tasks
- 📢 Shows how to use webhooks
- 🔧 Can be manually triggered for testing

### 4. `pr-checks.yml` - Pull Request Automation
**What it does**: Validates pull requests
- 🔍 Checks for large files
- 🔐 Scans for hardcoded secrets
- 🏷️ Auto-labels PRs (example)
- 💬 Comments on new PRs

### 5. `matrix-testing.yml` - Multi-Environment Testing
**What it does**: Tests across different platforms
- 🖥️ Tests on Ubuntu, Windows, and macOS
- 📦 Tests on Node.js 16, 18, and 20
- ⚡ Runs tests in parallel
- 🎯 Platform-specific steps

### 6. `release.yml` - Automated Releases
**What it does**: Creates GitHub releases from tags
- 🏷️ Triggers on version tags (v1.0.0)
- 📝 Generates changelog automatically
- 📦 Builds and uploads artifacts
- 🚀 Creates GitHub releases

### 7. `secrets-and-envs.yml` - Variables Demo
**What it does**: Shows how to use secrets and variables
- 🔐 Demonstrates secret usage
- 🌍 Shows environment variables
- 📤 Passes data between steps
- ℹ️ Uses GitHub context variables

## 🎯 Common GitHub Actions Concepts

### Triggers (`on`)
```yaml
on:
  push:               # On code push
  pull_request:       # On PR creation/update  
  schedule:           # On schedule (cron)
  workflow_dispatch:  # Manual trigger
```

### Job Dependencies
```yaml
jobs:
  test:
    # ... test steps
  deploy:
    needs: test  # Only run after test succeeds
```

### Conditional Execution
```yaml
if: github.ref == 'refs/heads/main'  # Only on main branch
if: github.event_name == 'push'       # Only on push events
if: always()                          # Run even if previous steps fail
```

### Using Secrets
```yaml
env:
  API_KEY: ${{ secrets.API_KEY }}  # Never hardcode secrets!
```

### Matrix Strategy
```yaml
strategy:
  matrix:
    os: [ubuntu-latest, windows-latest]
    node: [16, 18, 20]
```

## 📚 Learning Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow Syntax Reference](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)

## 🛠️ Useful Commands

**Manually trigger a workflow**:
1. Go to Actions tab in GitHub
2. Select the workflow
3. Click "Run workflow"

**View workflow runs**:
- Check the Actions tab in your repository
- Green ✅ = Success
- Red ❌ = Failed
- Yellow 🟡 = In progress

## 💡 Tips

1. **Start simple**: Begin with `hello-world.yml` to understand basics
2. **Use marketplace actions**: Don't reinvent the wheel
3. **Test locally**: Use [act](https://github.com/nektos/act) to test workflows locally
4. **Keep secrets secret**: Never commit tokens or passwords
5. **Cache dependencies**: Use caching to speed up workflows
6. **Use matrix testing**: Test multiple versions efficiently

## 🚨 Troubleshooting

**Workflow not running?**
- Check if file is in `.github/workflows/`
- Verify YAML syntax is correct
- Ensure branch/event matches trigger conditions

**Deployment failing?**
- Verify `RAILWAY_TOKEN` is set correctly
- Check Railway service name matches
- Look at workflow logs for errors

**Tests failing?**
- Run tests locally first
- Check Node.js version compatibility
- Review error logs in Actions tab