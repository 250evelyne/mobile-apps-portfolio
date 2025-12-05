# 💰 Bankly - Mobile Banking Application

A secure and user-friendly mobile banking application built with Java and Firebase, enabling users to perform essential financial operations including deposits, withdrawals, transfers, and transaction management.

![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)
![Android Studio](https://img.shields.io/badge/Android_Studio-3DDC84?style=for-the-badge&logo=android-studio&logoColor=white)

## 📋 Table of Contents
- [About the Project](#about-the-project)
- [Key Features](#key-features)
- [Technologies Used](#technologies-used)
- [Application Architecture](#application-architecture)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Application Flow](#application-flow)
- [Screenshots](#screenshots)
- [What I Learned](#what-i-learned)
- [Future Enhancements](#future-enhancements)
- [Author](#author)

## 📖 About the Project

Bankly is a realistic simulation of a digital banking system designed to help users perform basic financial operations in a secure and organized environment. The application provides a complete banking experience with user authentication, balance management, transaction scheduling, and comprehensive transaction history tracking.

### Project Goals
- Create a functional mobile banking simulation
- Implement secure user authentication and data management
- Provide intuitive financial transaction capabilities
- Enable transaction scheduling and confirmation workflows
- Maintain clear and user-friendly interfaces

## ✨ Key Features

### 🔐 User Authentication
- Secure user registration with Firebase Authentication
- Email and password login system
- Personal account creation with initial balance setup
- Protected user data and privacy

### 💳 Financial Operations
- **Deposit**: Add funds to your account balance
- **Withdraw**: Remove funds from your account (with balance validation)
- **Transfer**: Send money to other registered users
- **Transaction Scheduling**: Schedule future transactions with calendar selection
- **Balance Management**: Real-time balance updates across all operations

### 📊 Transaction Management
- **Dual Transaction Views**:
  - Scheduled Transactions (upcoming transfers)
  - Completed Transactions (past operations)
- **Transaction Details**: View comprehensive information for each transaction
- **Transaction Confirmation**: Recipients can confirm receipt of transferred funds
- **Transaction History**: Complete record of all financial activities
- **Status Tracking**: Monitor transaction states (Scheduled, Completed, Confirmed)

### 🎯 User Experience
- Clean and intuitive interface
- Easy navigation between screens
- Real-time data synchronization
- Secure data storage with Firebase
- User-friendly error handling

## 🛠️ Technologies Used

### Core Technologies
- **Language**: Java
- **IDE**: Android Studio
- **Database**: Firebase Realtime Database / Firestore
- **Authentication**: Firebase Authentication
- **UI Design**: XML Layouts with Material Design principles
- **Version Control**: Git

### Firebase Services
- Firebase Authentication (User registration and login)
- Firebase Realtime Database (Data storage and retrieval)
- Real-time data synchronization
- Secure cloud storage

## 🏗️ Application Architecture

The application follows a structured architecture with clear separation of concerns:

```
Bankly/
├── Activities/           # Screen controllers
├── Models/              # Data structures
├── Services/            # Firebase integration
├── Layouts/             # XML UI designs
└── Resources/           # Images and assets
```

### MVVM Pattern
The app implements elements of the Model-View-ViewModel pattern for better code organization and maintainability.

## 📂 Project Structure

### Core Activities

#### 1. **LoginActivity.java**
- Handles user authentication through Firebase
- Validates user credentials
- Redirects to HomeActivity upon successful login
- Clean error handling for failed login attempts

#### 2. **SignUpActivity.java**
- New user registration system
- Collects user information (name, email, password)
- Sets up initial account balance
- Stores user data securely in Firebase
- Automatic redirect to HomeActivity after registration

#### 3. **HomeActivity.java**
The main hub of the application featuring:
- **Two Tab System**:
  - Scheduled Transactions tab
  - Completed Transactions tab
- **Current Balance Display**: Real-time account balance
- **Transaction List**: Dynamic loading from Firebase
- **Navigation Options**:
  - Add new transaction (Deposit/Withdraw/Transfer)
  - View transaction details
  - Access transaction history
- Firebase integration for real-time data updates

#### 4. **DepositActivity.java**
- User-friendly deposit interface
- Amount input with validation
- Real-time balance update
- Instant Firebase synchronization
- Back navigation to HomeActivity

#### 5. **WithdrawActivity.java**
- Withdrawal interface with balance checking
- Insufficient funds validation
- Amount input with error handling
- Balance deduction and Firebase update
- Return navigation to HomeActivity

#### 6. **CreateTransactionActivity.java**
Comprehensive transfer creation system:
- **Recipient Selection**: Choose from registered users only
- **Amount Input**: Enter transfer amount with validation
- **Date Selection**: Calendar picker for scheduling transactions
- **Transaction Status Logic**:
  - Scheduled: For future-dated transactions
  - Completed: For current or past-dated transactions
- **Validation**: Ensures recipient exists and has sufficient balance
- Firebase transaction record creation

#### 7. **TransactionDetailActivity.java**
Detailed transaction view displaying:
- **Transaction Information**:
  - Sender name
  - Receiver name
  - Transaction amount
  - Transaction date
  - Current status
- **Status Messages**:
  - "Transaction not yet processed" (Scheduled)
  - Confirm button (Completed but not confirmed)
  - "Confirmed" (Completed and confirmed)
- **Confirmation Feature**: Recipients can confirm receipt
- Firebase status update functionality

### Core Services

#### 8. **DatabaseService.java**
Central Firebase management class handling:
- **User Operations**:
  - User data storage and retrieval
  - Balance management and updates
  - User authentication data
- **Transaction Operations**:
  - Create new transactions
  - Fetch transaction lists
  - Update transaction status
  - Query scheduled and completed transactions
- **Data Synchronization**: Real-time updates across devices
- **Error Handling**: Robust Firebase error management

### Data Models

#### 9. **User.java**
User data structure containing:
- User ID (unique identifier)
- Name
- Email address
- Current account balance
- Registration timestamp

#### 10. **Transaction.java**
Transaction data structure containing:
- Transaction ID (unique identifier)
- Sender information
- Receiver information
- Transaction amount
- Transaction date
- Transaction status (Scheduled/Completed/Confirmed)
- Timestamp

## 🚀 Installation

### Prerequisites
- Android Studio Arctic Fox or later
- JDK 11 or higher
- Android SDK (API Level 21+)
- Firebase account with project setup

### Setup Steps

1. **Clone the repository:**
```bash
git clone https://github.com/250evelyne/android-apps-portfolio.git
cd android-apps-portfolio/Bankly
```

2. **Open in Android Studio:**
   - Launch Android Studio
   - Select "Open an existing project"
   - Navigate to the Bankly folder
   - Click "OK"

3. **Configure Firebase:**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Create a new project or use existing
   - Add an Android app to your Firebase project
   - Download `google-services.json`
   - Place the file in `app/` directory

4. **Set up Firebase Services:**
   - Enable Firebase Authentication (Email/Password)
   - Enable Firebase Realtime Database or Firestore
   - Set appropriate security rules

5. **Sync Gradle:**
   - Android Studio will automatically prompt to sync
   - Wait for Gradle build to complete
   - Resolve any dependency issues

6. **Build and Run:**
   - Connect an Android device or start an emulator
   - Click the "Run" button or press `Shift + F10`
   - Select your target device
   - App will install and launch

### Firebase Database Structure

```json
{
  "users": {
    "userId1": {
      "name": "John Doe",
      "email": "john@example.com",
      "balance": 1000.00
    }
  },
  "transactions": {
    "transactionId1": {
      "senderId": "userId1",
      "receiverId": "userId2",
      "amount": 100.00,
      "date": "2024-12-05",
      "status": "Completed"
    }
  }
}
```

## 🔄 Application Flow

### User Journey

1. **App Launch**
   - User opens the Bankly application
   - Presented with LoginActivity screen

2. **Authentication**
   - **Existing Users**: Enter credentials → Firebase validation → HomeActivity
   - **New Users**: Click "Sign Up" → Fill registration form → Create account → HomeActivity

3. **Home Dashboard**
   - View current account balance
   - See two tabs: Scheduled and Completed transactions
   - Access transaction creation options

4. **Performing Operations**
   
   **Deposit Flow:**
   - Click "Deposit" button
   - Enter amount
   - Confirm → Balance updated in Firebase
   - Return to HomeActivity with updated balance

   **Withdraw Flow:**
   - Click "Withdraw" button
   - Enter amount
   - System validates sufficient balance
   - Confirm → Balance deducted in Firebase
   - Return to HomeActivity

   **Transfer Flow:**
   - Click "Transfer" button
   - Select recipient from registered users
   - Enter amount
   - Choose date using calendar picker
   - Confirm → Transaction created in Firebase
   - Status set based on date (Scheduled/Completed)
   - Return to HomeActivity

5. **Transaction Management**
   - Tap any transaction from list
   - View full transaction details in TransactionDetailActivity
   - **If Scheduled**: See "Transaction not yet processed" message
   - **If Completed**: Recipient can click "Confirm Receipt"
   - Confirmation updates status in Firebase

6. **Continuous Sync**
   - All changes reflect immediately across app
   - Balance updates in real-time
   - Transaction lists refresh automatically

### Data Flow Diagram

```
User Input → Activity → DatabaseService → Firebase → Real-time Update → UI Refresh
```

## 📸 Demonstration video 
[Watch how the app functions](https://drive.google.com/file/d/1oSu1Kvk3IYgvYw0hf0bSmjvyvV1cWld2/view)


- Login screen
- Sign up screen
- Home activity with tabs
- Deposit screen
- Withdraw screen
- Create transaction screen
- Transaction detail screen

## 📚 What I Learned

Through developing Bankly, I gained valuable hands-on experience with:

### Android Development
- Building multi-activity Android applications
- Implementing navigation between screens
- Creating responsive XML layouts
- Handling user input and validation
- Managing application lifecycle

### Firebase Integration
- Setting up Firebase Authentication
- Implementing user registration and login
- Working with Firebase Realtime Database
- Real-time data synchronization
- Secure data storage and retrieval

### Programming Concepts
- Object-oriented programming in Java
- Data modeling and structures
- Asynchronous operations and callbacks
- Error handling and exception management
- Code organization and separation of concerns

### Financial Logic
- Balance management and validation
- Transaction processing workflows
- Date-based scheduling logic
- Multi-user transaction systems
- Status tracking and updates

### Problem Solving
- Debugging complex application flows
- Ensuring data consistency
- Handling edge cases (insufficient funds, invalid users)
- Implementing confirmation workflows
- User experience optimization

## 🔮 Future Enhancements

### Planned Features
- [ ] **Transaction Categories**: Categorize transactions (bills, shopping, etc.)
- [ ] **Spending Analytics**: Visual charts and spending reports
- [ ] **Recurring Transactions**: Set up automatic monthly transfers
- [ ] **Transaction Search**: Search and filter transaction history
- [ ] **Multiple Accounts**: Support checking and savings accounts
- [ ] **Notifications**: Push notifications for transaction confirmations
- [ ] **Security PIN**: Add PIN or biometric authentication
- [ ] **Transaction Limits**: Set daily/weekly spending limits
- [ ] **Profile Management**: Edit user profile and settings
- [ ] **Dark Mode**: Theme customization options

### Technical Improvements
- [ ] Migrate to Kotlin for modern Android development
- [ ] Implement MVVM architecture fully with LiveData
- [ ] Add unit tests and instrumented tests
- [ ] Improve error handling and user feedback
- [ ] Optimize database queries for better performance
- [ ] Add offline mode with local caching
- [ ] Implement data encryption for sensitive information
- [ ] Add logging and analytics tracking

## 🐛 Known Issues


- Balance update delay on slow network connections

## 📄 License

This project was developed for educational purposes as part of the Computer Science program at LaSalle College.

## 👤 Author

**Evelyne Mukarukundo**  
Computer Science Student @ LaSalle College

- 📧 Email: evelynekessie@gmail.com
- 💼 LinkedIn: [EVELYNE MUKARUKUNDO](https://www.linkedin.com/in/evelyne-mukarukundo-317407188/)
- 📍 Location: Montréal, QC, Canada
- 🎓 Program: DEC in Computer Science - Programming

## 🙏 Acknowledgments

- **LaSalle College** - Computer Science Program
- **Firebase** - Backend infrastructure and documentation
- **Android Developers** - Comprehensive documentation and guides
- **Stack Overflow Community** - Problem-solving support
- **Material Design** - UI/UX guidelines

## 📞 Support

If you have questions about this project or want to connect:
- Open an issue in this repository
- Email me at evelynekessie@gmail.com
- Connect with me on LinkedIn

---

⭐ **If you found this project interesting or helpful, please consider giving it a star!**

**Note**: This is a student project developed for learning purposes and is not intended for production use with real financial data.

---

*Last Updated: December 2024*
