# Contributing to TANESCO-SmartPay

Thank you for your interest in contributing to TANESCO-SmartPay! We welcome contributions from developers, designers, and payment system experts. This document provides guidelines and instructions for contributing.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Making Changes](#making-changes)
- [Security Considerations](#security-considerations)
- [Committing Your Changes](#committing-your-changes)
- [Submitting a Pull Request](#submitting-a-pull-request)
- [Code Style Guidelines](#code-style-guidelines)
- [Testing](#testing)
- [Database Migrations](#database-migrations)
- [API Documentation](#api-documentation)
- [Reporting Security Issues](#reporting-security-issues)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Enhancements](#suggesting-enhancements)

## Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inclusive community. Please read and adhere to our code of conduct:

- **Be Respectful**: Treat all contributors with respect and kindness
- **Be Inclusive**: Welcome people of all backgrounds and experiences
- **Be Professional**: Keep discussions constructive and focused on the project
- **Be Responsible**: Handle sensitive payment data with care
- **Be Collaborative**: Work together to build a secure, reliable system

### Unacceptable Behavior

- Harassment, bullying, or discrimination
- Offensive language or personal attacks
- Sharing private or payment information
- Unauthorized security testing
- Spam or self-promotion

## Getting Started

### Prerequisites

- Git installed and configured
- Node.js v14+ or Python 3.8+
- PostgreSQL or MongoDB installed
- Docker (recommended)
- A GitHub account
- Basic knowledge of payment systems

### Fork and Clone

1. **Fork the repository** by clicking the "Fork" button on GitHub
2. **Clone your fork**
   ```bash
   git clone https://github.com/YOUR-USERNAME/TANESCO-SmartPay.git
   cd TANESCO-SmartPay
   ```

3. **Add upstream remote**
   ```bash
   git remote add upstream https://github.com/Mr-mtweve/TANESCO-SmartPay.git
   ```

4. **Install dependencies**
   ```bash
   npm install
   # or
   pip install -r requirements.txt
   ```

5. **Setup environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your development credentials
   ```

## Development Workflow

### Create a Feature Branch

```bash
# Update your local repository
git fetch upstream
git checkout upstream/main

# Create a new branch
git checkout -b feature/your-feature-name
# or for bug fixes
git checkout -b bugfix/issue-description
# or for payment-related features
git checkout -b feature/payment/your-feature-name
```

### Branch Naming Convention

- `feature/feature-name` - New features
- `feature/payment/feature-name` - Payment-related features
- `bugfix/issue-description` - Bug fixes
- `docs/description` - Documentation updates
- `test/test-description` - Test additions
- `security/issue-description` - Security patches

## Making Changes

### 1. Code Structure

Keep your changes:
- Small and focused on a single issue
- Well-organized and easy to understand
- Free of hardcoded credentials
- Free of test/dummy payment data

### 2. Write Clear Code

```javascript
// ✅ Good: Clear variable names and logic
async function processPayment(paymentData) {
  try {
    const validatedData = validatePaymentInput(paymentData);
    const response = await paymentGateway.process(validatedData);
    return { success: true, transactionId: response.id };
  } catch (error) {
    logger.error('Payment processing failed', { error });
    throw new PaymentError(error.message);
  }
}

// ❌ Bad: Unclear naming and missing error handling
function proc(x) {
  return payGW.proc(x);
}
```

## Security Considerations

### 🔒 Critical Security Rules

**DO:**
- ✅ Use environment variables for all sensitive data
- ✅ Validate and sanitize all user inputs
- ✅ Use HTTPS for all API endpoints
- ✅ Implement rate limiting
- ✅ Follow PCI DSS compliance guidelines
- ✅ Hash and salt all passwords
- ✅ Use secure payment gateway APIs
- ✅ Log security events (without sensitive data)

**DON'T:**
- ❌ Commit API keys, secrets, or credentials
- ❌ Store payment card details in your code
- ❌ Log sensitive payment information
- ❌ Use unencrypted communications
- ❌ Store plain text passwords
- ❌ Expose system errors to users

### Security Review Checklist

Before submitting a PR, ensure:
- [ ] No credentials/secrets in code
- [ ] All inputs are validated
- [ ] No SQL injection vulnerabilities
- [ ] No XSS vulnerabilities
- [ ] Proper authentication checks
- [ ] Authorization properly enforced
- [ ] Error messages don't leak information

## Committing Your Changes

### Commit Message Format

We follow the Conventional Commits specification:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat` - A new feature
- `fix` - A bug fix
- `docs` - Documentation changes
- `style` - Code style changes
- `refactor` - Code refactoring
- `test` - Adding or updating tests
- `security` - Security patches
- `chore` - Maintenance tasks

### Scopes

- `auth` - Authentication
- `payment` - Payment processing
- `bills` - Bill management
- `user` - User management
- `api` - API endpoints
- `db` - Database
- `docs` - Documentation

### Examples

```bash
git commit -m "feat(payment): add M-Pesa integration"
git commit -m "security(auth): fix authentication bypass vulnerability"
git commit -m "fix(bills): resolve bill calculation error"
git commit -m "docs(api): update payment endpoints documentation"
git commit -m "test(payment): add M-Pesa integration tests"
```

## Submitting a Pull Request

### Before Submitting

1. **Update your branch with latest upstream changes**
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Run tests locally**
   ```bash
   npm test
   # or
   python -m pytest
   ```

3. **Run security checks**
   ```bash
   npm run security-audit
   # or
   pip install safety && safety check
   ```

4. **Check code style**
   ```bash
   npm run lint
   ```

### Creating a Pull Request

1. **Push your branch to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

2. **Open a Pull Request** on GitHub with:
   - Clear title describing the change
   - Detailed description of what was changed and why
   - Reference to any related issues (e.g., "Fixes #123")
   - Security impact assessment (if applicable)
   - Testing steps and screenshots

### Pull Request Template

```markdown
## Description
Brief description of the changes

## Type of Change
- [ ] New feature
- [ ] Bug fix
- [ ] Security patch
- [ ] Documentation update
- [ ] Other

## Related Issues
Fixes #123

## Security Impact
- [ ] No security impact
- [ ] Low security impact
- [ ] High security impact (describe)

## How to Test
Steps to verify the changes

## Security Checklist
- [ ] No credentials/secrets in code
- [ ] Inputs are validated
- [ ] No SQL injection vulnerabilities
- [ ] No XSS vulnerabilities
- [ ] Proper authentication checks

## Testing
- [ ] Unit tests added/updated
- [ ] Integration tests added/updated
- [ ] All tests passing
- [ ] Code coverage maintained (>80%)

## Screenshots (if applicable)
Add screenshots here
```

## Code Style Guidelines

### General Rules

- Use consistent indentation (2 or 4 spaces)
- Keep lines under 100 characters
- Use meaningful variable and function names
- Add comments for complex logic
- Remove console.log and debug code before submitting
- Follow framework-specific conventions

### Example

```javascript
// ✅ Good style
async function validatePaymentMethod(method, accountId) {
  const validMethods = ['mobile_money', 'card', 'bank_transfer'];
  
  if (!validMethods.includes(method)) {
    throw new ValidationError('Invalid payment method');
  }
  
  const account = await Account.findById(accountId);
  return account && account.paymentMethods.includes(method);
}

// ❌ Bad style
async function vPM(m,a){
  if(!['mobile_money','card','bank_transfer'].includes(m))throw new Error('Invalid');
  return(await Account.findById(a))?.paymentMethods.includes(m);
}
```

## Testing

### Writing Tests

- Write tests for all new features
- Write tests for all bug fixes
- Update tests when changing existing code
- Aim for >80% code coverage
- Test both success and failure cases
- Include security-related tests

### Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm test -- --watch

# Run tests with coverage
npm test -- --coverage

# Run security tests
npm run test:security
```

## Database Migrations

### Creating a Migration

```bash
# Generate migration file
npm run migrate:create --name=add_new_field

# Or manually create in migrations/ folder
# naming: YYYY-MM-DD_HHmmss_description.sql
```

### Migration Template

```sql
-- Up
ALTER TABLE payments ADD COLUMN reference_number VARCHAR(50) UNIQUE;
CREATE INDEX idx_payments_reference ON payments(reference_number);

-- Down
DROP INDEX idx_payments_reference;
ALTER TABLE payments DROP COLUMN reference_number;
```

### Before Committing

```bash
# Test migration up
npm run migrate:up

# Test migration down
npm run migrate:down

# Verify data integrity
npm run test:database
```

## API Documentation

### Updating API Docs

When adding or modifying API endpoints:

1. **Update OpenAPI/Swagger file** (`docs/api.yml`)
2. **Add JSDoc comments** in code
3. **Update README.md** with examples
4. **Add example requests and responses**

### API Documentation Format

```javascript
/**
 * Process a payment
 * @route POST /api/v1/payments
 * @param {Object} paymentData - Payment details
 * @param {string} paymentData.accountId - TANESCO account ID
 * @param {number} paymentData.amount - Payment amount (TZS)
 * @param {string} paymentData.method - Payment method
 * @returns {Object} Payment confirmation
 * @returns {string} transactionId - Unique transaction ID
 * @returns {string} status - Payment status (pending/success/failed)
 * @throws {ValidationError} Invalid payment data
 * @throws {PaymentError} Payment processing failed
 * @security BearerAuth
 * @example
 * // Request
 * POST /api/v1/payments
 * {
 *   "accountId": "ABC123456",
 *   "amount": 50000,
 *   "method": "mobile_money"
 * }
 * // Response
 * {
 *   "transactionId": "TXN-2026-001",
 *   "status": "success"
 * }
 */
```

## Reporting Security Issues

### 🔒 DO NOT Open Public Issues for Security Vulnerabilities

Instead:

1. **Email security team** at security@tanesco-smartpay.com
2. **Include detailed information**:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if available)

3. **Allow time for response** before public disclosure
4. **Do not exploit the vulnerability** beyond what's necessary to verify it

## Reporting Bugs

### Before Reporting

- Check if the bug has already been reported
- Try to reproduce it consistently
- Gather relevant information

### Bug Report Template

**Title:** Brief description of the bug

**Environment:**
- OS: [e.g., Windows 10, Linux]
- Node/Python version: [e.g., v14.0.0]
- Database: [e.g., PostgreSQL 12]
- Version: [e.g., 1.0.0]

**Description:**
Clear description of what went wrong

**Steps to Reproduce:**
1. Step 1
2. Step 2
3. Step 3

**Expected Behavior:**
What should happen

**Actual Behavior:**
What actually happened

**Logs/Error Messages:**
Any relevant error logs (remove sensitive data)

## Suggesting Enhancements

### Enhancement Proposal Template

**Title:** Brief description of the enhancement

**Problem:**
What problem does this solve?

**Proposed Solution:**
How should this be implemented?

**Payment Gateway Impact:**
Will this affect payment processing?

**Alternatives:**
Other solutions you've considered

**Additional Context:**
Any additional information

## Getting Help

- 💬 Open a discussion for questions
- 📧 Email: support@tanesco-smartpay.com
- 📖 Check the documentation
- 🔍 Search existing issues and discussions

## Review Process

1. Automated tests must pass
2. Security checks must pass
3. Code review by maintainers
4. Address feedback and make changes
5. Final approval and merge

## Recognition

Contributors will be recognized in:
- README.md contributors section
- Release notes
- GitHub contributors page
- CONTRIBUTORS.md file

---

**Thank you for contributing to TANESCO-SmartPay!** 🚀

Together we're building a better payment system for Tanzania!

For security issues, please email: security@tanesco-smartpay.com
