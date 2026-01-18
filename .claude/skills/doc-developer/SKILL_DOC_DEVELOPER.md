# Developer Documentation Guidelines

## Purpose
Generate technical documentation that helps engineers understand, maintain, and extend the codebase.

## Target Audience
- Software engineers (new team members)
- DevOps engineers
- Technical contributors
- Open source contributors

## Documentation Structure

### 1. Technical Overview
````markdown
# [Project Name] - Technical Documentation

## Architecture Overview
- System architecture diagram (describe components)
- Technology stack
- Design patterns used
- Key architectural decisions

## Tech Stack
- **Language/Framework**: [e.g., Node.js, React, Python]
- **Database**: [e.g., PostgreSQL, MongoDB]
- **Infrastructure**: [e.g., AWS, Docker, Kubernetes]
- **Key Libraries**: [list major dependencies]
````

### 2. Setup & Installation
````markdown
## Development Environment Setup

### Prerequisites
- Node.js >= 18.0.0
- Docker Desktop
- PostgreSQL 15+

### Installation Steps
```bash
# Clone repository
git clone [repo-url]
cd [project-name]

# Install dependencies
npm install

# Setup environment
cp .env.example .env
# Edit .env with your local settings

# Run database migrations
npm run migrate

# Start development server
npm run dev
```

### Configuration
- Environment variables explained
- Database setup
- External service configuration
````

### 3. Codebase Structure
````markdown
## Project Structure
````
src/
├── api/           # REST API endpoints
├── components/    # React components
├── services/      # Business logic layer
├── models/        # Data models
├── utils/         # Utility functions
├── config/        # Configuration files
└── tests/         # Test files



### 4. API Documentation
````markdown
## API Reference

### Authentication
All API requests require JWT token in Authorization header:
````
Authorization: Bearer <token>


### 5. Key Modules & Components
````markdown
## Core Modules

### Authentication Service (`src/services/auth.js`)
Handles user authentication and JWT token management.

**Key Functions:**
- `authenticate(email, password)` - Validates credentials, returns JWT
- `validateToken(token)` - Verifies JWT validity
- `refreshToken(token)` - Generates new token

**Example:**
```javascript
const { authenticate } = require('./services/auth');

const token = await authenticate('user@example.com', 'password');
```

### Data Access Layer (`src/models/`)
Uses Sequelize ORM for database operations.

**Models:**
- User
- Project
- Task

**Relationships:**
- User hasMany Projects
- Project hasMany Tasks
````

### 6. Testing
````markdown
## Testing

### Running Tests
```bash
# Run all tests
npm test

# Run with coverage
npm run test:coverage

# Run specific test file
npm test src/services/auth.test.js
```

### Test Structure
- Unit tests: `*.test.js`
- Integration tests: `*.integration.test.js`
- E2E tests: `cypress/e2e/`

### Writing Tests
Follow AAA pattern (Arrange, Act, Assert):
```javascript
describe('AuthService', () => {
  it('should authenticate valid user', async () => {
    // Arrange
    const email = 'test@example.com';
    const password = 'validPassword';
    
    // Act
    const token = await authenticate(email, password);
    
    // Assert
    expect(token).toBeDefined();
    expect(jwt.verify(token, JWT_SECRET)).toBeTruthy();
  });
});
```
````

### 7. Database Schema
````markdown
## Database Schema

### Users Table
```sql
CREATE TABLE users (
  id UUID PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  name VARCHAR(255) NOT NULL,
  role VARCHAR(50) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);
```

### Migrations
Run migrations:
```bash
npm run migrate
```

Create new migration:
```bash
npm run migrate:create -- add-users-table
```
````

### 8. Deployment
````markdown
## Deployment

### Production Build
```bash
npm run build
```

### Docker Deployment
```bash
docker build -t app-name .
docker run -p 3000:3000 app-name
```

### Environment Variables
- `NODE_ENV`: production|development
- `DATABASE_URL`: PostgreSQL connection string
- `JWT_SECRET`: Secret for JWT signing
- `API_KEY`: External API key
````

### 9. Development Workflows
````markdown
## Development Workflow

### Creating a Feature
```bash
git checkout -b feature/feature-name
# Make changes
git add .
git commit -m "feat: add feature description"
git push origin feature/feature-name
# Create pull request
```

### Code Review Process
1. Run tests locally
2. Run `/code_review` (if available)
3. Create PR with description
4. Address review comments
5. Merge when approved

### Debugging
- Use debugger in VS Code (launch.json provided)
- Check logs: `npm run logs`
- Database queries logged in development mode
````

### 10. Troubleshooting
````markdown
## Common Issues

### Database Connection Failed
**Problem:** Cannot connect to PostgreSQL
**Solution:** 
- Check DATABASE_URL in .env
- Ensure PostgreSQL is running: `docker ps`
- Verify credentials

### Tests Failing
**Problem:** Integration tests timeout
**Solution:**
- Clear test database: `npm run test:db:reset`
- Check test environment variables
````

## Content Guidelines

### What to Include
✅ Architecture diagrams and patterns
✅ Complete setup instructions
✅ API endpoint documentation
✅ Database schema and migrations
✅ Code examples and usage
✅ Testing instructions
✅ Deployment procedures
✅ Troubleshooting guides

### What to Exclude
❌ Business requirements (PM doc)
❌ Product roadmap (PM doc)
❌ User stories (PM doc)
❌ Marketing content
❌ High-level "why" without "how"

## Tone & Style
- **Technical and precise**
- **Code-heavy with examples**
- **Assumes engineering knowledge**
- **Focus on implementation details**
- **Use technical terminology**

## Update Triggers
Update developer documentation when:
- New features are added
- Architecture changes
- New dependencies added
- API changes
- Database schema changes
- Deployment process changes