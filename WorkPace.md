# Inner Compass: Complete Development Breakdown

## 🔐 AUTHENTICATION SYSTEM

### Authentication Pages Required:
1. **Login Page**
   - Email/Password fields
   - Google OAuth button
   - "Forgot Password" link
   - "Sign Up" redirect

2. **Registration Page**
   - Email, Password, Confirm Password
   - User profile setup (name, age, preferences)
   - Terms & Privacy acceptance
   - Google OAuth option

3. **Password Reset Page**
   - Email input for reset link
   - New password form (from email link)

4. **Profile Setup Page**
   - Initial mental health preferences
   - Privacy settings configuration
   - Emergency contact setup

### Authentication Features:
- ✅ Email/Password authentication
- ✅ Google OAuth integration
- ✅ Email verification (automatic)
- ❌ OTP not mentioned in docs (Email verification used instead)
- ✅ Password reset via email
- ✅ Multi-factor authentication (optional)
- ✅ Session management with auto-refresh

---

## 📱 FRONTEND PAGES & COMPONENTS

### Main Application Pages (7 Core Pages):

#### 1. **Dashboard Page** - **REACT** Required
**Components:**
- Mood visualization charts (Chart.js integration)
- Quick mood check-in widget
- Recent journal entries preview
- Personalized AI recommendations panel
- Weekly/monthly insights display
- Quick action buttons (emergency contacts)

#### 2. **Mood Tracker Page** - **REACT** Required
**Components:**
- Interactive mood selector (1-10 scale slider)
- Emotion categorization buttons (happy, anxious, stressed, etc.)
- Daily/weekly/monthly trend charts
- Mood pattern heat map
- Export functionality for healthcare providers
- Historical mood data table

#### 3. **Journal Page** - **REACT** Required
**Components:**
- Rich text editor (ReactQuill)
- Auto-save functionality
- Entry list with search/filter
- Sentiment analysis results display
- Privacy controls per entry
- Export options

#### 4. **Resource Map Page** - **REACT** Required
**Components:**
- Google Maps integration
- Filter controls (therapists, support groups, crisis centers)
- Resource details sidebar
- Save/bookmark functionality
- Direct contact integration
- Location permission handling

#### 5. **Community Forum Page** - **REACT** Required
**Components:**
- Anonymous posting interface
- Topic-based discussion threads
- Peer support groups
- Crisis support threads
- Moderation and reporting system
- User reputation system

#### 6. **Settings/Profile Page** - Minimal React
**Components:**
- Profile information editing
- Privacy controls configuration
- Data export options
- Account deletion
- Notification preferences
- Theme selection (light/dark mode)

#### 7. **Analytics/Insights Page** - **REACT** Required
**Components:**
- Predictive analytics charts
- Wellness goal tracking
- Achievement badges
- Progress visualization
- Milestone celebrations
- Personal insights reports

---

## 🔧 FRONTEND FUNCTIONALITY BREAKDOWN

### **REACT** Heavy Components:

#### Dashboard Functionality:
- Real-time mood data visualization
- Interactive charts and graphs
- Dynamic recommendation updates
- Live notification system
- WebSocket connections for real-time insights

#### Mood Tracking Functionality:
- Interactive slider components
- Dynamic form validation
- Real-time chart updates
- Data export generation
- Trend analysis calculations

#### Journal Functionality:
- Rich text editing with formatting
- Auto-save with conflict resolution
- Sentiment analysis integration
- Search and filtering
- Privacy toggle per entry

#### Resource Map Functionality:
- Google Maps API integration
- Real-time location services
- Dynamic filtering system
- Interactive markers and popups
- Route planning integration

#### Community Functionality:
- Real-time messaging system
- Anonymous user management
- Content moderation interface
- Voting and reaction systems
- Thread management

### Minimal React Components:
- Settings forms
- Profile editing
- Static information pages
- Terms and privacy pages
- Help and documentation

---

## 🗂️ TABS & NAVIGATION STRUCTURE

### Main Navigation (7 Tabs):
1. **Dashboard** - Home overview
2. **Mood** - Mood tracking and trends
3. **Journal** - Personal journaling
4. **Resources** - Map and local resources
5. **Community** - Forum and support
6. **Insights** - Analytics and progress
7. **Settings** - Profile and preferences

### Sub-navigation within tabs:
- **Mood**: Today | Week | Month | Trends | Export
- **Journal**: Write | Entries | Search | Analytics
- **Resources**: Map | Saved | Emergency | Directory
- **Community**: Recent | Groups | Support | My Posts
- **Insights**: Overview | Goals | Predictions | Reports

---

## 🤖 MACHINE LEARNING INTEGRATION

### ML Features & APIs:

#### 1. Sentiment Analysis
- **Service**: OpenAI GPT-3.5/4 API
- **Function**: Analyze journal entries for emotional sentiment
- **Accuracy**: 85-90%
- **Processing Time**: 2-3 seconds per entry

#### 2. Stress Detection System
- **Services**: OpenAI + IBM Watson Tone Analyzer
- **Function**: Detect stress indicators in text
- **Risk Levels**: Low/Medium/High assessment
- **Accuracy**: 82%

#### 3. Crisis Detection
- **Service**: OpenAI API with specialized prompts
- **Function**: Identify crisis language in journals/posts
- **Response Time**: <5 minutes for alerts
- **False Positive Rate**: <5%

#### 4. Recommendation Engine
- **Service**: OpenAI API with custom prompting
- **Function**: Generate personalized coping strategies
- **Features**: Activity suggestions, resource recommendations
- **Update Frequency**: Real-time based on new data

#### 5. Predictive Analytics
- **Service**: Custom algorithms + OpenAI
- **Function**: Mood pattern predictions, stress forecasting
- **Data Sources**: Historical mood data, journal sentiment
- **Accuracy**: 78% for mood predictions

---

## 🔧 BACKEND ARCHITECTURE & PORTS

### Backend Services (Firebase Functions - Serverless):

#### Core API Endpoints:

##### Authentication Service
```
POST /api/auth/register - User registration
POST /api/auth/login - User login
POST /api/auth/logout - User logout
POST /api/auth/reset-password - Password reset
GET /api/auth/verify-email - Email verification
```

##### User Management Service
```
GET /api/users/profile - Get user profile
PUT /api/users/profile - Update user profile
PUT /api/users/preferences - Update preferences
DELETE /api/users/account - Delete account
GET /api/users/data-export - Export user data
```

##### Mood Tracking Service
```
POST /api/moods - Log new mood entry
GET /api/moods/entries - Get mood entries
GET /api/moods/trends - Get mood trends
GET /api/moods/insights - Get AI-generated insights
GET /api/moods/analytics - Get detailed analytics
DELETE /api/moods/{id} - Delete mood entry
```

##### Journal Service
```
POST /api/journal/entry - Save journal entry
GET /api/journal/entries - Retrieve entries
PUT /api/journal/{id} - Update entry
DELETE /api/journal/{id} - Delete entry
POST /api/journal/analyze - Trigger sentiment analysis
GET /api/journal/search - Search entries
```

##### ML Analysis Service
```
POST /api/ml/sentiment - Analyze sentiment
POST /api/ml/stress - Detect stress levels
POST /api/ml/crisis - Crisis detection
POST /api/ml/recommendations - Generate recommendations
GET /api/ml/insights - Get AI insights
```

##### Resource Service
```
GET /api/resources/nearby - Find nearby resources
POST /api/resources/save - Save resource
DELETE /api/resources/{id} - Remove saved resource
GET /api/resources/emergency - Get crisis resources
GET /api/resources/directory - Get resource directory
```

##### Community Service
```
POST /api/community/posts - Create post
GET /api/community/posts - Get posts
PUT /api/community/{id} - Update post
DELETE /api/community/{id} - Delete post
POST /api/community/report - Report content
GET /api/community/groups - Get support groups
```

### Database Collections (Firestore):

#### User Data Structure:
```
users/{userId}/
├── profile: { name, email, preferences, privacy_settings }
├── moods/{entryId}: { date, mood_score, emotions, notes, sentiment_analysis }
├── journals/{entryId}: { date, content, analysis_results, privacy_level }
├── resources/{resourceId}: { type, location, contact_info, saved_date }
├── community/{postId}: { content, timestamp, anonymous_id, thread_id }
├── insights/{date}: { daily_summary, recommendations, risk_assessment }
└── goals/{goalId}: { title, target, progress, created_date }
```

---

## 🌐 THIRD-PARTY API INTEGRATIONS

### Required API Keys & Services:

#### 1. Firebase Services
- **Authentication API**: User management
- **Firestore Database**: Data storage
- **Cloud Functions**: Serverless backend
- **Storage**: File uploads
- **Hosting**: Web hosting

#### 2. OpenAI API
- **Model**: GPT-3.5-turbo/GPT-4
- **Usage**: Text analysis, recommendations, crisis detection
- **Rate Limit**: 3,500 requests/minute
- **Estimated Cost**: $200/month for 5,000 users

#### 3. Google Maps Platform
- **Maps JavaScript API**: Interactive maps
- **Places API**: Resource location search
- **Geocoding API**: Address conversion
- **Estimated Cost**: $50/month for moderate usage

#### 4. Additional APIs
- **SendGrid**: Email notifications ($15/month)
- **Twilio**: SMS crisis alerts ($20/month)
- **IBM Watson Tone Analyzer**: Backup sentiment analysis

---

## 📊 DEVELOPMENT EFFORT BREAKDOWN

### **REACT** Intensive Development (6-7 weeks):
- Dashboard with real-time charts and data
- Interactive mood tracking interface
- Rich text journal editor with auto-save
- Google Maps integration with filtering
- Community forum with real-time features
- Analytics and insights visualization

### Minimal React Development (1-2 weeks):
- Authentication pages (forms only)
- Settings and profile pages
- Static content pages
- Basic navigation components

### Backend Development (2-3 weeks):
- Firebase Functions setup
- API endpoint development
- Third-party service integrations
- Database schema implementation
- Security rules configuration

### ML Integration (1 week):
- OpenAI API integration
- Custom prompt engineering
- Response processing logic
- Error handling and fallbacks

---

## 🚀 DEPLOYMENT & HOSTING

### Hosting Strategy:
- **Frontend**: Vercel (automatic GitHub deployments)
- **Backend**: Firebase Functions (auto-scaling)
- **Database**: Firebase Firestore (managed)
- **CDN**: Vercel Edge Network

### Required Ports (Development):
- **Frontend Dev Server**: Port 3000 (React)
- **Backend Dev Server**: Port 5000 (Firebase Functions)
- **Database Emulator**: Port 8080 (Firestore)
- **Auth Emulator**: Port 9099 (Firebase Auth)

### Production (No port management needed):
- All services are serverless/managed
- Automatic HTTPS and scaling
- Global CDN distribution

---

## 💰 ESTIMATED COSTS

### Monthly Operating Costs:
- **Firebase**: ~$50/month (1000 active users)
- **OpenAI API**: ~$200/month (5000 users)
- **Google Maps**: ~$50/month
- **SendGrid**: $15/month
- **Twilio**: $20/month
- **Vercel Hosting**: $20/month
- **Total**: ~$355/month

### Development Costs:
- **Initial Development**: $45,000 (10 weeks, 2 developers)
- **Maintenance**: 5 hours/week ongoing
- **API-driven approach saves 70% vs custom ML development**
