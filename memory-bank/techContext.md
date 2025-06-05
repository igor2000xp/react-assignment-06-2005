# Technical Context

## Technology Stack

### Core Technologies
- **React**: Modern functional components with hooks
- **TypeScript**: Strict type checking, interfaces over types
- **Gatsby**: Static site generation, GraphQL data layer
- **Tailwind CSS**: Utility-first CSS framework, mobile-first approach

### Development Environment
- **Node.js**: Required for Gatsby development
- **Git**: Version control (GitHub repository)
- **Cursor**: AI-powered code editor with project rules
- **Zsh**: User's shell environment (macOS)

### Build Tools & Configuration
- **Gatsby CLI**: Project scaffolding and development server
- **TypeScript Compiler**: Type checking and compilation
- **Gatsby Build**: Static site generation and optimization
- **Tailwind CSS**: Utility generation and purging

## Technical Constraints

### TypeScript Requirements
- No `any` or `unknown` types unless absolutely necessary
- Prefer interfaces over types
- Avoid type assertions (`as`, `!`)
- Use proper type definitions from the codebase

### Code Architecture Constraints
- Functional programming patterns only (no classes)
- Named exports for components and utilities
- Descriptive variable names with auxiliary verbs
- Modular file structure: component, queries, helpers, types

### Gatsby-Specific Constraints
- Use `useStaticQuery` for build-time data fetching
- Create pages in `src/pages/` or programmatically via `gatsby-node.js`
- Use Gatsby's Link component for internal navigation
- Optimize images with Gatsby plugins
- Environment variables through `gatsby-config.js`

### Styling Constraints
- Tailwind CSS only for styling
- Mobile-first responsive design approach
- Utility-based classes
- Minimal custom CSS

## Development Setup

### Project Structure (Planned)
```
src/
  components/          # Reusable React components
  pages/              # Gatsby pages
  hooks/              # Custom React hooks
  utils/              # Utility functions
  types/              # TypeScript type definitions
  styles/             # Tailwind and custom styles
gatsby-config.js      # Gatsby configuration
gatsby-node.js        # Build-time page generation
gatsby-browser.js     # Browser APIs
gatsby-ssr.js         # Server-side rendering APIs
```

### Configuration Files
- `package.json`: Dependencies and scripts
- `tsconfig.json`: TypeScript configuration
- `tailwind.config.js`: Tailwind customization
- `gatsby-config.js`: Gatsby plugins and metadata

## Dependencies (To Be Installed)

### Core Dependencies
- `gatsby`: Static site generator
- `react`: UI library
- `react-dom`: DOM bindings for React
- `typescript`: Type checking

### Gatsby Plugins
- `gatsby-plugin-typescript`: TypeScript support
- `gatsby-plugin-postcss`: PostCSS processing
- `gatsby-plugin-image`: Image optimization
- `gatsby-transformer-sharp`: Image processing
- `gatsby-plugin-sharp`: Image processing

### Development Dependencies
- `@types/react`: React type definitions
- `@types/react-dom`: React DOM type definitions
- `tailwindcss`: CSS framework
- `postcss`: CSS processing
- `autoprefixer`: CSS vendor prefixes

## Performance Considerations
- Gatsby's static generation for optimal loading
- Image optimization through Gatsby plugins
- Code splitting and lazy loading
- CSS purging for minimal bundle size
- GraphQL query optimization

## Browser Support
- Modern browsers with ES6+ support
- Responsive design for mobile and desktop
- Progressive enhancement principles

## Current State
- Empty project with cursor rules configured
- Git repository initialized
- Ready for Gatsby project setup 