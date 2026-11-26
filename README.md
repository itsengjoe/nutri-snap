# NutriSnap Frontend

This is the frontend for NutriSnap, built with React, TypeScript, and Tailwind CSS.

## Features

- Responsive design with mobile support
- Dark/light mode toggle
- Full RTL (Right-to-Left) support for Arabic
- Authentication flow (login, signup, verification)
- Photo analysis with AI-powered nutrition insights
- Personalized meal planning
- AI chat assistant for nutrition guidance
- Premium subscription management
- Admin dashboard for user and transaction management

## Tech Stack

- **Framework**: React 18 with TypeScript
- **Routing**: React Router v6
- **State Management**: TanStack Query v5
- **UI Components**: shadcn/ui with Tailwind CSS
- **Styling**: Tailwind CSS
- **Forms**: React Hook Form with Zod validation
- **Internationalization**: react-i18next (planned)
- **Build Tool**: Vite

## Project Structure

```
src/
├── components/          # Reusable UI components
│   ├── ui/              # shadcn/ui components
│   └── Navigation.tsx   # Main navigation component
├── hooks/               # Custom React hooks
├── lib/                 # Utilities and context providers
├── pages/              # Route pages
│   ├── admin/           # Admin pages
│   ├── auth/            # Authentication pages
│   └── ...              # Main application pages
├── App.tsx              # Root component with routing
├── main.tsx             # Entry point
└── globals.css          # Global styles
```

## Setup

1. Install dependencies:
   ```bash
   npm install
   ```

2. Start the development server:
   ```bash
   npm run dev
   ```

3. Build for production:
   ```bash
   npm run build
   ```

## Environment Variables

Create a `.env` file with the following variables:

```
VITE_API_URL=http://localhost:8000
```

## Development

- All new components should be created in the `src/components/` directory
- Pages should be created in the `src/pages/` directory
- Use Tailwind CSS for styling
- Follow the existing component structure and naming conventions
- Use TypeScript for type safety

## Routing

Routes are defined in `src/App.tsx`. Add new routes by importing the page component and adding a new `Route` element.

## UI Components

This project uses shadcn/ui components which are located in `src/components/ui/`. To add new components, follow the shadcn/ui documentation.