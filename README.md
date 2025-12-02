# XavierAI Development Guidelines

Welcome to the XavierAI Organization Development Guidelines. This comprehensive guide outlines the best practices, standards, and workflows that all developers should follow when contributing to XavierAI projects.

## Table of Contents

1. [Getting Started](#getting-started)
2. [Repository Structure](#repository-structure)
3. [Git Workflow](#git-workflow)
4. [Branch Management](#branch-management)
5. [Commit Standards](#commit-standards)
6. [Pull Request Process](#pull-request-process)
7. [Code Review Guidelines](#code-review-guidelines)
8. [Issue Management](#issue-management)
9. [Documentation Standards](#documentation-standards)
10. [Security Guidelines](#security-guidelines)
11. [CI/CD Integration](#cicd-integration)
12. [Release Management](#release-management)
13. [Tools and Resources](#tools-and-resources)

## Getting Started

### Prerequisites
- Git installed on your local machine
- GitHub account with access to XavierAI organization
- Preferred IDE/editor with Git integration
- Node.js, Python, or other language-specific tools as required by the project

### Initial Setup
1. **Clone Repository**
   ```bash
   git clone https://github.com/xavieraiorg/[repository-name].git
   cd [repository-name]
   ```

2. **Configure Git (First-time setup)**
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@company.com"
   git config --global init.defaultBranch main
   ```

3. **Set up SSH keys** (Recommended for security)
   ```bash
   ssh-keygen -t ed25519 -C "your.email@company.com"
   # Add the public key to your GitHub account
   ```

## Repository Structure

All XavierAI repositories should follow this standard structure:

```
project-root/
├── .github/                    # GitHub-specific files
│   ├── workflows/             # GitHub Actions
│   ├── ISSUE_TEMPLATE/        # Issue templates
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── CODEOWNERS            # Code ownership
├── docs/                      # Documentation
├── src/                       # Source code
├── tests/                     # Test files
├── scripts/                   # Build/deployment scripts
├── .env.example              # Environment variables template
├── .gitignore               # Git ignore rules
├── README.md                # Project overview
├── CONTRIBUTING.md          # Contribution guidelines
├── LICENSE                  # License file
└── package.json/requirements.txt  # Dependencies
```

## Git Workflow

### Gitflow Workflow
We use a modified Gitflow workflow with the following branches:

- **`main`**: Production-ready code
- **`develop`**: Integration branch for features
- **`feature/*`**: New features and enhancements
- **`hotfix/*`**: Critical bug fixes for production
- **`release/*`**: Release preparation branches

### Daily Workflow
1. **Start your day**: Pull latest changes
   ```bash
   git checkout develop
   git pull origin develop
   ```

2. **Create feature branch**: 
   ```bash
   git checkout -b feature/JIRA-123-user-authentication
   ```

3. **Make changes and commit regularly**
   ```bash
   git add .
   git commit -m "feat: implement user login validation"
   ```

4. **Push and create PR**
   ```bash
   git push origin feature/JIRA-123-user-authentication
   # Create Pull Request via GitHub UI
   ```

## Branch Management

### Branch Naming Convention
- **Feature branches**: `feature/TICKET-ID-short-description`
- **Bug fix branches**: `bugfix/TICKET-ID-short-description`
- **Hotfix branches**: `hotfix/TICKET-ID-short-description`
- **Release branches**: `release/v1.2.0`

### Branch Protection Rules
- `main` and `develop` branches are protected
- Require pull request reviews before merging
- Require status checks to pass
- Enforce up-to-date branches before merging
- No direct pushes to protected branches

### Branch Cleanup
- Delete feature branches after merging
- Keep `main`, `develop`, and active `release/*` branches
- Regular cleanup of stale branches (monthly)

## Commit Standards

### Conventional Commits
We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Commit Types
- **`feat`**: New features
- **`fix`**: Bug fixes
- **`docs`**: Documentation changes
- **`style`**: Code style changes (formatting, semicolons, etc.)
- **`refactor`**: Code refactoring
- **`test`**: Adding or updating tests
- **`chore`**: Build process, dependency updates
- **`perf`**: Performance improvements
- **`ci`**: CI/CD pipeline changes

### Examples
```bash
feat(auth): add OAuth2 integration with Google
fix(api): resolve null pointer exception in user service
docs: update API documentation for v2 endpoints
style: format code according to ESLint rules
refactor(utils): extract common validation functions
test(auth): add unit tests for login functionality
chore: update dependencies to latest versions
```

### Commit Best Practices
- Write clear, concise commit messages
- Use imperative mood ("add feature" not "added feature")
- Limit first line to 50 characters
- Provide detailed description in body if needed
- Reference issue numbers when applicable
- Make atomic commits (one logical change per commit)

## Pull Request Process

### Creating Pull Requests
1. **Use the PR Template**: Fill out all sections in the PR template
2. **Clear Title**: Use descriptive titles following conventional commit format
3. **Detailed Description**: Explain what changes were made and why
4. **Link Issues**: Connect PR to related issues using keywords
5. **Add Labels**: Use appropriate labels for categorization
6. **Request Reviews**: Assign relevant reviewers

### PR Template Sections
- **Description**: What changes were made?
- **Type of Change**: Bug fix, new feature, breaking change, etc.
- **Testing**: How was this tested?
- **Screenshots**: Visual changes (if applicable)
- **Checklist**: Self-review items

### PR Requirements
- ✅ All tests pass
- ✅ Code follows style guidelines
- ✅ Self-review completed
- ✅ Documentation updated (if needed)
- ✅ No merge conflicts
- ✅ At least one reviewer approval

## Code Review Guidelines

### For Authors
- **Self-review**: Review your own code before requesting review
- **Small PRs**: Keep PRs focused and reasonably sized
- **Context**: Provide sufficient context and explanation
- **Tests**: Include appropriate tests
- **Documentation**: Update docs when needed

### For Reviewers
- **Timely Reviews**: Review within 24-48 hours
- **Constructive Feedback**: Be specific and helpful
- **Focus Areas**: 
  - Logic and functionality
  - Code quality and readability
  - Security vulnerabilities
  - Performance implications
  - Test coverage

### Review Checklist
- [ ] Code follows project conventions
- [ ] Logic is sound and efficient
- [ ] Security considerations addressed
- [ ] Tests are comprehensive
- [ ] Documentation is updated
- [ ] No sensitive data exposed

## Issue Management

### Issue Types
- **🐛 Bug**: Something isn't working
- **✨ Enhancement**: New feature or improvement
- **📚 Documentation**: Documentation improvement
- **🔧 Task**: General task or chore
- **❓ Question**: General question

### Issue Templates
Use GitHub issue templates for consistency:
- Bug Report Template
- Feature Request Template
- Documentation Request Template

### Issue Workflow
1. **Create**: Use appropriate template
2. **Label**: Add relevant labels
3. **Assign**: Assign to appropriate developer
4. **Track**: Update status regularly
5. **Close**: Close when resolved with reference to PR

### Labels
- **Priority**: `priority/high`, `priority/medium`, `priority/low`
- **Type**: `type/bug`, `type/feature`, `type/docs`
- **Status**: `status/in-progress`, `status/blocked`, `status/review`
- **Component**: `component/api`, `component/ui`, `component/auth`

## Documentation Standards

### Code Documentation
- **Comments**: Explain complex logic, not obvious code
- **JSDoc/Docstrings**: Document all public functions/methods
- **README**: Each repository must have a comprehensive README
- **API Documentation**: Auto-generated from code comments

### README Structure
```markdown
# Project Name
Brief description

## Features
## Installation
## Usage
## API Reference
## Contributing
## License
```

### Documentation Best Practices
- Keep documentation up-to-date with code changes
- Use clear, concise language
- Include examples and use cases
- Provide troubleshooting guides
- Document configuration options

## Security Guidelines

### Secrets Management
- **Never commit**: API keys, passwords, tokens
- **Use Environment Variables**: For configuration
- **GitHub Secrets**: For CI/CD secrets
- **Rotate Regularly**: Update secrets periodically

### Security Checks
- **Dependency Scanning**: Regular security audits
- **Code Scanning**: Static analysis for vulnerabilities
- **Access Control**: Principle of least privilege
- **Two-Factor Authentication**: Required for all team members

### Security Checklist
- [ ] No hardcoded secrets
- [ ] Input validation implemented
- [ ] Authentication/authorization in place
- [ ] Dependencies are up-to-date
- [ ] Security headers configured

## CI/CD Integration

### GitHub Actions
All repositories should include:
- **CI Pipeline**: Automated testing on every PR
- **Security Scanning**: Dependency and code scanning
- **Code Quality**: Linting and formatting checks
- **Deployment**: Automated deployment to staging/production

### Required Workflows
```yaml
# .github/workflows/ci.yml
name: Continuous Integration
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
      - run: npm ci
      - run: npm test
      - run: npm run lint
```

### Quality Gates
- All tests must pass
- Code coverage > 80%
- No linting errors
- Security scans pass
- Performance benchmarks met

## Release Management

### Versioning
We follow [Semantic Versioning](https://semver.org/):
- **MAJOR.MINOR.PATCH** (e.g., 1.2.3)
- **MAJOR**: Breaking changes
- **MINOR**: New features (backward compatible)
- **PATCH**: Bug fixes (backward compatible)

### Release Process
1. **Create Release Branch**: `release/v1.2.0`
2. **Update Version**: Update version numbers
3. **Update Changelog**: Document changes
4. **Test**: Thorough testing of release candidate
5. **Merge**: Merge to main and tag release
6. **Deploy**: Automated deployment
7. **Announce**: Notify team and stakeholders

### Changelog Format
```markdown
# Changelog

## [1.2.0] - 2023-12-01
### Added
- User authentication system
- API rate limiting

### Changed
- Improved error handling
- Updated dependencies

### Fixed
- Memory leak in data processor
- Login redirect issue
```

## Tools and Resources

### Required Tools
- **Git**: Version control
- **GitHub CLI**: `gh` for CLI operations
- **IDE Extensions**: GitLens, GitHub Pull Requests
- **Linters**: ESLint, Pylint, etc.
- **Formatters**: Prettier, Black, etc.

### Recommended Tools
- **GitKraken/SourceTree**: Git GUI clients
- **Postman**: API testing
- **Docker**: Containerization
- **Jest/Pytest**: Testing frameworks

### Useful Commands
```bash
# Check out PR locally
gh pr checkout [PR-number]

# Create PR from command line
gh pr create --title "feat: new feature" --body "Description"

# View repository issues
gh issue list

# Create and switch to new branch
git checkout -b feature/new-feature

# Interactive rebase for cleaning commits
git rebase -i HEAD~3

# Check repository statistics
git shortlog -sn
```

## Best Practices Summary

### DO ✅
- Write clear commit messages
- Create focused pull requests
- Review code thoroughly
- Keep branches up-to-date
- Document your code
- Test your changes
- Follow naming conventions
- Use issue templates

### DON'T ❌
- Commit directly to main/develop
- Push sensitive information
- Create huge pull requests
- Skip code reviews
- Ignore CI failures
- Forget to update documentation
- Use force push on shared branches
- Leave stale branches

## Getting Help

### Resources
- **Internal Documentation**: [Company Wiki/Confluence]
- **GitHub Docs**: [docs.github.com](https://docs.github.com)
- **Git Documentation**: [git-scm.com](https://git-scm.com)
- **Team Chat**: #dev-help channel

### Contacts
- **DevOps Team**: @devops
- **Security Team**: @security
- **Tech Leads**: @tech-leads

---

## Contributing to This Guide

This guideline is a living document. To suggest improvements:
1. Create an issue with the `documentation` label
2. Submit a pull request with proposed changes
3. Discuss in team meetings

**Last Updated**: December 2024  
**Version**: 1.0.0
