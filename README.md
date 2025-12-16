# Dungeon Crawler - Android Game

A turn-based dungeon crawler game for Android, built with Java in Android Studio. Explore procedurally generated levels, battle monsters, manage health and potions, level up your character, and aim for the high score!

This was my software engineering capstone project — a complete mobile game demonstrating game logic, UI controls, player progression, and clean Android architecture.

## Download & Play

**Latest APK**: [Download Dungeon Crawler APK](dungeon-crawler.apk) (~50 MB)

**Requirements**:
- Android 12+ (API 31+)
- 50 MB free storage
- Allow "Install from unknown sources" (one-time setting)

**Installation**:
1. Download the APK from the link above.
2. Open the file on your device.
3. Follow the prompts to install.

## How to Play

### Home Screen
- View your highest and recent scores.
- Tap **Start Game** to begin.
- Tap **Help** for instructions.

### Gameplay
- **Player**: Blue circle — move using on-screen directional buttons.
- **Monsters**: Red circles — battles start automatically on contact.
- **HP Bar** (green): Track your health. Use potions to heal (up to 4).
- **XP Bar** (yellow): Gain XP from battles to level up and improve stats.
- **Camera**: Pinch to zoom (1x–3x), drag to pan.
- **UI Toggle**: Tap the screen to show/hide controls (auto-hides after 3 seconds).

### Winning & Game Over
- Clear all monsters on a level to advance.
- Game ends if HP reaches 0 — submit your score to the leaderboard.

### Tips
- Plan moves carefully to avoid fighting multiple monsters at once.
- Save potions for when HP is critically low.
- Level up to gain better stats and more potions.


## Developer Guide (For Contributors or Reviewers)

### Prerequisites
- Android Studio 2023.2.1 or later
- JDK 17
- Android SDK API 36

### Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/Itsyourboy13/dungeon-crawler-android.git
   cd dungeon-crawler-android
   
2. Open the project in Android Studio
3. Sync Gradle and build the project

### Running Tests
- Unit tests are in `PlayerTest.java`
- Run `PlayerTest.java` to verify some of the core logic

### Building the APK
- Build → Build Bundle(s) / APK(s) → Build APK

## Tech & Features Demonstrated
- Java Android development
- Custom views (DungeonView)
- Game loop and turn-based mechanics
- Player progression (XP, leveling, potions)
- Touch controls (directional buttons, pinch zoom, drag pan)
- Score tracking and UI auto-hide
- Clean architecture with tests

## NOTES
This game was developed as a capstone project. The source code is shared for portfolio and learning purposes.
Feel free to explore the code, run the game, or reach out with feedback!
Thanks for playing!