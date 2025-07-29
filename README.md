# PancakeSwap Trading Bot

A web-based application for automated token trading on PancakeSwap using the Binance Smart Chain (BSC).

## Features

- **Web Interface**: User-friendly web interface for easy interaction
- **BSC Connection**: Connects to Binance Smart Chain network
- **Wallet Balance**: Check your BNB balance
- **Token Swapping**: Swap BNB for any BSC token using PancakeSwap
- **Real-time Status**: Check connection status and transaction results
- **Transaction Tracking**: Get transaction hashes for verification on BscScan

## Prerequisites

- Python 3.11+
- A BSC wallet with some BNB for gas fees and trading
- Private key of your BSC wallet

## Installation

1. Clone or download this application
2. Navigate to the project directory:
   ```bash
   cd pancakeswap-bot-app
   ```

3. Activate the virtual environment:
   ```bash
   source venv/bin/activate
   ```

4. Install dependencies (if not already installed):
   ```bash
   pip install -r requirements.txt
   ```

## Configuration

1. Edit the `src/config.py` file and replace the private key:
   ```python
   private = "YOUR_PRIVATE_KEY_HERE"
   ```

   **⚠️ SECURITY WARNING**: Never share your private key or commit it to version control!

## Usage

1. Start the application:
   ```bash
   python src/main.py
   ```

2. Open your web browser and navigate to:
   ```
   http://localhost:5000
   ```

3. Use the web interface to:
   - Check BSC connection status
   - View your wallet balance
   - Execute token swaps

## API Endpoints

The application provides the following REST API endpoints:

- `GET /api/status` - Check BSC connection status
- `GET /api/balance` - Get wallet balance
- `POST /api/swap` - Execute token swap

### Swap API Example

```bash
curl -X POST http://localhost:5000/api/swap \
  -H "Content-Type: application/json" \
  -d '{
    "token_address": "0xTokenAddressHere",
    "amount_bnb": 0.001,
    "gas_price_gwei": 5
  }'
```

## Important Notes

### Security
- **Private Key Security**: Your private key is stored in `src/config.py`. Keep this file secure and never share it.
- **Testnet First**: Consider testing on BSC Testnet before using mainnet.
- **Backup**: Always backup your wallet and private keys.

### Trading
- **Slippage**: The current implementation uses `amountOutMin = 0`, which means no slippage protection. This is not recommended for production use.
- **Gas Fees**: Ensure you have sufficient BNB for gas fees (typically 0.001-0.005 BNB per transaction).
- **Token Verification**: Always verify token addresses before trading to avoid scams.

### Technical
- **Development Server**: The included server is for development only. Use a production WSGI server for production deployment.
- **Error Handling**: Check transaction hashes on [BscScan](https://bscscan.com) to verify successful transactions.

## Troubleshooting

### Common Issues

1. **Insufficient Funds Error**:
   - Ensure your wallet has enough BNB for both the swap amount and gas fees
   - Current transaction requires: swap amount + (gas limit × gas price)

2. **Connection Issues**:
   - Check your internet connection
   - BSC RPC endpoint might be temporarily unavailable

3. **Transaction Failures**:
   - Verify the token address is correct
   - Check if the token has sufficient liquidity on PancakeSwap
   - Increase gas price if network is congested

### Getting Help

- Check transaction details on [BscScan](https://bscscan.com)
- Verify token contracts on [BSC Token Tracker](https://bscscan.com/tokens)
- Review PancakeSwap documentation for trading requirements

## Disclaimer

This software is provided "as is" without warranty. Use at your own risk. Always:
- Test with small amounts first
- Verify all token addresses
- Understand the risks of cryptocurrency trading
- Keep your private keys secure

## License

This project is based on the original PancakeSwap bot by CodeWithJoe2020 and has been enhanced with a web interface and additional features.

