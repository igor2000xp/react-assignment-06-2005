# System Patterns

## Architecture Overview
This project follows a modern React/Gatsby architecture with functional programming patterns, emphasizing type safety, component reusability, and performance optimization.

## Core Design Patterns

### Component Architecture
- **Functional Components**: All components use function declarations with hooks
- **Named Exports**: Components and utilities use named exports for better tree-shaking
- **Composition over Inheritance**: Favor component composition and custom hooks
- **Single Responsibility**: Each component has a single, well-defined purpose

### File Organization Pattern
```
ComponentName/
  index.ts           # Export barrel
  ComponentName.tsx  # Main component
  ComponentName.test.tsx  # Tests
  ComponentName.types.ts  # Type definitions
  hooks/            # Component-specific hooks
  utils/            # Component-specific utilities
```

### TypeScript Patterns
- **Interface-First Design**: Define interfaces before implementation
- **Strict Typing**: No `any`, `unknown`, or type assertions
- **Generic Constraints**: Use generics with proper constraints
- **Utility Types**: Leverage TypeScript utility types

### State Management Patterns
- **Local State**: React useState for component-specific state
- **Shared State**: Custom hooks for shared logic
- **Context Pattern**: React Context for cross-component state (when needed)
- **Data Fetching**: Gatsby's GraphQL layer for static data

## Gatsby-Specific Patterns

### Page Creation Pattern
```typescript
// Static pages in src/pages/
export default function PageName() {
  return <PageComponent />
}

// Dynamic pages via gatsby-node.js
exports.createPages = async ({ graphql, actions }) => {
  // Programmatic page creation
}
```

### Data Fetching Pattern
```typescript
// useStaticQuery for components
function Component() {
  const data = useStaticQuery(graphql`
    query ComponentQuery {
      # GraphQL query
    }
  `)
  return <div>{/* Use data */}</div>
}

// Page queries for pages
export const query = graphql`
  query PageQuery {
    # Page-specific data
  }
`
```

### Layout Pattern
```typescript
// Layout wrapper for consistent structure
export function Layout({ children }: LayoutProps) {
  return (
    <div className="min-h-screen">
      <Header />
      <main>{children}</main>
      <Footer />
    </div>
  )
}
```

## Styling Patterns

### Tailwind Component Pattern
```typescript
// Utility-first with semantic classes
function Button({ variant = 'primary', children, ...props }: ButtonProps) {
  const baseClasses = 'px-4 py-2 rounded font-medium transition-colors'
  const variantClasses = {
    primary: 'bg-blue-600 text-white hover:bg-blue-700',
    secondary: 'bg-gray-200 text-gray-900 hover:bg-gray-300'
  }
  
  return (
    <button 
      className={`${baseClasses} ${variantClasses[variant]}`}
      {...props}
    >
      {children}
    </button>
  )
}
```

### Responsive Design Pattern
```typescript
// Mobile-first responsive classes
<div className="
  p-4 
  md:p-6 
  lg:p-8 
  grid 
  grid-cols-1 
  md:grid-cols-2 
  lg:grid-cols-3 
  gap-4 
  md:gap-6
">
```

## Error Handling Patterns

### Error Boundary Pattern
```typescript
// React Error Boundary for component error handling
export function ErrorBoundary({ children }: ErrorBoundaryProps) {
  const [hasError, setHasError] = useState(false)
  
  if (hasError) {
    return <ErrorFallback />
  }
  
  return children
}
```

### Loading State Pattern
```typescript
// Consistent loading state handling
function DataComponent() {
  const [isLoading, setIsLoading] = useState(true)
  const [hasError, setHasError] = useState(false)
  
  if (isLoading) return <LoadingSpinner />
  if (hasError) return <ErrorMessage />
  
  return <DataDisplay />
}
```

## Hook Patterns

### Custom Hook Pattern
```typescript
// Reusable logic in custom hooks
export function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue)
  
  const toggle = useCallback(() => setValue(v => !v), [])
  const setTrue = useCallback(() => setValue(true), [])
  const setFalse = useCallback(() => setValue(false), [])
  
  return { value, toggle, setTrue, setFalse }
}
```

### Data Fetching Hook Pattern
```typescript
// Consistent data fetching pattern
export function useApiData<T>(endpoint: string) {
  const [data, setData] = useState<T | null>(null)
  const [isLoading, setIsLoading] = useState(true)
  const [error, setError] = useState<Error | null>(null)
  
  // Implementation...
  
  return { data, isLoading, error }
}
```

## Performance Patterns

### Code Splitting Pattern
```typescript
// Lazy loading for route-based splitting
const LazyComponent = lazy(() => import('./HeavyComponent'))

function App() {
  return (
    <Suspense fallback={<Loading />}>
      <LazyComponent />
    </Suspense>
  )
}
```

### Memoization Pattern
```typescript
// Strategic memoization for expensive computations
const ExpensiveComponent = memo(function ExpensiveComponent({ data }: Props) {
  const processedData = useMemo(() => 
    heavyComputation(data), 
    [data]
  )
  
  return <div>{processedData}</div>
})
```

## Testing Patterns

### Component Testing Pattern
```typescript
// Jest + React Testing Library
describe('ComponentName', () => {
  it('should render correctly', () => {
    render(<ComponentName {...requiredProps} />)
    expect(screen.getByRole('button')).toBeInTheDocument()
  })
  
  it('should handle user interactions', async () => {
    const handleClick = jest.fn()
    render(<ComponentName onClick={handleClick} />)
    
    await user.click(screen.getByRole('button'))
    expect(handleClick).toHaveBeenCalledOnce()
  })
})
```

## Build and Deployment Patterns

### Gatsby Build Optimization
- Static query optimization
- Image processing pipeline
- CSS purging and minification
- Bundle analysis and optimization

### Environment Configuration
```typescript
// gatsby-config.js environment-based configuration
module.exports = {
  siteMetadata: {
    title: process.env.SITE_TITLE || 'Default Title'
  },
  plugins: [
    // Environment-specific plugins
  ]
}
```

## Current Implementation Status
- Patterns defined and ready for implementation
- No code yet written
- Architecture decisions documented
- Ready to begin development following these patterns 