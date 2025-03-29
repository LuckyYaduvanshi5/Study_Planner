# 📚 Study Planner

<p align="center">
  <img src="https://raw.githubusercontent.com/LuckyYaduvanshi5/Study-Planner/main/public/logo192.png" alt="Study Planner Logo" width="200" />
</p>

A comprehensive web application to help students organize their study tasks and schedules effectively.

## ✨ Features

- 🔐 **User Authentication**: Secure signup and login using Supabase authentication
- ✅ **Task Management**: Create, track, and complete study tasks with due dates
- 🗓️ **Schedule Planning**: Plan your weekly study schedule by subject and day
- 📊 **Progress Tracking**: Visualize your task completion with interactive charts
- 📱 **Responsive Design**: Works on desktop and mobile devices

## 🛠️ Tech Stack

- **Frontend**: React.js, React Router, Bootstrap, Tailwind CSS
- **Backend**: Supabase (PostgreSQL database with REST API)
- **Authentication**: Supabase Auth
- **Charts**: Chart.js with react-chartjs-2

## 🚀 Installation and Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/LuckyYaduvanshi5/Study-Planner.git
   cd Study-Planner
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the root directory with your Supabase credentials:
   ```env
   REACT_APP_SUPABASE_URL=your_supabase_url
   REACT_APP_SUPABASE_ANON_KEY=your_supabase_anon_key
   ```

4. Start the development server:
   ```bash
   npm start
   ```

## 💾 Database Setup

<p align="center">
  <img src="https://supabase.com/images/logo-preview.jpg" alt="Supabase Logo" width="300" />
</p>

1. Create a [Supabase](https://supabase.io) account and project
2. Set up the following tables:

```sql
-- Users table
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  email TEXT UNIQUE NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  last_login TIMESTAMP
);

-- Tasks table
CREATE TABLE tasks (
  id SERIAL PRIMARY KEY,
  user_id INTEGER REFERENCES users(id),
  task_name TEXT NOT NULL,
  due_date TIMESTAMP,
  completed BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Schedules table
CREATE TABLE schedules (
  id SERIAL PRIMARY KEY,
  user_id INTEGER REFERENCES users(id),
  day TEXT NOT NULL,
  subject TEXT NOT NULL,
  study_hours NUMERIC NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

3. Enable Row Level Security (RLS) policies:

```sql
CREATE POLICY "Users can manage their own tasks"
ON tasks
FOR ALL
USING (auth.uid() = user_id);

CREATE POLICY "Users can manage their own schedules"
ON schedules
FOR ALL
USING (auth.uid() = user_id);
```

## 📁 Project Structure

```
/src
  /components  - Reusable UI components
  /pages       - Main application pages
  /hooks       - Custom React hooks
  /styles      - CSS files
  /utils       - Helper functions
```

## 📸 Screenshots

<p align="center">
  <img src="https://via.placeholder.com/800x450.png?text=Dashboard+Screenshot" alt="Dashboard" width="400" />
  <img src="https://via.placeholder.com/800x450.png?text=Task+Management" alt="Task Management" width="400" />
</p>
<p align="center">
  <img src="https://via.placeholder.com/800x450.png?text=Schedule+View" alt="Schedule View" width="400" />
  <img src="https://via.placeholder.com/800x450.png?text=Progress+Tracking" alt="Progress Tracking" width="400" />
</p>

## 📝 License

MIT

## 🔄 Contributing & Repository

To contribute to this project or push your changes to the repository:

1. Initialize Git in your local project (if not already done):
   ```bash
   git init
   ```

2. Add all files to Git staging:
   ```bash
   git add .
   ```

3. Commit your changes:
   ```bash
   git commit -m "Initial commit" 
   ```

4. Link to the remote repository:
   ```bash
   git remote add origin https://github.com/LuckyYaduvanshi5/Study_Planner.git
   ```

5. Push your changes:
   ```bash
   git push -u origin main
   ```

   If your default branch is named "master" instead of "main", use:
   ```bash
   git push -u origin master
   ```

6. For subsequent pushes, you can simply use:
   ```bash
   git push
   ```

## 👏 Acknowledgments

- [Supabase](https://supabase.io) for the backend infrastructure
- [React Bootstrap](https://react-bootstrap.github.io/) for the UI components
- [Chart.js](https://www.chartjs.org/) for data visualization
- [Tailwind CSS](https://tailwindcss.com/) for styling
