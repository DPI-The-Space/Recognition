# How to Update The Space

This guide covers how to make changes to The Space website. The site is a single-page HTML application with data stored in Firebase.

---

## For All Team Members

### Setting Up Your Profile
1. Log in by selecting your team and name
2. Click **Edit Profile** on the left sidebar (or navigate to any profile from the About The Team tab)
3. Fill out your details:
   - **Photo** — Upload a profile picture
   - **Birthday** — Will auto-appear on the calendar
   - **Pronouns**
   - **Favorite Snacks** — Press Enter after each one
   - **Hobbies & Interests** — Press Enter after each one
   - **Fun Fact**
   - **Drink Order**
   - **What I Do** — Describe your day-to-day work in your own words
   - **What Gives You Energy / Drains Your Energy**
4. Click **Save Profile**

### Posting Recognition (Work Announcements)
1. Go to the **Work Announcements** tab
2. Fill out the form on the right:
   - Select your name
   - Add the person(s) you're recognizing
   - Choose one or more recognition categories
   - Write your message
   - Optionally add a photo or GIF
3. Click **Post Recognition**

### Posting Life Updates
1. Go to the **Life Announcements** tab
2. Fill out the form on the right:
   - Select your name
   - Choose a category (Birthday, Wedding, New Pet, etc.)
   - Write your message
   - Optionally add a photo or GIF
3. Click **Post Update**

### Adding Calendar Events
1. Go to the **Calendar** tab
2. Click on any day
3. Fill in the event title, category, time, and description
4. Click **Add Event**

---

## For Admins (Updating the Code)

The website lives in two files:
- `recognition-website/index.html` — Main site (all tabs, logic, and data)
- `recognition-website/profile.html` — Profile editing page

### Adding a New Team Member

1. Open `index.html`
2. Find the `teamMembers` object (search for `const teamMembers`) and add the person's name to the appropriate team array
3. Find the `allMembers` array (search for `const allMembers`) and add the name alphabetically
4. If you know their job title, find the `defaults` object inside the `getProfile` function and add an entry:
   ```javascript
   'New Person Name': { jobTitle: 'Their Charter Title' },
   ```
5. Do the same in `profile.html` — find `const defaultTitles` and add:
   ```javascript
   'New Person Name': 'Their Charter Title',
   ```

### Removing a Team Member

1. Remove their name from the `teamMembers` object (the team they belong to)
2. Remove their name from the `allMembers` array
3. Optionally remove their entry from the `defaults` object

### Changing Team Assignments

Move the person's name from one team array to another in the `teamMembers` object.

### Adding a New Team/Category

1. Add the new team key and member array to `teamMembers`
2. Add a new option to the team filter dropdowns:
   - Login page team picker buttons (search for `team-picker`)
   - Directory filter (search for `dirTeamFilter`)
   - About The Team filter (search for `teamTeamFilter`)
3. Add the team to `teamManagers` if there are designated managers
4. Update `profile.html` team select dropdown

### Updating Job Titles

Find the `defaults` object in the `getProfile` function in `index.html` and update the `jobTitle` value. Also update `defaultTitles` in `profile.html`.

### Adding New Resources

Find the `page-resources` section in `index.html` and add a new link card following the existing format:
```html
<a href="YOUR_URL" target="_blank" style="flex:1;min-width:280px;background:#fff;border-radius:16px;padding:24px;text-decoration:none;box-shadow:0 2px 8px rgba(0,0,0,0.2);border:1px solid #d0dce8;text-align:center;transition:transform 0.15s;">
  <div style="font-size:2rem;margin-bottom:8px;">EMOJI</div>
  <div style="font-size:1rem;font-weight:600;color:#0057b8;">Title</div>
  <div style="font-size:0.8rem;color:#888;margin-top:4px;">Subtitle</div>
</a>
```

---

## Data & Storage

- **Profiles, posts, comments, and calendar events** are stored in Firebase (Firestore)
- **Login state and preferences** are stored in the browser's localStorage
- **No server setup required** — the site runs as a static HTML file

---

## Questions?

Reach out to Malia Jones at malia.jones@spectrum.com
