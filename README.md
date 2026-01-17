# 🎓 SSC 2027 Batch Name Voting System

A real-time voting platform for SOS Hermann Gmeiner College, Bogura students to vote on their batch name.

## ✨ Features

✅ **Real-time Updates** - See votes update instantly across all devices  
✅ **Supabase Integration** - Cloud database with CDN-based SDK  
✅ **Voter Protection** - One vote per device/browser using localStorage  
✅ **Beautiful UI** - Clean, modern design with animated bar charts  
✅ **Mobile Responsive** - Works perfectly on phones, tablets, and desktops  
✅ **No Backend Required** - Deploy directly to GitHub Pages  

## 🚀 Quick Start

### 1. Set Up Supabase Database

1. **Create a Supabase account** at [supabase.com](https://supabase.com)
2. **Create a new project**
3. **Run the SQL setup**:
   - Open the SQL Editor in Supabase
   - Copy the contents of `supabase_setup.sql`
   - Paste and run in the SQL Editor
4. **Get your credentials**:
   - Go to Settings → API
   - Copy your Project URL and anon public key

### 2. Configure the HTML File

1. Open `index.html` in a text editor
2. Find these lines (around line 479-480):
   ```javascript
   const SUPABASE_URL = 'https://YOUR_PROJECT_ID.supabase.co';
   const SUPABASE_ANON_KEY = 'YOUR_ANON_KEY_HERE';
   ```
3. Replace with your actual Supabase credentials
4. Save the file

### 3. Test Locally

1. Double-click `index.html` to open in your browser
2. Try casting a vote
3. Open in another browser to see real-time updates

### 4. Deploy to GitHub Pages

1. Create a new GitHub repository
2. Upload `index.html`
3. Enable GitHub Pages in Settings → Pages
4. Your site will be live at: `https://yourusername.github.io/repo-name/`

## 📚 Documentation

- **[SUPABASE_COMPLETE_SETUP.md](SUPABASE_COMPLETE_SETUP.md)** - Detailed step-by-step setup guide
- **[supabase_setup.sql](supabase_setup.sql)** - SQL commands for database setup

## 🗳️ How It Works

### Voting Flow
1. User selects a batch name and clicks "Vote"
2. Confirmation dialog appears
3. Vote is submitted to Supabase using **upsert logic**:
   - If batch name exists → increment vote_count
   - If batch name doesn't exist → insert new record with vote_count = 1
4. localStorage marks the user as "voted"
5. Vote buttons are disabled
6. Results update in real-time

### Real-time Updates
- Uses Supabase Realtime (PostgreSQL Change Data Capture)
- Subscribes to `votes_2027` table changes
- Automatically updates UI when any vote is cast
- Highlights updated results with animation

### Voter Protection
- Uses `localStorage` to track voting status
- Key: `ssc2027_voted` (value: "true")
- Persists across page refreshes
- One vote per browser/device

## �️ Technical Stack

- **Frontend**: Pure HTML, CSS, JavaScript (no frameworks)
- **Database**: Supabase (PostgreSQL)
- **Real-time**: Supabase Realtime Channels
- **CDN**: Supabase JS SDK v2 via jsdelivr
- **Hosting**: GitHub Pages (or any static host)

## 📊 Database Schema

```sql
votes_2027
├── id (BIGSERIAL, PRIMARY KEY)
├── batch_name (TEXT, UNIQUE, NOT NULL)
├── vote_count (INTEGER, DEFAULT 0)
├── created_at (TIMESTAMPTZ)
└── updated_at (TIMESTAMPTZ)
```

## � Batch Names

The voting includes 23 batch name options with Bangla meanings:

1. Astric - তারার মতো উজ্জ্বল ও আলোকিত
2. Aurelius - সোনালি গৌরব ও রাজকীয় মর্যাদা
3. Ascendants - সবার উপরে উঠে যাওয়ার প্রতীক
4. Eminence - শ্রেষ্ঠত্ব ও সম্মানজনক অবস্থান
5. Vanguards - ভবিষ্যতের পথপ্রদর্শক
... and 18 more!

## � Security Features

- **Row Level Security (RLS)** enabled on Supabase
- **Public read access** for viewing results
- **Public insert/update** for voting (protected by localStorage)
- **XSS protection** with HTML escaping
- **HTTPS only** for production deployment

## 🐛 Troubleshooting

### Votes not submitting?
- Check browser console (F12) for errors
- Verify Supabase credentials are correct
- Ensure RLS policies are set up

### Real-time not working?
- Verify Realtime is enabled in Supabase
- Check that `ALTER PUBLICATION` was run
- Refresh the page

### "Already voted" but didn't vote?
- Clear localStorage: Open DevTools → Application → Local Storage → Delete `ssc2027_voted`

## 📱 Browser Support

- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

## 📄 License

© 2027 SSC Batch | SOS Hermann Gmeiner College, Bogura  
All Rights Reserved

## 🤝 Contributing

This is a closed voting system for SSC 2027 batch students only.

## 📞 Support

For technical issues, check the troubleshooting section in `SUPABASE_COMPLETE_SETUP.md`

---

**Made with ❤️ for SSC 2027 Batch**
