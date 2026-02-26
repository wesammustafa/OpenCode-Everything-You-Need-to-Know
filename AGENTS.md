# OpenCode Agent Guidelines

This document helps OpenCode understand your project's structure, conventions, and requirements.

## Project Overview

**Project Type**: [Describe your project type, e.g., React/TypeScript web application]
**Purpose**: [Brief description of what the project does]
**Key Technologies**: [List main technologies and frameworks]

## Code Conventions

### File Structure
```
src/
├── components/     # React components
├── pages/         # Page components
├── utils/         # Utility functions
├── hooks/         # Custom React hooks
├── types/         # TypeScript type definitions
└── styles/        # CSS/SCSS files
```

### Naming Conventions
- **Files**: kebab-case (e.g., `user-profile.tsx`)
- **Components**: PascalCase (e.g., `UserProfile`)
- **Functions**: camelCase (e.g., `formatUserName`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_RETRY_COUNT`)
- **Types**: PascalCase with `Type` suffix (e.g., `UserProfileType`)

### Code Style
- **Indentation**: 2 spaces
- **Semicolons**: Yes
- **Quotes**: Single quotes for strings
- **Line length**: 100 characters max
- **Trailing commas**: Yes in objects and arrays

## Development Guidelines

### Testing
- Write unit tests for all utility functions
- Use Jest and React Testing Library
- Test files should be next to source files (e.g., `component.tsx` and `component.test.tsx`)
- Aim for 80%+ test coverage

### Error Handling
- Use try/catch for async operations
- Log errors to console in development
- Show user-friendly error messages in production
- Validate all external inputs

### Security
- Never commit secrets or API keys
- Validate and sanitize all user inputs
- Use environment variables for configuration
- Implement proper authentication and authorization

### Performance
- Use React.memo() for expensive components
- Implement code splitting for large bundles
- Optimize images and assets
- Monitor bundle size

## Project-Specific Rules

### Do's
- Use TypeScript strict mode
- Follow the existing component patterns
- Add comments for complex logic
- Update documentation when changing APIs
- Run tests before committing

### Don'ts
- Don't use `any` type in TypeScript
- Don't commit console.log statements
- Don't modify multiple concerns in one commit
- Don't ignore TypeScript/ESLint warnings
- Don't add dependencies without team approval

## Common Patterns

### API Calls
```typescript
// Use this pattern for API calls
async function fetchUser(id: string): Promise<User> {
  try {
    const response = await api.get(`/users/${id}`);
    return response.data;
  } catch (error) {
    console.error('Failed to fetch user:', error);
    throw new Error('User not found');
  }
}
```

### Component Structure
```typescript
// Use this component structure
interface UserProfileProps {
  userId: string;
  onUpdate?: () => void;
}

export function UserProfile({ userId, onUpdate }: UserProfileProps) {
  const [user, setUser] = useState<User | null>(null);
  
  useEffect(() => {
    loadUser();
  }, [userId]);
  
  async function loadUser() {
    const data = await fetchUser(userId);
    setUser(data);
  }
  
  if (!user) return <LoadingSpinner />;
  
  return (
    <div className="user-profile">
      <h2>{user.name}</h2>
      {/* ... */}
    </div>
  );
}
```

## Tool Configuration

### Formatters
- **Prettier**: Use project prettier config
- **ESLint**: Follow Airbnb style guide with custom rules
- **TypeScript**: Strict mode enabled

### Build Tools
- **Bundler**: Vite
- **Package Manager**: npm
- **CI/CD**: GitHub Actions

## Getting Started

1. **Install dependencies**: `npm install`
2. **Start development server**: `npm run dev`
3. **Run tests**: `npm test`
4. **Build for production**: `npm run build`
5. **Check code quality**: `npm run lint`

## Helpful Commands

```bash
# Format code
npm run format

# Type check
npm run type-check

# Run all checks
npm run check

# Update dependencies
npm run update-deps
```

## Contact & Support

- **Team**: [Your team name]
- **Repository**: [GitHub repo URL]
- **Documentation**: [Docs URL]
- **Slack**: [Slack channel]

---

*This document is automatically generated and should be updated as the project evolves.*