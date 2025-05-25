# Calendar Management Frontend

React TypeScript application for multi-tenant calendar management with Google Calendar integration.

## ✨ Features

- **Google OAuth Authentication** - Secure login with Google accounts
- **Multi-tenant Support** - Isolated data per organization
- **Calendar Integration** - Full Google Calendar API integration
- **Event Management** - Create, view, and manage calendar events
- **Responsive Design** - Works on desktop and mobile devices
- **TypeScript** - Full type safety and developer experience

## 🛠️ Tech Stack

- **React 18** - Modern React with hooks
- **TypeScript** - Type-safe development
- **React Router** - Client-side routing
- **Axios** - HTTP client with interceptors
- **Custom Hooks** - Reusable business logic
- **CSS Modules** - Scoped styling

## 📁 Project Structure

```
src/
├── components/          # React components
│   ├── Login.tsx       # Authentication component
│   ├── Calendar.tsx    # Main calendar interface
│   └── EventForm.tsx   # Event creation form
├── hooks/              # Custom React hooks
│   ├── useAuth.ts      # Authentication logic
│   └── useCalendar.ts  # Calendar operations
├── services/           # API services
│   ├── authService.ts  # Authentication API
│   └── calendarService.ts # Calendar API
├── types/              # TypeScript definitions
│   └── index.ts        # Shared types
├── utils/              # Utility functions
│   └── dateUtils.ts    # Date formatting helpers
├── App.tsx             # Main application
└── index.tsx           # Application entry point
```

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ 
- npm or yarn
- Backend API running (see backend README)

### Installation

1. **Clone and navigate**
```bash
git clone <repository-url>
cd calendar-management/frontend
```

2. **Install dependencies**
```bash
npm install
```

3. **Environment setup**
```bash
cp .env.example .env
```

Configure your `.env` file:
```env
REACT_APP_API_URL=http://localhost:3001
REACT_APP_GOOGLE_CLIENT_ID=your-google-client-id.googleusercontent.com
```

4. **Start development server**
```bash
npm start
```

Application will open at `http://localhost:3000`

## 📦 Dependencies

### Production Dependencies
```json
{
  "react": "^18.2.0",
  "react-dom": "^18.2.0",
  "react-router-dom": "^6.8.0",
  "axios": "^1.3.0",
  "typescript": "^4.9.0"
}
```

### Development Dependencies
```json
{
  "@types/react": "^18.0.0",
  "@types/react-dom": "^18.0.0",
  "react-scripts": "5.0.1"
}
```

## 🔧 Configuration

### Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `REACT_APP_API_URL` | Backend API URL | `http://localhost:3001` |
| `REACT_APP_GOOGLE_CLIENT_ID` | Google OAuth Client ID | `xxx.googleusercontent.com` |

### Google OAuth Setup

1. Create Google Cloud Project
2. Enable Google Calendar API
3. Create OAuth 2.0 credentials
4. Add authorized origins:
   - `http://localhost:3000` (development)
   - Your production domain

## 🏗️ Architecture

### Authentication Flow
```
1. User clicks "Login with Google"
2. Redirect to Google OAuth
3. Google redirects back with auth code
4. Backend exchanges code for tokens
5. Frontend receives JWT token
6. Token stored in localStorage
7. Axios interceptor adds token to requests
```

### State Management
- **React Hooks** - Local component state
- **Custom Hooks** - Shared business logic
- **Context API** - Global state (if needed)
- **localStorage** - Token persistence

### API Integration
- **Axios Interceptors** - Automatic token injection
- **Error Handling** - Automatic logout on 401
- **Request/Response** - Centralized API logic

## 🎨 Components

### Login Component
```typescript
// Simple authentication interface
- Google OAuth button
- Loading states
- Error handling
```

### Calendar Component
```typescript
// Main calendar interface
- Event list display
- Create event button
- Event filtering
- Responsive layout
```

### EventForm Component
```typescript
// Event creation/editing
- Form validation
- Date/time pickers
- Submit handling
- Cancel functionality
```

## 🔗 Custom Hooks

### useAuth Hook
```typescript
const { user, loading, login, logout } = useAuth();
```

**Features:**
- Authentication state management
- Google OAuth integration
- Token handling
- User profile loading
- Automatic logout on errors

### useCalendar Hook
```typescript
const { events, loading, createEvent, loadEvents } = useCalendar();
```

**Features:**
- Event loading from Google Calendar
- Event creation
- Loading states
- Error handling
- Automatic refresh

## 🛡️ Security

### Token Management
- JWT tokens stored in localStorage
- Automatic token injection via Axios
- Token expiration handling
- Secure logout functionality

### API Security
- All requests authenticated
- Automatic 401 handling
- CORS configuration
- Request validation

### Data Protection
- Multi-tenant isolation
- No sensitive data in localStorage
- Secure OAuth flow
- XSS protection

## 📱 Responsive Design

### Breakpoints
- **Mobile**: < 768px
- **Tablet**: 768px - 1024px  
- **Desktop**: > 1024px

### Mobile Features
- Touch-friendly interface
- Responsive navigation
- Optimized forms
- Swipe gestures (future)

## 🧪 Testing

### Available Scripts
```bash
# Run tests
npm test

# Run tests with coverage
npm test -- --coverage

# Run tests in watch mode
npm test -- --watch
```

### Testing Strategy
- **Unit Tests** - Components and hooks
- **Integration Tests** - API interactions
- **E2E Tests** - User workflows (future)

### Example Test
```typescript
// src/hooks/__tests__/useAuth.test.ts
import { renderHook } from '@testing-library/react';
import { useAuth } from '../useAuth';

test('should handle login flow', () => {
  const { result } = renderHook(() => useAuth());
  // Test implementation
});
```

## 🚀 Build & Deployment

### Development Build
```bash
npm start
```

### Production Build
```bash
npm run build
```

### Deployment Options

#### Static Hosting (Recommended)
- **Netlify** - Automatic deployments from Git
- **Vercel** - Zero-configuration deployment
- **AWS S3 + CloudFront** - Scalable hosting

#### Traditional Hosting
- **Nginx** - Serve built files
- **Apache** - Static file serving
- **Docker** - Containerized deployment

### Environment-Specific Builds
```bash
# Development
npm run build:dev

# Staging  
npm run build:staging

# Production
npm run build:prod
```

## 🔍 Debugging

### Development Tools
- **React Developer Tools** - Component inspection
- **Redux DevTools** - State debugging (if using Redux)
- **Network Tab** - API request monitoring
- **Console Logging** - Runtime debugging

### Common Issues

#### Authentication Problems
```typescript
// Check token in localStorage
localStorage.getItem('token')

// Verify API URL
console.log(process.env.REACT_APP_API_URL)

// Check network requests
// Open Network tab in DevTools
```

#### Calendar Integration Issues
```typescript
// Verify Google Client ID
console.log(process.env.REACT_APP_GOOGLE_CLIENT_ID)

// Check CORS settings in backend
// Ensure Google OAuth redirect URLs are correct
```

## 📈 Performance

### Optimization Strategies
- **Code Splitting** - Route-based splitting
- **Lazy Loading** - Component lazy loading
- **Memoization** - React.memo and useMemo
- **Bundle Analysis** - webpack-bundle-analyzer

### Bundle Analysis
```bash
npm install -g webpack-bundle-analyzer
npm run build
npx webpack-bundle-analyzer build/static/js/*.js
```

### Performance Metrics
- **First Contentful Paint** - < 1.5s
- **Largest Contentful Paint** - < 2.5s
- **First Input Delay** - < 100ms
- **Cumulative Layout Shift** - < 0.1

## 🛠️ Development

### Code Standards
- **ESLint** - Code linting
- **Prettier** - Code formatting
- **TypeScript** - Type checking
- **Husky** - Git hooks (optional)

### Git Workflow
```bash
# Create feature branch
git checkout -b feature/calendar-filters

# Make changes and commit
git add .
git commit -m "Add calendar event filters"

# Push and create PR
git push origin feature/calendar-filters
```

### VS Code Extensions
- ES7+ React/Redux/React-Native snippets
- TypeScript Importer
- Auto Rename Tag
- Bracket Pair Colorizer
- GitLens

## 🤝 Contributing

### Getting Started
1. Fork the repository
2. Create feature branch
3. Make changes
4. Add tests
5. Update documentation
6. Submit pull request

### Code Review Process
- Automated tests must pass
- Code review by team member
- Documentation updates
- Performance impact assessment

## 📚 Learning Resources

### React & TypeScript
- [React Documentation](https://reactjs.org/docs)
- [TypeScript Handbook](https://www.typescriptlang.org/docs)
- [React + TypeScript Cheatsheet](https://github.com/typescript-cheatsheets/react)

### Google Calendar API
- [Google Calendar API Documentation](https://developers.google.com/calendar)
- [OAuth 2.0 for Web Applications](https://developers.google.com/identity/protocols/oauth2/web-server)

## 🐛 Troubleshooting

### Common Errors

#### "Network Error"
```bash
# Check if backend is running
curl http://localhost:3001/health

# Verify CORS configuration
# Check browser console for CORS errors
```

#### "Invalid Google Client ID"
```bash
# Verify environment variable
echo $REACT_APP_GOOGLE_CLIENT_ID

# Check Google Cloud Console settings
# Ensure authorized origins are correct
```

#### "Token Expired"
```bash
# Clear localStorage
localStorage.clear()

# Refresh the page
# Login again
```

### Getting Help
- Check browser console for errors
- Review network requests in DevTools
- Consult Google Calendar API documentation
- Create GitHub issue with detailed description

## 📄 License

MIT License - see LICENSE file for details

---

**Happy coding! 🚀**

For backend setup instructions, see the [Backend README](../backend/README.md)
