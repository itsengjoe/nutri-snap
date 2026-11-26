# NutriSnap

A personal nutrition assistant application that helps users track nutrition, plan meals, and achieve health goals with AI-powered insights.

## Project Architecture

### Frontend
- **Framework**: React with TypeScript
- **Build Tool**: Vite (port 5000 in development)
- **Styling**: Tailwind CSS with shadcn/ui components
- **Routing**: React Router DOM
- **State Management**: React Context (AuthContext)

### Backend
- **Framework**: FastAPI (Python)
- **Database**: PostgreSQL with SQLAlchemy (async with asyncpg)
- **Authentication**: JWT tokens with python-jose
- **Password Hashing**: bcrypt via passlib

### Key Features
- User authentication (signup, login, email verification)
- AI-powered meal planning (OpenAI integration)
- Photo analysis for nutrition tracking
- AI chat assistant
- Premium subscription management
- Admin panel for user management with ban reason/duration and email notifications
- English-only interface (simplified from bilingual)
- Terms of Service with 10-day account deletion recovery

## Development Setup

### Running the Application
- Frontend runs on port 5000 with Vite dev server
- Backend API runs on port 8000 with uvicorn
- Frontend proxies `/api/*` requests to the backend

### Environment Variables
- `DATABASE_URL`: PostgreSQL connection string (auto-configured by Replit)
- `SECRET_KEY`: JWT secret key for authentication

### Workflows
- **Frontend**: `npm run dev` - Runs Vite dev server on port 5000
- **Backend API**: Runs FastAPI with uvicorn on port 8000

## Deployment
- Production uses autoscale deployment
- Backend serves static frontend files from `dist/` directory
- Build command: `npm run build && pip install -r backend/requirements.txt`

## Recent Changes (January 2026)
- **Subscription Plans with Hard Limits**:
  - Free Plan: 3 chat messages/day, 5 meal plans/month, 1 photo analysis/day
  - Premium Plan (120 EGP/month): 10 chat messages/day, 3 meal plans/day, 3 photo analyses/day
  - Hard limits enforced at API level (not just UI warnings)
  - Daily counters reset automatically at midnight, monthly counters reset on 1st of month
- **Admin Panel Improvements**:
  - Premium duration selection (1, 3, 6, or 12 months) when granting premium
  - Unban dialog with optional reason field
  - Unban email notification sent to users when unbanned
- **Mobile UX Fix**: Toast messages now dismiss after 5 seconds (was too long)
- **AI Chat UI Improvements**:
  - Redesigned desktop layout with better spacing
  - Sidebar moved to right side for better visual hierarchy
  - Added scroll-to-bottom button on mobile
  - Added clear chat button with confirmation warning
  - Chat messages auto-delete after 30 days
- **Premium Payment Flow Updated**:
  - Changed to InstaPay only (removed bank transfer)
  - New account email: mohamed.barakat8480@instapay
  - Users must enter their InstaPay email before submitting
  - Added InstaPay logo
- **Settings Simplified**: Removed target protein input (auto-calculated from user profile)
- **Daily Data Reset**: Recent meals now show only today's meals, daily quotas reset each day
- **Schedule Feature**: Added monthly calendar view showing daily calories, protein, and meals
  - New /monthly-summary API endpoint for aggregated nutrition data
  - Color-coded indicators (green for on-target, yellow for close, blue for meals)
- **Enhanced Nutrition Calculator System** (NO AI):
  - User inputs: gender, age, height, weight, activity level (sedentary/light/moderate/heavy), training experience (beginner/intermediate/advanced), goal (fat_loss/maintenance/muscle_gain)
  - Step 1: BMR via Mifflin-St Jeor (male: +5, female: -161)
  - Step 2: TDEE = BMR × activity multiplier (1.2/1.375/1.55/1.725)
  - Step 3: Goal adjustment (fat loss: 85%/80%, maintenance: 100%, muscle gain: 110%/115%) with safety caps (±700/-500 kcal)
  - Step 4: Protein = weight × factor from table (1.6-2.4 g/kg based on goal and experience), max 3g/kg
  - Step 5: Minimum calories (male: 1500, female: 1200)
  - Step 6: Stored as daily_calories and daily_protein in user profile
  - Recalculates only when weight, activity_level, goal, training_experience, gender, age, or height changes
  - Daily budget (EGP) saved separately for meal planning
- **Image Handling**: Fixed static file serving for uploads directory
  - Added /uploads mount point in FastAPI
  - Updated frontend URLs for profile pictures and transaction screenshots
- **Dashboard Mobile UI**: Improved bottom navigation with Schedule link
  - Responsive stats cards with better text sizing and spacing
  - Mobile-optimized header layout
- Added redirect logic for logged-in users on Home, Login, and Signup pages
- Updated UI color scheme to green primary color
- Added classy animations and utility classes in globals.css
- Added download button for transaction screenshots in admin panel
- Fixed audit log error by handling null details field
- Removed Arabic language - now English-only interface
- Added ban dialog in AdminUsers with reason and duration inputs
- Added send_ban_notification email method with styled HTML template
- Added transaction photo download endpoint for admins
- Fixed duplicate methods in EmailService
- Added Security section in Settings with Change Password and Logout All Devices features
- Implemented token version system for proper logout-all functionality
- Fixed forgot password flow with multi-step process
- Added formatNumber utility for rounding number displays

## Previous Changes
- Added transparent background logo
- Updated copyright years to 2026 across all pages
- Configured for Replit environment
- Set up PostgreSQL database connection with asyncpg
- Configured CORS for development
- Added Vite proxy for API calls
- Set up static file serving for production
- Updated Login/Signup pages to display API error messages
- AuthContext now returns error messages from backend
- Settings allows gym_years = 0

## Contact Support
- Email: corex.games.service@gmail.com
- Discord: https://discord.gg/tCnTRxUyUq
