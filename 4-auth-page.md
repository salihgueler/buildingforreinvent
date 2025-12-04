Create src/pages/AuthPage.tsx with:

1. Login/Signup toggle form with:

   - Email field (signup only)
   - Username field
   - Password field (min 6 chars)
   - Form validation using react-hook-form + zod

2. UI elements:

   - Centered card layout
   - GameHub logo and branding
   - Toggle between login/signup modes
   - Demo info box showing test accounts

3. On submit:
   - Call onLogin prop with credentials
   - Show success/error toasts
   - Handle confirmation flow for signup

Props: onLogin(email, password, username?, isSignUp?) callback
