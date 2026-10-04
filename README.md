# Dungeon Crawler (Android)

A turn-based dungeon crawler I built for Android in Java. Each level is a freshly generated maze. Monsters hunt you through the corridors, and battles are resolved on a separate battle screen. Your best runs are saved to a local leaderboard.

## Features

- **Procedural dungeon generation**: Each level is a 15×15 grid of rooms carved into a maze with a randomised depth-first search, so every room is reachable. The maze is then turned into a graph (Princeton's algs4 `Graph`) that the game logic uses.
- **Fog of war**: You can only see rooms along open corridors within 4 spaces. Rooms you have already discovered stay on the map.
- **Monster AI**: Monsters use breadth-first search (`BreadthFirstPaths`) over the room graph to path toward the player. They chase hard when close and only occasionally move when far away.
- **Turn-based battles**: Running into a monster opens a battle screen with **Attack**, **Potion** and **Flee**. Damage is rolled from each character's attack range and shown with hit animations. Fleeing costs you one monster hit.
- **Player progression**: You earn XP by winning battles. Each level-up recalculates health and attack, raises the XP needed for the next level, and gives you an extra potion. Potions heal 50–75% of max HP.
- **Levels and difficulty**: Clear every monster to finish a level. New levels spawn monsters around your current level. A counter shows how many monsters are left.
- **Leaderboard (Room database)**: At game over you can enter your name and submit your score (highest level reached and enemies killed). The leaderboard can be filtered by local scores, today, this week, this month, this year, or by player name. The home screen shows your highest and most recent scores.
- **Save and restore state**: The dungeon, player, monsters, level and camera state are saved to a `Bundle`, so a game survives screen rotation and other configuration changes.
- **Camera controls**: Pinch to zoom (1×–3×) and drag to pan around the dungeon.
- **UI**: A home screen, a help screen, a new-player prompt, landscape layouts, and level-complete and game-over dialogs.
- **Unit tests**: JUnit 4 and Mockito tests for the `Player` class cover movement validation, the attack damage range, potion healing, XP gain and level-up, and stat recalculation.

## Screenshots

<!-- TODO: add screenshots / GIFs -->
| Home | Dungeon | Battle | Leaderboard |
|------|---------|--------|-------------|
| _coming soon_ | _coming soon_ | _coming soon_ | _coming soon_ |

Design and class diagrams are in the repo: [`dungeonCrawlerDesignDiagram.png`](dungeonCrawlerDesignDiagram.png) and [`dungeonCrawlerClassDiagram.png`](dungeonCrawlerClassDiagram.png).

## Tech Stack

- **Language:** Java (source/target compatibility 11)
- **Platform:** Android SDK, `minSdk 24`, `targetSdk`/`compileSdk 36`
- **Build:** Gradle 8.13 (wrapper), Android Gradle Plugin 8.13, version catalog (`gradle/libs.versions.toml`)
- **Android Jetpack:** Room (persistence), LiveData and ViewModel, Navigation component, ViewBinding, AppCompat, Material Components, ConstraintLayout
- **Graphics:** Custom `View`s drawn on a `Canvas`, with `ScaleGestureDetector` and `GestureDetector` for zoom and pan
- **Algorithms:** [algs4](https://algs4.cs.princeton.edu/) (`Graph`, `BreadthFirstPaths`, `StdRandom`) by Robert Sedgewick and Kevin Wayne
- **Testing:** JUnit 4.13.2, Mockito 5.11.0 (plus AndroidX Test/Espresso set up for instrumented tests)
- **CI:** A GitHub Actions workflow builds a debug APK and publishes it to GitHub Pages

## Getting Started

### Prerequisites

- Android Studio (2023.2.1 or later)
- JDK 17
- Android SDK Platform 36

### Build and run

```bash
git clone https://github.com/Itsyourboy13/dungeon-crawler-android.git
cd dungeon-crawler-android
```

1. Open the folder in Android Studio and let Gradle sync.
2. Choose an emulator or a connected device and press **Run**.

Or from the command line:

```bash
./gradlew assembleDebug        # APK ends up in app/build/outputs/apk/debug/
./gradlew installDebug         # installs on a connected device/emulator
```

You can also download a prebuilt debug APK from the project's GitHub Pages site: https://itsyourboy13.github.io/dungeon-crawler-android/

### Run the tests

```bash
./gradlew test                 # JVM unit tests (PlayerTest, ExampleUnitTest)
./gradlew connectedAndroidTest # instrumented tests (needs a device/emulator)
```

In Android Studio you can also right-click `app/src/test/java/card/andrew/dungeoncrawler/PlayerTest.java` and choose **Run 'PlayerTest'**.

## Project Structure

```
app/src/main/java/card/andrew/dungeoncrawler/
├── AppStartupActivity.java      # Launch entry point
├── HomeActivity.java            # Hosts home / leaderboard / help navigation
├── MainActivity.java            # Game screen: HUD (HP/XP bars, potions, controls)
├── GameView.java                # Game loop, rendering, input, zoom/pan, levels, save/restore
├── DungeonView.java             # Background dungeon rendering
├── Dungeon.java / Room.java     # Maze generation (randomised DFS), room graph, fog of war
├── Direction.java               # Grid directions
├── Character.java               # Shared stats/combat for player and monsters
├── Player.java                  # XP, levelling, potions
├── Monster.java                 # BFS pathfinding toward the player
├── BattleActivity.java          # Turn-based battle screen (attack / potion / flee)
├── GameState.java               # Shares player/monster between screens
├── LevelFinishedFragment.java   # Level-complete dialog
├── GameOverFragment.java        # Game-over dialog + score submission
├── data/                        # Room database, DAO, repository, LeaderboardEntry model
└── ui/
    ├── home/                    # Home screen (high/recent score)
    ├── leaderboard/             # Leaderboard list, filters, name search
    └── help/                    # How-to-play screen
app/src/main/java/edu/princeton/cs/algs4/   # Bundled algs4 classes (GPLv3)
app/src/test/java/card/andrew/dungeoncrawler/  # JUnit/Mockito unit tests
docs: Test plan.docx, User Guide for DungeonCrawler.docx, User Guide for Maintenance.docx
```

## About This Project

I built this as my capstone for my BS in Software Engineering at Western Governors University (WGU). I designed and wrote the game myself, from the maze generation and monster AI to the battle system, the Room leaderboard and the tests. The repo also includes the test plan, user guide and maintenance guide I wrote for it.

## License and Credits

Released under the **GNU General Public License v3.0**. See [LICENSE](LICENSE).

This project includes classes from **algs4** by Robert Sedgewick and Kevin Wayne (*Algorithms, 4th Edition*), which are licensed under GPLv3. See [`app/src/main/java/edu/princeton/cs/algs4/LICENSE`](app/src/main/java/edu/princeton/cs/algs4/LICENSE).
