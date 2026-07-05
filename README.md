# Recoursion

**Bachelor Thesis Project - University of Piraeus, Department of Informatics**

Interactive web application for discovering and recommending the most suitable online courses with a focus on user preferences.

## Overview

Recoursion aggregates online courses from multiple platforms (Udemy, Coursera, edX, Pluralsight, YouTube) and provides personalized, explainable recommendations based on user preferences and interactions. The recommendation system is deterministic and transparent, explaining the reasoning behind each suggestion.

## Features

- **Course Discovery** - Browse 200 courses from 5 platforms covering 121 technologies
- **Search & Filtering** - Search by keyword, filter by platform, difficulty, duration, and technology
- **Personalized Recommendations** - Explainable recommendations based on preferences and behavior
- **Multi-Criteria Ratings** - Rate courses on quality, clarity, depth, difficulty, and overall impression
- **Favorites Management** - Save courses with real-time badge updates
- **User Profiles** - Set preferences for technologies, difficulty, depth, and duration
- **Responsive Design** - Full mobile support with hamburger navigation
- **Dark Mode** - Toggle between light and dark themes

## Technology Stack

| Category | Technology |
|----------|------------|
| Frontend | React 18 + Vite |
| Language | JavaScript (ES6+) |
| Styling | CSS Modules |
| State Management | React Context API + Custom Hooks |
| Authentication | Firebase Authentication |
| Database | Cloud Firestore |
| Routing | React Router v6 |

## Getting Started

### Prerequisites

- Node.js 18+
- npm 9+
- Firebase account

### Installation

```bash
git clone https://github.com/Dtsiakas/recoursion.git
cd recoursion

npm install

npm run dev
```

### Firebase Configuration

1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
2. Enable Authentication (Email/Password)
3. Create a Firestore database
4. Add your Firebase credentials to `src/services/firebase.js`

## Project Structure

```
src/
├── components/     # Reusable UI components (Button, Card, Input, etc.)
├── pages/          # Page components (Discover, CourseDetails, Profile, etc.)
├── hooks/          # Custom React hooks (useAuth, useCourses)
├── context/        # React Context providers (Auth, Favorites)
├── services/       # Firebase service layer
├── utils/          # Recommendation engine
├── data/           # Course dataset (200 courses)
└── styles/         # Global CSS variables and styles
```

## Recommendation Engine

The recommendation system uses a deterministic additive scoring algorithm with a maximum total of 100 points:

```
Total Score = Technology Match (0-40)
            + Difficulty Match (0-20)
            + Depth Match      (0-15)
            + Duration Match   (0-15)
            + Interaction Boost (0-10)
```

- **Technology Match** (max 40): Ratio of preferred technologies covered by the course
- **Difficulty Match** (max 20): Ordinal distance between preferred and course difficulty
- **Depth Match** (max 15): Ordinal distance between preferred and course depth
- **Duration Match** (max 15): Ordinal distance between preferred and course duration
- **Interaction Boost** (max 10): Similarity to favorited and positively rated courses

Each recommendation includes a human-readable explanation of why it was suggested.

## Author

**Dimitris Tsiakas** - University of Piraeus, Department of Informatics

Supervisor: Konstantina Chrysafiadi

## License

This project was developed as a bachelor thesis and is intended for educational purposes.
