# FlashCard Application

A Java + JavaFX desktop flashcard study tool built as an OOP coursework project at BITS Pilani.

**Download pre-built JARs:** [Mac](https://github.com/AG-AGENT47/flashcard-application/releases/download/v1.0/FlashCard-Mac.jar) · [Ubuntu](https://github.com/AG-AGENT47/flashcard-application/releases/download/v1.0/FlashCard-Ubuntu.jar) · [Windows](https://github.com/AG-AGENT47/flashcard-application/releases/download/v1.0/FlashCard-Windows.jar) Supports four card types, a Factory design pattern for card creation, and a full study session (revision) workflow with login, deck management, and category organization.

---

## Features

- **4 card types** — MCQ (Multiple Choice), True/False, Fill-in-the-Blank, and Definition; each is a distinct class extending the abstract `Card` base
- **Factory pattern** — `CardGenerator` decouples card creation from card-type logic; pass a `CardType` enum and get the right card back
- **Full data model** — `User` → `Deck` → `Card` hierarchy with a `Category` classification layer
- **Study session** — `ReviseDeckScene` renders each card interactively and scores the session
- **Edit cards** — dedicated edit scene per card type
- **7 custom exceptions** — dedicated `ExceptionHandling` package covering empty containers, invalid parameters, scene change failures, timer thread errors, and more
- **Scene management** — `SceneHandler` centralizes all JavaFX scene transitions

---

## Project Structure

```
src/main/java/
├── com/example/flashcard/       # JavaFX controllers (one per screen)
│   ├── App.java / Main.java     # Entry points
│   ├── LoginScreenController
│   ├── UserHomeScreenController
│   ├── CategoryScreenController
│   ├── DeckSceneController
│   ├── ReviseDeckSceneController
│   ├── EditCardSceneController
│   ├── CreateMCQCardController
│   ├── CreateTfCardController
│   ├── CreateFIBCardController
│   ├── CreateDefCardController
│   └── SceneHandler
├── models/
│   ├── Card.java                # Abstract base class
│   ├── CardType.java            # Enum: MCQ, TF, FIB, DEF
│   ├── Deck.java
│   ├── Category.java
│   └── cards/                  # Concrete card implementations
│       ├── MCQCard.java
│       ├── TFCard.java
│       ├── FIBCard.java
│       └── DefCard.java
│   └── cardFactory/
│       └── CardGenerator.java  # Factory — creates cards by CardType
├── user/
│   └── User.java
├── services/
│   └── AdminServer.java
└── ExceptionHandling/           # 7 custom exception classes
    ├── containerEmptyException
    ├── containerNotFoundException
    ├── invalidParameterException
    ├── noSelectionException
    ├── notFXMLLoaderInstanceException
    ├── sceneChangeException
    └── timerThreadException

src/main/resources/com/example/flashcard/   # FXML layout files (one per screen)
```

---

## Build and Run

### Prerequisites
- Java 17+
- Maven 3.8+
- JavaFX 19 (pulled automatically via Maven)

### Run
```bash
./mvnw javafx:run
```

### Build JAR
```bash
./mvnw package
java -jar target/FlashCard.jar
```
