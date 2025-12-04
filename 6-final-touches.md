# Frontend Styling & App Configuration

## 1. Update src/main.tsx

- Import and call `initializeApiClient` with environment variables (VITE_API_ENDPOINT, VITE_AWS_REGION, VITE_USER_POOL_ID, VITE_USER_POOL_CLIENT_ID)
- Render App in StrictMode

## 2. Update src/index.css with Gaming Theme

- Import tailwindcss and tw-animate-css
- Define CSS variables using oklch color space:
  - Primary: Purple theme (oklch 0.55-0.7, 0.25, 270)
  - Accent: Teal theme (oklch 0.65-0.7, 0.2, 160)
  - Background: Dark slate tones
- Dark mode variables with vibrant primary/accent colors
- Add utility classes:
  - `.text-gradient`: Primary to accent gradient text
  - `.glass`: Frosted glass effect with backdrop blur
  - `.glow`: Purple glow shadow effect

## 3. Create tailwind.config.js

- darkMode: "class"
- Extend theme with primary/secondary colors using CSS variables

## 4. Consistent Design Language

- Background: `bg-linear-to-b from-slate-900 to-slate-800`
- Cards/panels: `bg-slate-800/50 backdrop-blur-md border border-white/10 rounded-2xl`
- Inputs: `bg-slate-800/50 border-white/10 text-white placeholder:text-slate-500 focus:border-primary/50`
- Buttons: Primary uses theme color, outline buttons use `bg-slate-800/50 border-white/10`
- Text: White for headings, slate-300/400 for secondary text
- Shadows: `shadow-lg shadow-primary/20` for accent elements

## 5. Create src/App.tsx

State management:

- isAuthenticated boolean
- currentUser object (id, username, avatar)
- isLoading boolean
- pendingConfirmation for email verification flow

Auth check on mount:

- Check localStorage for auth_token and user_id
- Fetch user profile if authenticated
- Clear invalid sessions on error

Login handler:

- Support both login and signup flows
- Store token in localStorage
- Fetch user profile after auth

Logout handler:

- Clear localStorage (auth_token, user_id)
- Reset state

Routing:

- Unauthenticated: /auth route only, redirect others
- Authenticated: All routes wrapped in Layout
- Routes: /ai-assistant, /profile

Wrap in ThemeProvider (dark default) and BrowserRouter, add Toaster
