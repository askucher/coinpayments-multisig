# USDT Multisig

A multi-signature wallet for USDT on EVM-compatible chains (Ethereum, TRON) with a Flutter cross-platform app.

## Prerequisites

Before you begin, install the following tools:

### 1. Foundry (Smart Contract Development)

Foundry is a blazing fast toolkit for Ethereum application development written in Rust.

```bash
curl -L https://foundry.paradigm.xyz | bash
foundryup
```

Foundry includes:
- **Forge** - Ethereum testing framework
- **Cast** - CLI for interacting with smart contracts
- **Anvil** - Local Ethereum node

📖 [Foundry Documentation](https://book.getfoundry.sh/)

### 2. Flutter (Mobile/Desktop App)

```bash
# macOS (Homebrew)
brew install flutter

# Or download from https://flutter.dev/docs/get-started/install
```

### 3. Rust & Cargo (TRON Utils)

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

### 4. Just (Command Runner)

```bash
# macOS
brew install just

# Or see https://github.com/casey/just#installation
```

## Quick Start

```bash
# List all available commands
just

# Run smart contract tests
just test

# Start local Ethereum node
just anvil

# Deploy contracts (in another terminal)
just deploy-all

# Run the Flutter app
just app-macos
```

## Smart Contract Commands

| Command | Description |
|---------|-------------|
| `just build` | Compile Solidity contracts |
| `just test` | Run all tests with `forge test` |
| `just test-gas` | Run tests with gas report |
| `just test-match <pattern>` | Run tests matching pattern |
| `just fmt` | Format Solidity code |
| `just clean` | Clean build artifacts |

### Local Development

```bash
# Terminal 1: Start local node
just anvil

# Terminal 2: Deploy contracts
just deploy-all

# Terminal 3: Run app
just app-macos
```

### Contract Interaction

```bash
just balance <contract>         # Get USDT balance
just owners <contract>          # List owners
just threshold <contract>       # Get threshold
just tx-count <contract>        # Get transaction count
just submit <contract> <to> <amount>  # Submit transaction
just approve <contract> <tx_id> [owner]  # Approve transaction
just execute <contract> <tx_id>  # Execute transaction
```

## Flutter App Commands

| Command | Description |
|---------|-------------|
| `just app-deps` | Install Flutter dependencies |
| `just app-macos` | Run on macOS |
| `just app-ios` | Run on iOS simulator |
| `just app-android` | Run on Android |
| `just app-web` | Run on Chrome (web) |
| `just build-macos` | Build macOS release |
| `just build-web` | Build web release |
| `just app-analyze` | Analyze Flutter code |
| `just app-fmt` | Format Dart code |
| `just app-clean` | Clean Flutter build |

### Multi-Instance Testing

Run multiple app instances with isolated storage for testing different owners:

```bash
just app1  # Owner 1 instance
just app2  # Owner 2 instance
just app3  # Owner 3 instance
# ... up to just app8
```

## TRON Deployment

```bash
# Build TRON utilities
just build-tron-utils

# Generate TRON wallet
just tron-generate-key

# Deploy to TRON Nile testnet
just deploy-all-tron

# Deploy to TRON mainnet
just tron-deploy-mainnet <private_key> <usdt> <owners> <threshold>
```

## Project Structure

```
multisig/
├── src/                    # Solidity contracts
│   └── Multisig.sol       # Main multisig contract
├── test/                   # Forge tests
│   └── Multisig.t.sol     # Contract tests
├── app/                    # Flutter application
├── tron-utils/            # Rust CLI for TRON deployment
├── TRC20_USDT/            # TRC20 USDT reference contracts
└── justfile               # All development commands
```

## License

MIT
