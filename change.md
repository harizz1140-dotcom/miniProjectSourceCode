# Changes Made to trans.c - Bank Account System

## Overview
This is a comprehensive Bank Account Management System written in C that provides file-based banking operations with advanced features.

## Key Features Implemented

### 1. **Core Data Structure**
- **clientData struct**: Contains account information
  - Account number (`acctNum`)
  - Last name (`lastName`)
  - First name (`firstName`)
  - Account balance (`balance`)

### 2. **Main Menu System** 
- Interactive menu with 9 options:
  1. Store formatted text file for printing
  2. Update an account
  3. Add a new account
  4. Delete an account
  5. View a specific account
  6. Display all active accounts
  7. Transfer funds between accounts
  8. Show bank statistics
  9. Exit program

### 3. **File Operations**
- **textFile()**: Exports accounts to accounts.txt in formatted text
- **credit.dat**: Binary file for persistent data storage
- File auto-creation if it doesn't exist

### 4. **Account Management Functions**

#### **newRecord()**
- Create new bank accounts
- Validate account numbers (1-100)
- Prevent duplicate accounts
- Input parsing for: LastName FirstName Balance

#### **updateRecord()**
- Modify existing account balances
- Accept charges (negative) or payments (positive)
- Display updated balance confirmation

#### **deleteRecord()**
- Remove accounts by setting them to blank records
- Prevents deletion of non-existent accounts

#### **viewAccount()**
- View single account details
- Read-only operation (no modifications)
- Display formatted account information

#### **displayAllAccounts()**
- Show all active accounts in table format
- Displays: Account#, Last Name, First Name, Balance
- Shows message if no active accounts exist

### 5. **Advanced Features**

#### **transferFunds()**
- Transfer money between two accounts
- Validates source and destination accounts
- Checks for sufficient funds before transfer
- Prevents self-transfers
- Updates both accounts atomically

#### **showStatistics()**
- Calculate total active accounts
- Compute total bank balance
- Identify highest balance account
- Display formatted statistics report

### 6. **Input Validation & Safety**
- **clearInputBuffer()**: Safely clears stdin buffer
- **getValidUnsignedInt()**: Validates unsigned integer input
- Account number range validation (1-100)
- Balance and amount validation
- Safe string input with buffer limits
- String truncation protection for names

### 7. **User Experience Enhancements**
- Formatted console output with aligned columns
- Clear menu navigation
- Success/error messages for all operations
- Input validation with retry loops
- Safe file pointer management

## Technical Improvements
- Proper struct initialization
- Safe string operations (strncpy with bounds checking)
- Correct file pointer positioning (fseek)
- Input buffer management
- Error handling for file operations
- Protection against buffer overflows

## File Structure
```
trans.c
├── Includes & Defines
├── Structure Definition (clientData)
├── Function Prototypes
├── main() - Menu loop and file management
├── Helper Functions
│   ├── clearInputBuffer()
│   └── getValidUnsignedInt()
├── File Operations
│   └── textFile()
├── Account Management
│   ├── newRecord()
│   ├── updateRecord()
│   ├── deleteRecord()
│   └── viewAccount()
├── Display Functions
│   └── displayAllAccounts()
├── Advanced Features
│   ├── transferFunds()
│   └── showStatistics()
└── Menu System
    └── enterChoice()
```

## Data Persistence
- Uses binary file (credit.dat) for data storage
- Maintains account information across program sessions
- Random-access file operations for efficient record management
