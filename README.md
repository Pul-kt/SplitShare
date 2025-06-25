# SplitShare 💰

A C++ implementation of an expense sharing application similar to Splitwise. SplitShare allows users to split expenses among friends, manage group expenses, and simplify debts with an intuitive command-line interface.

## ✨ Features

### Core Functionality
- **User Management**: Create and manage user accounts
- **Group Management**: Create groups and manage group memberships
- **Expense Splitting**: Support for multiple split types:
  - Equal split among participants
  - Exact amount specification
  - Percentage-based splitting
- **Individual Expenses**: Track expenses between two users
- **Settlement System**: Record payments and settle debts
- **Debt Simplification**: Optimize payment flows to minimize transactions
- **Real-time Notifications**: Observer pattern implementation for expense updates

### Advanced Features
- **Balance Tracking**: Track individual and group balances
- **Group Validation**: Prevent users from leaving groups with outstanding balances
- **Memory Management**: Proper resource cleanup and memory management
- **Error Handling**: Comprehensive validation and error handling

## 🏗️ Design Patterns Used

This project demonstrates several important design patterns:

1. **Singleton Pattern**: ExpenseManager ensures single instance
2. **Strategy Pattern**: Different splitting strategies (Equal, Exact, Percentage)
3. **Observer Pattern**: Notification system for expense updates
4. **Factory Pattern**: SplitStrategy creation
5. **Facade Pattern**: Simplified interface for complex operations

## 🚀 Getting Started

### Prerequisites
- C++ compiler with C++11 support or higher
- Standard Template Library (STL)

### Compilation
```bash
g++ -std=c++11 -o splitshare main.cpp
```

### Running the Application
```bash
./splitshare
```

## 📊 Usage Examples

### Creating Users and Groups
```cpp
// Create users
User* alice = manager->createUser("Alice", "alice@email.com");
User* bob = manager->createUser("Bob", "bob@email.com");

// Create group and add members
Group* group = manager->createGroup("Weekend Trip");
manager->addUserToGroup(alice->userId, group->groupId);
manager->addUserToGroup(bob->userId, group->groupId);
```

### Adding Expenses
```cpp
// Equal split expense
vector<string> members = {alice->userId, bob->userId};
manager->addExpenseToGroup(group->groupId, "Dinner", 100.0, 
                          alice->userId, members, SplitType::EQUAL);

// Exact amount split
vector<double> amounts = {60.0, 40.0};
manager->addExpenseToGroup(group->groupId, "Groceries", 100.0,
                          bob->userId, members, SplitType::EXACT, amounts);
```

### Settling Payments
```cpp
// Settle payment within group
manager->settlePaymentInGroup(group->groupId, bob->userId, alice->userId, 50.0);

// Individual settlement
manager->settleIndividualPayment(bob->userId, alice->userId, 25.0);
```

## 🏛️ Architecture

### Class Structure
```
Splitwise (Singleton)
├── User (Observer)
│   ├── Balance tracking
│   └── Notification handling
├── Group (Observable)
│   ├── Member management
│   ├── Expense tracking
│   └── Balance calculation
├── Expense
│   └── Transaction details
└── Split Strategies
    ├── EqualSplit
    ├── ExactSplit
    └── PercentageSplit
```

### Key Components

- **Splitwise**: Main facade class managing all operations
- **User**: Represents individual users with balance tracking
- **Group**: Manages group expenses and member relationships  
- **Expense**: Stores expense details and split information
- **Split Strategies**: Handle different expense splitting logic
- **DebtSimplifier**: Optimizes payment flows using greedy algorithm

## 🔧 Technical Details

### Balance Management
- Users maintain individual balance sheets
- Groups track internal member balances separately
- Automatic cleanup of zero balances
- Debt simplification using graph algorithms

### Memory Management
- Smart pointer usage for automatic cleanup
- Proper destructor implementation
- Resource management in group operations

### Validation
- User membership validation for group operations
- Balance verification before user removal
- Input validation for all operations

## 🧪 Sample Output

```
=========== Creating Users ====================
User created: Aditya (ID: user1)
User created: Rohit (ID: user2)

=========== Creating Group and Adding Members ====================
Group created: Hostel Expenses (ID: group1)
Aditya added to group Hostel Expenses

=========== Adding Expenses in group ====================
[NOTIFICATION to Aditya]: New expense added: Lunch (Rs 800.000000)

=========== Balance for Aditya ====================
Total you owe: Rs 0.00
Total others owe you: Rs 600.00
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📋 Future Enhancements

- [ ] Persistent data storage (database integration)
- [ ] REST API implementation
- [ ] Web interface
- [ ] Mobile app support
- [ ] Currency conversion
- [ ] Expense categories and tags
- [ ] Receipt image handling
- [ ] Advanced reporting and analytics

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by Splitwise application
- Built as a Low Level Design (LLD) practice project
- Demonstrates object-oriented programming principles
- Showcases design pattern implementation in C++

## 📞 Contact

Your Name - pulkit.jindal30@gmail.com

Project Link: https://github.com/Pul-kt/SplitShare
