# Stock Management

This smart contract, named `StockManagement`, is designed to manage the pricing and transactions of a stock system on the Ethereum blockchain. It allows the owner of the contract to set and update share prices for different stocks and enables users to perform stock transactions by specifying an asked price.

## Smart Contract Overview

### State Variables

- **`stockOwner`**: The Ethereum address of the owner of the stock management system.
- **`sharePrices`**: A mapping that associates each stock's unique identifier (`stockId`) with its corresponding share price.

### Constructor

The constructor sets the `stockOwner` variable to the Ethereum address of the contract deployer.

### Modifiers

- **`onlyStockOwner`**: A modifier that restricts certain functions to be callable only by the owner of the stock.

### Functions

1. **`setSharePrice(uint256 stockId, uint256 price) external onlyStockOwner`**
   - Allows the owner to set or update the share price of a specific stock identified by `stockId`.
   - Requires that the price is non-negative.

2. **`processStockTransaction(uint256 stockId, uint256 askedPrice) external`**
   - Allows users to perform stock transactions for a specific stock identified by `stockId`.
   - Requires that the asked price is greater than 0.
   - Checks if the asked price exceeds the available shares and reverts the transaction if true.
   - Reduces the available shares if the transaction is valid.

### Error Handling

- The contract uses `require` statements to ensure that certain conditions are met before proceeding with the execution of functions. If a `require` statement evaluates to `false`, the function will revert, and any changes will be rolled back.

- The contract uses `assert` statements to check for conditions that should never evaluate to `false` under normal circumstances. If an `assert` statement evaluates to `false`, indicating a critical issue, the transaction will be reverted, and state changes will be rolled back.

## License

This smart contract is licensed under the MIT License. See the `SPDX-License-Identifier` comment at the beginning of the contract for more details.
## Author

belagaliabhinandan@gmail.com
