# Personal To-Do List Manager

A modern, colorful web application for personal task management with comprehensive features including categories, calendars, reminders, productivity tracking, and analytics. The project includes 8 interconnected pages with responsive design, local storage-based data persistence, and user authentication.

---

## 📋 Project Overview

This is a complete task management system that combines productivity tools with user-friendly design. The application features:

- **Task Management:** Create, edit, delete, and organize tasks with priorities and categories
- **Productivity Tracking:** Monitor progress, streaks, and completion rates
- **Calendar Integration:** Mini calendar with reminders and due date tracking
- **Analytics Dashboard:** Comprehensive reports and data export capabilities
- **User Authentication:** Secure login/registration system
- **Responsive Design:** Works seamlessly on desktop and mobile devices

The entire application uses browser's `localStorage` for data persistence and `sessionStorage` for user session management.

---

## 📁 File Structure & Description

### 1. **front.html** - Landing Page
**Purpose:** Main entry point and landing page of the application.

**Features:**
- Modern gradient background (cyan to purple)
- Hero section with call-to-action
- Navigation menu with links to Home, Search, and Contact
- Login button for user authentication
- Responsive design with smooth animations

**Key Elements:**
- Logo: "To-Do Manager"
- CTA Button: "Get Started" - redirects to login page
- Navigation bar with internal links
- Footer with copyright information

**Styling:** Gradient background, modern spacing, fade-in animations

---

### 2. **login.html** - Authentication Portal
**Purpose:** User login and registration page with form switching.

**Features:**
- Dual form system: Login and Register modes
- Gradient background (green to purple)
- Form validation for username, email, and password
- Local storage for user credentials
- Session management for logged-in users
- Toggle between Login and Register modes

**Key Functionality:**
- **Registration:** Stores user data in localStorage
- **Login:** Validates credentials and creates a session
- **Session Redirect:** Redirects to appropriate pages after login (dashboard or home)
- `goToLogin()` function for redirecting protected pages

**Data Stored:**
```json
{
  "user": { "username": "...", "email": "...", "password": "..." }
}
```

**Session Variables:**
- `loggedInUser` - Stores current user's username
- `redirectAfterLogin` - Stores target page for post-login redirect

---

### 3. **home.html** - Dashboard Home & Navigation Hub
**Purpose:** Main dashboard showing all available features and navigation cards.

**Features:**
- Grid-based card layout showing 5 main features
- User greeting and logout functionality
- Navigation to all major sections
- Responsive card system with hover effects
- Logo display and user information

**Cards Include:**
1. Dashboard / Home - Overview with totals and progress
2. Task Management - Add, edit, delete, complete tasks
3. Category / Planner - Create and manage categories
4. Calendar, Reminders & Tracker - Calendar view with reminders
5. Report & Analytics - Productivity reports and data export

**Key Functionality:**
- Checks if user is logged in before displaying content
- Logout button to clear session
- Responsive grid layout
- Navigation to all application sections

---

### 4. **dashboard.html** - Main Dashboard & Overview
**Purpose:** Displays task statistics, progress, streaks, and quick task management.

**Features:**
- Real-time statistics (Total, Completed, Pending tasks)
- Today's progress bar with gradient
- Streak counter (days without breaking chain)
- Motivational quotes
- Recent completed tasks journal
- Quick add form for fast task creation
- Navigation buttons to Tasks and Categories

**Key Metrics Displayed:**
- Total Tasks Count
- Completed Tasks Count
- Pending Tasks Count
- Today's Progress (visual bar)
- Current Streak (consecutive days)
- Motivational Quote

**Quick Add Form:**
- Input format: `Task - Priority - Time (HH:MM)`
- Parses input and creates task with specific time

**Data Structure:**
```json
{
  "tasks": [...],
  "categories": [...],
  "journal": [...],
  "streak": { "current": 0, "lastDate": null }
}
```

---

### 5. **tasks.html** - Task Management Interface
**Purpose:** Complete task CRUD (Create, Read, Update, Delete) functionality.

**Features:**
- Add new tasks with title, priority, due date, and category
- Task list with filtering (All, Completed, Pending)
- Task sorting (by Created date, Priority, Due date)
- Edit task details
- Mark tasks as complete/incomplete
- Delete tasks
- Category selector dropdown
- Priority levels (Low, Medium, High)

**Form Fields:**
- Title (required)
- Priority dropdown (Low, Medium, High)
- Due Date & Time (datetime-local)
- Category selector
- Add button

**Filtering & Sorting:**
- Filter by status: All, Completed, Pending
- Sort by: Created date, Priority, Due Date

**Task Object Structure:**
```json
{
  "id": 1234567890,
  "title": "Task Name",
  "desc": "",
  "priority": "High",
  "category": "General",
  "due": "ISO Date String",
  "done": false,
  "created": "ISO Date String"
}
```

---

### 6. **categories.html** - Category Management
**Purpose:** Create, rename, and delete task categories.

**Features:**
- Display all categories with task counts
- Add new category
- Rename existing category
- Delete category
- Open tasks filtered by category
- Minimal, clean interface

**Category Management:**
- Displays each category with count of associated tasks
- Actions: Rename, Delete, Open (filters tasks in tasks.html)
- Prevents deletion of default "General" category
- Form to add new categories

**Default Category:** "General" (cannot be deleted)

---

### 7. **calendar_tracker.html** - Calendar, Reminders & Tracker
**Purpose:** Advanced calendar view, reminders, notes, progress tracking, and reports.

**Features:**
- Mini calendar with current month and navigation
- Reminders system with time management
- Notes section for daily journaling
- Progress bars for task completion
- Report generation page
- Task journal and streak tracking

**Sections:**
1. **Calendar View** - Navigate months, click dates
2. **Reminders** - Set and manage task reminders
3. **Notes** - Daily journal entries
4. **Progress Bars** - Visual task completion
5. **Report Page** - Productivity analytics and reports

**Key Functionality:**
- Current date highlighting
- Month navigation
- Reminder notifications
- Progress tracking visualization
- Task statistics and analytics

---


### 8. **report.html** - Analytics & Report Generation
**Purpose:** Comprehensive analytics dashboard with data export capabilities.

**Features:**
- Real-time statistics dashboard (Total, Completed, Pending, Streak)
- Visual progress bars for completion rates
- Priority breakdown with individual progress indicators
- Interactive task distribution chart
- Most active days analysis (top 10 days by task creation)
- Recent journal entries display (last 20 entries)
- Data export functionality (JSON backup and PDF print)

**Statistics Dashboard:**
- **Total Tasks:** Complete count of all tasks
- **Completed:** Number of finished tasks
- **Pending:** Number of unfinished tasks
- **Current Streak:** Consecutive days with completed tasks

**Progress Overview:**
- **Completion Rate:** Visual progress bar with percentage
- **Priority Breakdown:** Separate bars for High, Medium, Low priority tasks
- **Real-time Updates:** All metrics update dynamically

**Visual Analytics:**
- **Task Distribution Chart:** Bar chart showing Total, Completed, and Pending tasks
- **Interactive Canvas:** Responsive chart that scales with data
- **Color-coded Bars:** Purple for Total, Green for Completed, Red for Pending

**Activity Analysis:**
- **Most Active Days:** Top 10 days sorted by task creation activity
- **Task Counts:** Shows number of tasks created per day
- **Date Formatting:** Human-readable date display

**Journal Integration:**
- **Recent Entries:** Last 20 journal entries in reverse chronological order
- **Timestamp Display:** Full date and time for each entry
- **Content Preview:** Shows journal entry text

**Navigation:**
- Links to Dashboard, Tasks, Calendar, and Home pages
- Consistent styling with other application pages
- Responsive design for mobile and desktop

---

## 🔐 Authentication Flow

```
front.html → login.html
                ↓
            (Register or Login)
                ↓
          home.html (navigation hub)
                ↓
        (Choose section: tasks, dashboard, calendar, categories, report)
```

**Session Management:**
1. User registers → credentials stored in `localStorage`
2. User logs in → `sessionStorage.loggedInUser` is set
3. Protected pages check for `loggedInUser` before rendering
4. Logout clears both `sessionStorage` and `localStorage`

---

## 💾 LocalStorage Data Structure

```json
{
  "user": {
    "username": "string",
    "email": "string",
    "password": "string"
  },
  "todoAppData": {
    "tasks": [
      {
        "id": "number",
        "title": "string",
        "desc": "string",
        "priority": "Low|Medium|High",
        "category": "string",
        "due": "ISO Date String or null",
        "done": "boolean",
        "created": "ISO Date String"
      }
    ],
    "categories": ["string"],
    "journal": [
      {
        "date": "string",
        "entry": "string"
      }
    ],
    "streak": {
      "current": "number",
      "lastDate": "ISO Date String or null"
    }
  },
  "todoReminders": [
    {
      "title": "string",
      "time": "ISO Date String",
      "id": "number"
    }
  ]
}
```

---

## 🎨 Design System

**Color Scheme:**
- Primary Accent: `#6c63ff` (Purple)
- Secondary Accent: `#ff6b6b` (Red for dashboard)
- Background Gradients:
  - Cyan to Purple: `#a0f7f2` to `#b28dff`
  - Light Blue to Purple: `#a0f1ff` to `#d8a9ff`
  - Green to Purple: `#62e6c9` to `#5046e9`
  - Light Blue to Indigo: `#7ad6f0` to `#6256e8`

**Typography:**
- Font Family: Inter, system-ui, Segoe UI, Roboto, Arial
- Fallback: Poppins for some pages

**Layout:**
- Maximum width: 900px to 1100px
- Responsive grid system
- Card-based UI with shadows and hover effects
- Sticky headers for navigation

---

## 🚀 Features Summary

### User Management
- ✅ User Registration
- ✅ User Login with Password Validation
- ✅ Session Management
- ✅ Logout Functionality
- ✅ Auto-redirect for Protected Pages

### Task Management
- ✅ Create Tasks with Priority & Categories
- ✅ Edit Task Details
- ✅ Mark Tasks as Complete
- ✅ Delete Tasks
- ✅ Filter by Status (All, Completed, Pending)
- ✅ Sort by Created Date, Priority, Due Date
- ✅ Quick Add Feature

### Organization
- ✅ Create Custom Categories
- ✅ Rename Categories
- ✅ Delete Categories
- ✅ Filter Tasks by Category
- ✅ Category-based Task Management

### Tracking & Insights
- ✅ Task Statistics (Total, Completed, Pending)
- ✅ Today's Progress Visualization
- ✅ Streak Tracking
- ✅ Completed Task Journal
- ✅ Motivational Quotes
- ✅ Productivity Reports
- ✅ Advanced Analytics Dashboard
- ✅ Priority Breakdown Analysis
- ✅ Activity Tracking by Date
- ✅ Data Export (JSON & PDF)
- ✅ Visual Charts and Progress Bars

### Additional Features
- ✅ Calendar View with Navigation
- ✅ Reminders System
- ✅ Daily Notes/Journal
- ✅ Global Search Functionality
- ✅ Responsive Design
- ✅ Modern UI/UX with Animations

---

## 🔧 Technical Stack

- **Frontend:** HTML5, CSS3, JavaScript
- **Storage:** Browser LocalStorage & SessionStorage
- **Authentication:** Client-side with LocalStorage
- **Responsive Design:** CSS Grid & Flexbox
- **Animations:** CSS Keyframes & Transitions

---

## 📱 Browser Compatibility

- Chrome (Latest)
- Firefox (Latest)
- Safari (Latest)
- Edge (Latest)
- Mobile browsers with localStorage support

---

