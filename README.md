# 🏦 Stacks Bank - DeFi Lending & Staking Protocol

A robust decentralized finance (DeFi) protocol built on the Stacks blockchain that enables users to stake STX tokens to earn interest and take collateralized loans against their staked assets.

## 🌟 Features

### 💰 Staking
- **Earn Interest**: Stake STX tokens and earn 5% annual interest
- **Flexible Withdrawals**: Withdraw your stake plus accumulated interest anytime
- **Minimum Stake**: 1 STX minimum to participate
- **Real-time Interest**: Interest accrues continuously based on block height

### 🏦 Lending
- **Collateralized Loans**: Borrow up to 66.67% of your staked collateral value
- **Competitive Rates**: 8% annual interest rate on loans
- **Flexible Repayment**: Make partial or full loan repayments
- **Minimum Loan**: 0.5 STX minimum loan amount

### 🛡️ Risk Management
- **150% Collateralization**: Minimum collateral ratio for loan safety
- **Automated Liquidation**: Under-collateralized positions are automatically liquidated
- **Real-time Monitoring**: Track your collateralization ratio in real-time

## 📋 Contract Overview

### Core Functions

#### Staking Functions
- `stake(amount)` - Stake STX tokens to earn interest
- `withdraw-stake(amount)` - Withdraw staked tokens with interest
- `get-stake(user)` - View user's stake information
- `calculate-stake-interest(user)` - Calculate earned interest

#### Lending Functions
- `take-loan(amount)` - Borrow against staked collateral
- `repay-loan(amount)` - Repay loan (partial or full)
- `get-loan(user)` - View user's loan information
- `get-total-debt(user)` - Calculate total debt including interest

#### Liquidation
- `liquidate(borrower)` - Liquidate under-collateralized positions
- `is-liquidatable(user)` - Check if a position can be liquidated

### Read-Only Functions

- `get-accumulated-interest(user)` - View accumulated interest
- `calculate-loan-interest(user)` - Calculate loan interest owed
- `get-contract-stats()` - View protocol statistics

### Administrative Functions (Owner Only)

- `set-stake-interest-rate(new-rate)` - Adjust staking interest rate
- `set-loan-interest-rate(new-rate)` - Adjust loan interest rate  
- `toggle-contract-pause()` - Pause/unpause contract operations
- `emergency-withdraw(amount)` - Emergency fund withdrawal when paused

## 🔧 Getting Started

### Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) - Stacks smart contract development toolkit
- [Stacks CLI](https://docs.stacks.co/docs/write-smart-contracts/clarinet) - Command line interface

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd stacks-bank
```

2. Check contract syntax:
```bash
clarinet check
```

3. Run tests:
```bash
clarinet test
```

### Deployment

Deploy to different networks using Clarinet:

```bash
# Deploy to devnet
clarinet deploy --devnet

# Deploy to testnet  
clarinet deploy --testnet

# Deploy to mainnet
clarinet deploy --mainnet
```

## 📊 Protocol Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| Minimum Stake | 1 STX | Minimum amount to stake |
| Minimum Loan | 0.5 STX | Minimum loan amount |
| Stake Interest Rate | 5% APY | Annual percentage yield for stakers |
| Loan Interest Rate | 8% APY | Annual percentage rate for borrowers |
| Liquidation Threshold | 150% | Minimum collateralization ratio |
| Max Interest Rate | 20% APY | Maximum allowed interest rate |

## 🔐 Security Features

### Access Control
- **Owner Authorization**: Critical functions restricted to contract owner
- **Input Validation**: Comprehensive validation of all user inputs
- **Amount Checks**: Minimum and maximum amount validations

### Risk Management
- **Collateralization Monitoring**: Continuous monitoring of loan-to-collateral ratios
- **Liquidation Protection**: Automated liquidation prevents bad debt
- **Emergency Controls**: Contract pause and emergency withdrawal capabilities

### Error Handling
- **Comprehensive Error Codes**: Clear error messages for all failure cases
- **State Validation**: Validates contract and user state before operations
- **Transaction Safety**: Safe STX transfers with proper error handling

## 📈 Interest Calculation

Interest is calculated using simple interest formula:

```
Interest = Principal × Rate × Time / (365 days × 10000 basis points)
```

Where:
- Time is measured in blocks since last update
- Rates are stored in basis points (100 = 1%)
- Interest compounds when users interact with the protocol

## 🧪 Testing

The contract includes comprehensive test coverage for:

- ✅ Staking and withdrawal operations
- ✅ Loan issuance and repayment
- ✅ Interest calculations
- ✅ Liquidation scenarios
- ✅ Administrative functions
- ✅ Error conditions and edge cases

Run tests with:
```bash
clarinet test
```

## 🔍 Contract Statistics

Monitor protocol health with `get-contract-stats()`:

```clarity
{
  total-staked: uint,      // Total STX staked in protocol
  total-borrowed: uint,    // Total STX borrowed by users  
  stake-rate: uint,        // Current staking interest rate
  loan-rate: uint,         // Current loan interest rate
  paused: bool            // Contract pause status
}
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📞 Support

For questions and support, please open an issue in the repository or contact the development team.

## ⚠️ Disclaimer

This smart contract is for educational and experimental purposes. Please conduct thorough testing and security audits before using in production. Users should understand the risks associated with DeFi protocols and only invest what they can afford to lose.

---

Built with ❤️ on Stacks blockchain
