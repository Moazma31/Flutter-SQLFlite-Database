# Flutter-SQLFlite-Database
# RecallIt  — Smart Leitner Spaced Repetition Flashcard App

**RecallIt** is an offline-first mobile application built with **Flutter** and **SQLite (`sqflite`)** designed to help students retain complex academic concepts for the long term. By integrating the scientifically proven **Leitner Spaced Repetition System (SRS)**, the app dynamically schedules flashcard reviews based on user recall performance.

---

##  Key Features

- **5-Box Leitner Spaced Repetition Engine:** Automatically moves flashcards between 5 progression boxes based on self-evaluation (`Remembered` vs. `Forgot`), adjusting review intervals (1, 3, 7, 14, and 30 days).
- **100% Offline Local Storage:** Powered by SQLite (`sqflite`), ensuring all subjects, topics, flashcards, and progress data remain permanently stored on the device without requiring an internet connection.
- **Full CRUD Management:** Easily create, organize, and manage hierarchical study material (`Subjects` → `Topics` → `Flashcards`).
- **Interactive Review & Flip Mode:** Smooth tap-to-flip flashcard interface for active recall practice with real-time progress bars.
- **Gamification & Analytics:** Features a daily study **Streak** tracker, post-quiz performance summaries, and a dedicated Leitner Box distribution overview.
- **11-Screen Architecture:** Clean, modular UI covering Onboarding, Splash, Dashboard, Topics, Card Management, Dedicated Card Creation, Review Quiz, Quiz Results, Statistics, Settings, and an In-App Guide.

---

##  How the Leitner Algorithm Works

Every newly created flashcard starts in **Box 1**. During a review session:
1. **If you remember the answer (`Remembered`):** The card advances to the next higher box, extending its next review interval:
   - **Box 1:** Reviewed every `1 day`
   - **Box 2:** Reviewed every `3 days`
   - **Box 3:** Reviewed every `7 days`
   - **Box 4:** Reviewed every `14 days`
   - **Box 5:** Mastered — reviewed every `30 days`
2. **If you forget the answer (`Forgot`):** The card immediately resets back to **Box 1** for daily reinforcement, regardless of its previous box level.

---

##  Project Architecture & File Structure

```text
lib/
├── main.dart                          # Application entry point & global Material 3 theme
├── database/
│   └── db_helper.dart                 # Singleton SQLite database manager & CRUD queries
├── models/
│   └── recall_models.dart             # Data models (Subject, Topic, FlashCard) with Map serialization
└── screens/
    ├── onboarding_screen.dart         # First-time user introduction to Leitner methodology
    ├── splash_screen.dart             # Animated brand launch screen
    ├── home_screen.dart               # Main dashboard with Subject list & daily Streak badge
    ├── topic_screen.dart              # Topic management & quick-launch quiz triggers
    ├── card_list_screen.dart          # Flashcard repository displaying current Box levels
    ├── add_edit_card_screen.dart      # Dedicated form for creating/editing flashcards
    ├── review_screen.dart             # Core Leitner Quiz engine & interactive card flipper
    ├── quiz_result_screen.dart        # Post-session score & retention summary
    ├── stats_screen.dart              # Visual overview of Leitner Box intervals & mastery stages
    ├── profile_settings_screen.dart   # User profile & app preference toggles
    └── help_screen.dart               # In-app manual explaining Leitner rules
