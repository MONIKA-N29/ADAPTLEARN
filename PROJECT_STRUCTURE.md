# Student Quiz Evaluation Web Application

## Overview
A comprehensive web application for evaluating student performance through quizzes for Class 10 and Class 12 students.

## Features Implemented

### 1. Multi-language Support
- English, Hindi, and Tamil translations
- Language selector available on all screens
- Translations stored in `/src/data/translations.ts`

### 2. Authentication System
- Signup and Login functionality
- Credentials saved in browser's localStorage
- Context-based auth management in `/src/contexts/AuthContext.tsx`

### 3. Class Selection
- Choose between Class 10 or Class 12
- Each class has 3 subjects: Physics, Chemistry, Biology

### 4. Subject and Topic Selection
- Each subject has 3 topics
- Each topic contains 20 questions
- 10 random questions are selected per quiz

### 5. Quiz System
- Timed quiz (10 minutes)
- Question navigation
- Progress tracking
- Visual indicators for answered/unanswered questions

### 6. Performance Analysis
- Score evaluation (correct/incorrect answers)
- Identifies weak subtopics
- Compares performance with previous attempts
- Shows improvement or decline

### 7. Study Materials
- YouTube video recommendations based on weak areas
- Study material links for each subtopic
- Personalized daily study schedule

### 8. Progress Tracking
- All quiz attempts saved in localStorage
- Performance comparison across multiple attempts
- Historical data retention

## File Structure

### Data Files
- `/src/data/translations.ts` - All language translations
- `/src/data/quizData.ts` - Quiz questions for all subjects and topics

### Utility Files
- `/src/utils/auth.ts` - Authentication logic
- `/src/utils/quizEngine.ts` - Quiz generation, scoring, and analysis

### Context Providers
- `/src/contexts/LanguageContext.tsx` - Language state management
- `/src/contexts/AuthContext.tsx` - Authentication state management

### Components
- `/src/app/components/Auth.tsx` - Login/Signup interface
- `/src/app/components/LanguageSelector.tsx` - Language switcher
- `/src/app/components/ClassSelection.tsx` - Class 10/12 selection
- `/src/app/components/SubjectSelection.tsx` - Subject and topic selection
- `/src/app/components/QuizInterface.tsx` - Quiz taking interface
- `/src/app/components/Results.tsx` - Results and analysis display

### Main App
- `/src/app/App.tsx` - Main application orchestrator

## How It Works

1. **User Registration/Login**
   - User signs up with email and password
   - Credentials stored in localStorage
   - Automatic login on return visits

2. **Class Selection**
   - User selects Class 10 or Class 12
   - Selection saved to user profile

3. **Quiz Selection**
   - Choose subject (Physics/Chemistry/Biology)
   - Choose topic (3 topics per subject)
   - Click "Start Quiz"

4. **Taking the Quiz**
   - 10 random questions from 20 available
   - 10-minute timer
   - Can navigate between questions
   - Visual indicators for answered questions

5. **Results & Analysis**
   - Immediate score display
   - Accuracy percentage
   - Weak subtopic identification
   - Comparison with previous attempts
   - YouTube study material recommendations
   - Personalized study schedule

6. **Retaking Quizzes**
   - Can retake any quiz
   - New random 10 questions each time
   - Performance compared with all previous attempts

## Data Storage

All data is stored in browser's localStorage:
- User credentials: `quiz_app_users`
- Current user: `quiz_app_current_user`
- Quiz attempts: `quiz_attempts_{userEmail}`
- Language preference: `quiz_app_language`

## Question Structure

Each question includes:
- Question text
- 4 multiple choice options
- Correct answer index
- Subtopic classification
- Topic association

Example:
```typescript
{
  id: 'p10_m_1',
  question: 'What is Newton\'s First Law of Motion?',
  options: ['Option A', 'Option B', 'Option C', 'Option D'],
  correctAnswer: 0,
  subtopic: 'Force and Motion',
  topic: 'mechanics'
}
```

## Performance Analysis Algorithm

1. **Weak Area Detection**
   - Groups incorrect answers by subtopic
   - Calculates error rate per subtopic
   - Ranks subtopics by incorrect count

2. **Study Material Matching**
   - Maps subtopics to YouTube resources
   - Provides 2-3 video links per weak area

3. **Schedule Generation**
   - Creates morning/afternoon/evening study plan
   - Prioritizes weakest subtopics
   - Distributes topics across time slots

4. **Performance Comparison**
   - Compares current score with most recent previous attempt
   - Shows improvement percentage
   - Provides motivational feedback

## Technologies Used

- React 18.3.1
- TypeScript
- Tailwind CSS
- Radix UI components
- Lucide React icons
- localStorage for data persistence

## Running the Application

The application is ready to run. Simply:
1. Open the application in your browser
2. Sign up with an email and password
3. Select your class
4. Choose a subject and topic
5. Take the quiz
6. View your results and study recommendations

## Future Enhancements (Not Implemented)

For a production version, consider:
- Backend database (Supabase/Firebase)
- Real authentication system
- More advanced analytics
- Export results as PDF
- Share results with teachers
- Leaderboards
- Adaptive difficulty
- More subjects and topics
