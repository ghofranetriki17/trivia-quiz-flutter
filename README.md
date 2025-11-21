# trivia-quiz-flutter
# Trivia Quiz Flutter

A feature-rich mobile quiz application built with Flutter that provides interactive trivia questions from various categories using the Open Trivia Database API.

## Features

- **Multiple Categories**: Choose from various question categories
- **Difficulty Levels**: Easy, medium, and hard difficulty settings
- **Timer**: Limited time to answer each question
- **Visual Feedback**: Color-coded responses (green for correct, red for incorrect)
- **Sound Effects**: Audio feedback for right and wrong answers
- **Vibration**: Haptic feedback on incorrect answers
- **Multi-language**: Support for English, French, and Arabic
- **Dark/Light Theme**: Toggle between light and dark modes
- **Local Storage**: Save scores and preferences locally
- **Leaderboard**: Track and display high scores

## Technology Stack

- **Framework**: Flutter
- **API**: Open Trivia Database (OpenTDB)
- **State Management**: Flutter StatefulWidget
- **Local Storage**: Shared Preferences
- **Internationalization**: Flutter Localizations

## Installation

1. Ensure you have Flutter installed on your machine
2. Clone this repository:
   ```bash
   git clone https://github.com/ghofranetriki17/trivia-quiz-flutter.git
   ```
3. Navigate to the project directory:
   ```bash
   cd trivia-quiz-flutter
   ```
4. Install dependencies:
   ```bash
   flutter pub get
   ```
5. Run the application:
   ```bash
   flutter run
   ```

## Dependencies

The project uses the following main packages:

- `http`: For API calls to OpenTDB
- `html_unescape`: To decode HTML entities in questions
- `audioplayers`: For sound effects
- `vibration`: For haptic feedback
- `shared_preferences`: For local data storage
- `flutter_localizations`: For multi-language support

## Project Structure

```
lib/
├── main.dart                 # Application entry point
├── models/
│   └── settings.dart         # Settings data model
├── screens/
│   ├── home_screen.dart      # Main menu screen
│   ├── quiz_setup_screen.dart # Quiz configuration
│   ├── quiz_screen.dart      # Main quiz interface
│   ├── result_screen.dart    # Results display
│   └── settings_screen.dart  # App settings
└── services/
    ├── settings_service.dart # Settings management
    ├── theme_service.dart    # Theme management
    └── local_storage_service.dart # Score storage
```

## Development Approach

### Step-by-Step Implementation

**Week 1 - Foundation**
- Project creation and Flutter setup
- `pubspec.yaml` configuration with required packages
- Basic folder structure organization
- Home screen implementation

**Week 2 - Navigation & API**
- Quiz setup screen with category API integration
- Navigation between screens using named routes
- Basic quiz screen without advanced features

**Week 3 - Core Features**
- Timer implementation for each question
- Sound effects and vibration feedback
- Score management system

**Week 4 - Storage & Polish**
- Local storage service for scores
- Results screen and leaderboard
- Multi-language support (English, French, Arabic)
- Dark/light theme implementation

**Week 5 - Final Touches**
- Error handling
- UX improvements (button colors, animations)
- Testing and debugging

### Key Technical Solutions

**Timer Implementation**
```dart
Timer.periodic(Duration(seconds: 1), (timer) {
  setState(() {
    timeLeft--;
    if (timeLeft <= 0) {
      timer.cancel();
      _autoNextQuestion();
    }
  });
});
```

**Sound & Vibration**
- Audio feedback for correct/incorrect answers
- Vibration on wrong answers (300ms duration)
- Respects user preferences for sound enable/disable

**Answer Shuffling**
```dart
List<String> _getShuffledAnswers(Map question) {
  final answers = List<String>.from(question['incorrect_answers']);
  answers.add(question['correct_answer']);
  answers.shuffle(Random());
  return answers;
}
```

**Multi-language Support**
- ARB files for English and French translations
- Flutter localization integration
- Dynamic language switching

## Usage

1. **Home Screen**: Start from the main menu to begin a quiz or view settings
2. **Quiz Setup**: Select category, difficulty, and number of questions
3. **Quiz**: Answer questions within the time limit with visual and audio feedback
4. **Results**: View your score and review correct answers
5. **Leaderboard**: Check your previous scores and rankings

## Developers

- **Ghofrane Triki**
- **Baya Jribi**

## Academic Context
- **Course**: Mobile Programming  
- **Teacher**: S. Hadhri
- **Institution**: IIT - Institut International de Technologie
- **Academic Year**: 2024/2025

## License

This project is for educational purposes as part of academic coursework.
