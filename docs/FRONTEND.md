# Frontend Documentation

The StudySmart frontend is a Single Page Application (SPA) built with React and Vite.

## Tech Stack
- **Framework**: React
- **Build Tool**: Vite
- **Styling**: Tailwind CSS
- **UI Components**: Radix UI, Shadcn UI
- **Icons**: Lucide React
- **Authentication**: Clerk
- **HTTP Client**: Axios

## Project Structure
The frontend code is located in the `client` directory.

```
client/
├── public/          # Static assets
├── src/
│   ├── components/  # Reusable UI components
│   ├── App.jsx      # Main application component / Routing
│   ├── main.jsx     # Entry point
│   └── index.css    # Global styles (Tailwind imports)
├── package.json     # Dependencies and scripts
└── vite.config.js   # Vite configuration
```

## Key Dependencies

### Clerk (`@clerk/clerk-react`)
Handles user authentication and session management. The application requires a publishable key configured in the environment variables.

### Shadcn UI & Radix UI
Used for accessible and customizable UI components like Tabs, Buttons, Dialogs, etc.

### Tailwind CSS
Utility-first CSS framework for styling. Configuration is in `tailwind.config.js`.

## Scripts
- `npm run dev`: Starts the development server.
- `npm run build`: Builds the application for production.
- `npm run preview`: Previews the production build.
- `npm run lint`: Runs ESLint.
