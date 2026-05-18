# TANESCO-SmartPay

A smart payment solution for TANESCO (Tanzania Electric Supply Company) customers to manage electricity bills and payments efficiently.

## 📋 Table of Contents

- [About](#about)
- [Features](#features)
- [Getting Started](#getting-started)
- [Installation](#installation)
- [Usage](#usage)
- [API Reference](#api-reference)
- [Architecture](#architecture)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

## About

TANESCO-SmartPay is an innovative platform designed to streamline electricity bill payment and management for TANESCO customers in Tanzania. It provides a user-friendly interface for checking bills, making payments, and tracking consumption patterns.

### Vision
To make electricity bill payment seamless, transparent, and accessible to all TANESCO customers across Tanzania.

## Features

✨ **Core Features:**
- 💡 Real-time electricity bill tracking
- 💳 Multiple payment methods support
- 📊 Consumption analytics and insights
- 📱 Mobile-friendly interface
- 🔐 Secure payment gateway integration
- 📧 Bill reminders and notifications
- 💾 Payment history and receipts
- 👤 Customer account management
- 🔍 Bill dispute resolution support
- 📈 Usage predictions and recommendations

## Getting Started

### Prerequisites

- Node.js v14+ or Python 3.8+
- Git
- npm or pip package manager
- TANESCO API credentials (for integration)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Mr-mtweve/TANESCO-SmartPay.git
   cd TANESCO-SmartPay
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   pip install -r requirements.txt
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your credentials
   ```

4. **Start the application**
   ```bash
   npm start
   # or
   python app.py
   ```

## Usage

### Basic Operations

#### Check Your Bill
```bash
curl -X GET https://api.tanesco-smartpay.com/bills/your-account-id \
  -H "Authorization: Bearer YOUR_TOKEN"
```

#### Make a Payment
```bash
curl -X POST https://api.tanesco-smartpay.com/payments \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "account_id": "123456",
    "amount": 50000,
    "payment_method": "mobile_money"
  }'
```

#### View Payment History
```bash
curl -X GET https://api.tanesco-smartpay.com/payments/history \
  -H "Authorization: Bearer YOUR_TOKEN"
```

## API Reference

### Authentication
All endpoints require Bearer token authentication.

**Endpoint:** `/auth/login`
```json
POST /auth/login
{
  "email": "user@example.com",
  "password": "password"
}
```

### Bills Endpoints

- `GET /bills` - List all bills
- `GET /bills/:id` - Get bill details
- `GET /bills/:id/history` - Get bill history
- `POST /bills/:id/dispute` - File a bill dispute

### Payments Endpoints

- `POST /payments` - Create payment
- `GET /payments/history` - Payment history
- `GET /payments/:id` - Get payment details
- `POST /payments/:id/receipt` - Download receipt

### Account Endpoints

- `GET /account` - Get account details
- `PUT /account` - Update account information
- `POST /account/password-change` - Change password

## Architecture

```
├── Frontend (React/Vue)
│   ├── Dashboard
│   ├── Bills Management
│   ├── Payments
│   └── Account Settings
├── Backend (Node.js/Python)
│   ├── API Gateway
│   ├── Auth Service
│   ├── Bills Service
│   ├── Payments Service
│   └── Notifications Service
├── Database
│   └── PostgreSQL/MongoDB
└── External Services
    ├── TANESCO API
    ├── Payment Gateway
    └── Email/SMS Service
```

## Roadmap

### Phase 1 (Current)
- ✅ User authentication
- ✅ Bill viewing
- ✅ Basic payments

### Phase 2 (Q3 2026)
- 📅 Mobile app launch (iOS & Android)
- 📅 Advanced analytics dashboard
- 📅 Auto-pay feature
- 📅 Bill prediction using AI

### Phase 3 (Q4 2026)
- 📅 Solar integration support
- 📅 Multi-user account management
- 📅 Business/Commercial accounts
- 📅 Blockchain-based receipts

## Contributing

We welcome contributions from the community! Here's how to get involved:

### Getting Started with Development

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make your changes** and commit with clear messages
   ```bash
   git commit -m "feat: add new feature description"
   ```

4. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

5. **Open a Pull Request** with a detailed description

### Development Guidelines

- Write clean, well-documented code
- Follow the existing code style
- Add tests for new features
- Update documentation as needed
- Keep commits small and focused

### Reporting Issues

Found a bug? Please open an issue with:
- Clear description of the problem
- Steps to reproduce
- Expected vs actual behavior
- Screenshots (if applicable)
- Your environment details

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Support

- 📧 Email: support@tanesco-smartpay.com
- 💬 GitHub Issues: [Report a bug](https://github.com/Mr-mtweve/TANESCO-SmartPay/issues)
- 📖 Documentation: [Full docs](https://docs.tanesco-smartpay.com)

---

**Built with ❤️ for TANESCO customers**

Last Updated: May 18, 2026
