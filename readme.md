#   To-Do Dashboard

## 📸 Screenshots

<p align="center">
  <img src="https://github.com/fumioryoto/todo-dashboard/raw/main/Screenshot.png" alt="Dashboard" width="1500">
</p>

A modern React-based to-do dashboard deployed on GitHub Pages with Google Sheets integration. Manage your tasks with automatic syncing to your own Google Sheet.

## ✨ Features

- ✅ Add, edit, and manage tasks
- 📅 Schedule tasks for specific dates
- 🔄 Set recurring tasks (repeat on specific days)
- ✔️ Mark tasks as done
- 🗑️ Remove and restore tasks
- 🔗 Google Drive link extractor
- 📊 Integrated with Google Sheets for data storage
- 🌐 Deployed on GitHub Pages (no backend needed)
- 💾 Offline support with localStorage fallback
- 📱 Responsive design with Tailwind CSS

## 🚀 Quick Start

### Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- GitHub account
- Google Cloud Project with OAuth credentials

### Step 1: Fork/Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/todo-dashboard.git
cd todo-dashboard
```

### Step 2: Install Dependencies

```bash
npm install
```

### Step 3: Google Cloud Setup

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. **Enable APIs:**
   - Search for and enable the **Google Sheets API**
4. **Create OAuth 2.0 Credentials:**
   - Go to Credentials → Create Credentials → OAuth 2.0 Client ID
   - Choose "Web application"
   - Add authorized JavaScript origins:
     - `http://localhost:3000` (for local development)
     - `https://YOUR_USERNAME.github.io` (for production)
   - Add authorized redirect URIs:
     - `http://localhost:3000` (for local development)
     - `https://YOUR_USERNAME.github.io` (for production)
   - Copy the **Client ID**

5. (Optional) Create an API Key:
   - Go to Credentials → Create Credentials → API Key
   - Copy the **API Key**

### Step 4: Environment Variables

Create a `.env` file in the root directory:

```env
REACT_APP_GOOGLE_CLIENT_ID=YOUR_CLIENT_ID_HERE
REACT_APP_GOOGLE_API_KEY=YOUR_API_KEY_HERE
```

Or copy from the example:

```bash
cp .env.example .env
# Edit .env with your credentials
```

### Step 5: Create Google Sheet

1. Create a new Google Sheet: https://sheets.google.com
2. Create two sheets/tabs:
   - **Todos** - for active tasks
   - **Removed** - for deleted tasks
3. Add headers in row 1 of each sheet:
   ```
   ID | Task | Date | RepeatDays | Done
   ```
4. Copy the sheet ID from the URL:
   - URL: `https://docs.google.com/spreadsheets/d/SHEET_ID_HERE/edit`
   - Keep this ID handy for the app

### Step 6: Local Development

```bash
npm start
```

Visit `http://localhost:3000` and test the app locally.

### Step 7: Deploy to GitHub Pages

#### Option A: Using GitHub Actions (Automatic)

1. Push your code to GitHub:

   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. Go to your GitHub repository → Settings → Secrets and variables → Actions
3. Add these secrets:
   - `GOOGLE_CLIENT_ID` - Your OAuth Client ID
   - `GOOGLE_API_KEY` - Your API Key (optional)

4. Update `package.json`:

   ```json
   "homepage": "https://YOUR_USERNAME.github.io/todo-dashboard"
   ```

5. Push the changes. GitHub Actions will automatically build and deploy!

#### Option B: Manual Deployment

1. Update `package.json`:

   ```json
   "homepage": "https://YOUR_USERNAME.github.io/todo-dashboard"
   ```

2. Build and deploy:

   ```bash
   npm run build
   npm run deploy
   ```

3. Enable GitHub Pages in your repository settings

## 📖 Usage Guide

### First Time Setup

1. Click **"Sign In with Google"** button
2. Authorize the app to access Google Sheets
3. Paste your Google Sheet URL or ID
4. Click **"Load"** to sync existing tasks

### Adding Tasks

1. Enter task name in the input field
2. (Optional) Select a date
3. (Optional) Choose days for recurring tasks
4. Click **"Add"**

### Viewing Tasks

- **Pending**: Today's tasks not yet completed
- **Done**: Completed tasks from today
- **Scheduled**: Tasks with dates or recurring patterns
- **Removed**: Deleted tasks (can restore or permanently delete)

### Managing Tasks

- Click **"Mark Done"** to complete a task
- Click the **delete button** (🗑️) to remove a task
- Tasks automatically sync with Google Sheets

## 🔄 Data Sync

### Auto-Sync Features

- Changes automatically save to Google Sheets (1-second debounce)
- Tasks also saved to browser localStorage as backup
- If offline, app works with localStorage data
- Syncs back when online

### Offline Support

- App works without internet using localStorage
- All changes are preserved locally
- Sync to Google Sheets when back online

## 🎨 Customization

### Change App Title

Edit `src/App.js`:

```javascript
<h1 className="text-3xl font-bold mb-4 text-center">Your App Title</h1>
```

### Update Styles

- App uses Tailwind CSS
- Edit `tailwind.config.js` for theme customization
- Edit `src/index.css` for global styles

## 🔒 Security Notes

- ✅ OAuth 2.0 authentication (your data, your control)
- ✅ No sensitive data stored on servers
- ✅ Data stored in your Google Drive
- ✅ Authorization tokens managed by Google

## 🐛 Troubleshooting

### "Sign In with Google" button doesn't work

- Check that `REACT_APP_GOOGLE_CLIENT_ID` is set correctly
- Ensure your GitHub Pages URL is in Google Console authorized origins
- Check browser console for error messages

### Can't load Google Sheet

- Verify Google Sheets ID is correct
- Ensure you have the correct permissions on the sheet
- Try clearing browser storage: `localStorage.clear()`

### Changes not syncing

- Check that you're signed in with Google
- Verify internet connection
- Check browser console for API errors
- Data is still saved locally to localStorage

### "Failed to load data" error

- Check that the spreadsheet ID is correct
- Ensure the sheet has "Todos" and "Removed" tabs
- Verify column headers: ID, Task, Date, RepeatDays, Done
- Check Google Console for API quota issues

## 📝 Environment Setup for CI/CD

In GitHub Actions workflow, secrets are automatically used:

```yaml
env:
  REACT_APP_GOOGLE_CLIENT_ID: ${{ secrets.GOOGLE_CLIENT_ID }}
  REACT_APP_GOOGLE_API_KEY: ${{ secrets.GOOGLE_API_KEY }}
```

## 📱 Responsive Design

The app is fully responsive and works on:

- 📱 Mobile phones (iOS, Android)
- 📱 Tablets
- 💻 Desktop browsers

## 🤝 Contributing

Feel free to submit issues and enhancement requests!

## 📄 License

This project is open source and available under the MIT License.

## 📞 Support

For issues or questions:

1. Check the Troubleshooting section
2. Review Google Cloud Console settings
3. Check browser console for error messages
4. Open an issue on GitHub

---

**Made with ❤️ for productivity**
