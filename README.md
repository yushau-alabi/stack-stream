# Mixer Contract

## Overview

The Mixer Contract is a sophisticated Stacks blockchain smart contract designed to provide a secure and efficient mechanism for creating and managing mixer pools. This contract enables users to pool and redistribute funds while maintaining enhanced security features and transaction controls.

## Features

### Key Functionalities

- Create mixer pools
- Join existing mixer pools
- Deposit and withdraw funds
- Distribute pool funds with mixing fees
- Enhanced security mechanisms
- Emergency pause functionality

### Security Enhancements

- Daily transaction limits
- Participant verification
- Maximum pool participant restrictions
- Transaction amount limitations
- Emergency contract pause

## Contract Constants

### Transaction Limits

- Maximum Daily Transaction Limit: 10,000,000,000 STX
- Maximum Pool Participants: 10
- Maximum Transaction Amount: 1,000,000,000,000 STX
- Minimum Pool Amount: 100,000 STX
- Mixing Fee: 2% of total pool funds

## Functions

### Public Functions

#### `initialize()`

- Initializes the contract
- Can only be called by the contract owner
- Prevents re-initialization

#### `deposit(amount: uint)`

- Allows users to deposit STX into their contract balance
- Enforces daily transaction limits
- Checks transaction amount validity

#### `withdraw(amount: uint)`

- Enables users to withdraw funds from their contract balance
- Implements daily transaction limit checks
- Verifies sufficient user balance

#### `create-mixer-pool(pool-id: uint, initial-amount: uint)`

- Creates a new mixer pool
- Requires minimum initial pool amount
- Validates user balance and pool parameters

#### `join-mixer-pool(pool-id: uint, amount: uint)`

- Allows users to join an existing mixer pool
- Prevents duplicate participants
- Checks pool capacity and user balance

#### `distribute-pool-funds(pool-id: uint)`

- Distributes pool funds among participants
- Applies 2% mixing fee
- Marks pool as inactive after distribution

#### `toggle-contract-pause()`

- Emergency function to pause/unpause the entire contract
- Can only be executed by contract owner

#### `withdraw-protocol-fees()`

- Allows contract owner to withdraw accumulated mixing fees

### Read-Only Functions

- `get-user-balance(user: principal)`: Returns user's contract balance
- `get-daily-limit-remaining(user: principal)`: Calculates remaining daily transaction limit
- `get-contract-status()`: Provides overall contract status
- `get-pool-details(pool-id: uint)`: Retrieves specific mixer pool details

## Error Handling

The contract includes comprehensive error handling with specific error codes:

- `ERR-NOT-AUTHORIZED` (u1000)
- `ERR-INVALID-AMOUNT` (u1001)
- `ERR-INSUFFICIENT-BALANCE` (u1002)
- And more... (refer to error constants in the contract)

## Best Practices and Recommendations

1. Always verify pool details before joining
2. Be aware of daily transaction limits
3. Understand mixing fees before pool participation
4. Keep track of your contract balance
5. Be cautious of pool size and participation restrictions

## Security Considerations

- Contract can be paused in emergencies
- Strict participant and transaction validations
- Daily transaction limits prevent potential abuse
- Mixing fees support contract sustainability

## Deployment and Usage

### Prerequisites

- Stacks blockchain environment
- Compatible wallet supporting smart contract interactions

### Recommended Workflow

1. Initialize the contract
2. Deposit funds
3. Create or join a mixer pool
4. Distribute pool funds
5. Withdraw as needed
