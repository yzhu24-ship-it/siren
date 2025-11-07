# 🌙 Rusty Lake Mystery - The Black Cube

A web-based point-and-click puzzle adventure game inspired by the classic Rusty Lake series.

## 🎮 Game Overview

You awaken to find yourself in a mysterious Victorian-era room. The room is filled with eerie atmosphere and unsolved mysteries. Your goal is to find the legendary **Black Cube** to escape this enigmatic place.

## ✨ Key Features

### Visual & Progressive Gameplay
- **Visual Progress Tracker**: See your quest progress with an animated step-by-step indicator
- **Tutorial System**: Context-sensitive hints that guide you through each puzzle
- **Visual Cues**: Highlighted items and pulsing buttons show you what to do next
- **Achievement Notifications**: Satisfying pop-up notifications when you solve puzzles
- **Interaction Counter**: Track how many times you've examined each item
- **Progressive Difficulty**: Puzzles unlock sequentially for a guided experience

### Atmosphere & Design
- **Victorian Gothic Style**: Immersive dark aesthetic with period-appropriate design
- **Mystery Events**: Random atmospheric events enhance immersion
- **Smooth Animations**: Fluid transitions and visual feedback
- **Responsive Design**: Works on desktop and mobile devices

### Game Systems
- **Item Collection**: Find and use key items to progress
- **Chained Puzzles**: 4 interconnected puzzles that must be solved in order
- **Save/Load System**: LocalStorage-based progress saving
- **Statistics Tracking**: Monitor items, puzzles, and interactions

## 🎯 How to Play

### Basic Controls

1. **Examine Items**: Click on item buttons to investigate them
2. **Collect Items**: Some items reveal key objects after multiple examinations
3. **Use Items**: Click "Use" buttons in your inventory to employ collected items
4. **Wait for Events**: Click "Wait..." to trigger random mystery events
5. **Save Progress**: Use Save/Load buttons to preserve your game state

### Visual Guidance System

The game provides multiple visual cues to guide you:

- **Progress Tracker**: Shows your current step (1-4) with visual indicators
  - **Active Step**: Glowing gold circle with pulse animation
  - **Completed Step**: Green circle with checkmark
  - **Progress Bar**: Fills as you complete puzzles

- **Tutorial Box**: Updates with each step, providing:
  - Current objective description
  - Specific hint for what to do next
  - Context-sensitive guidance

- **Item Highlights**: Items you need to interact with glow
- **Pulsing Buttons**: "Use" buttons pulse when they're needed
- **New Item Animation**: Collected items appear with special effects

### Puzzle Walkthrough

The game has 4 sequential puzzles:

#### 1️⃣ Step 1: Find the Key
**Objective**: Discover the hidden key in the portrait

- Look for the **Mysterious Portrait**  (highlighted with glowing border)
- Click it **3 times** to reveal its secret
- Watch the interaction counter to track your progress
- On the 3rd click, obtain the **Old Key**
- Achievement unlocked: "First Clue Found!"

#### 2️⃣ Step 2: Unlock the Desk
**Objective**: Use the key to open the locked desk

- Find the **Old Key** in your inventory
- Click the **"Use"** button (it will be pulsing)
- The desk drawer opens automatically
- Obtain the **Precision Gear**
- Achievement unlocked: "Desk Unlocked!"

#### 3️⃣ Step 3: Repair the Clock
**Objective**: Fix the broken clock with the gear

- Use the **Precision Gear** from your inventory (pulsing button)
- The clock springs to life!
- A hidden compartment reveals the **Faded Note**
- The note displays the code: **376**
- Achievement unlocked: "Clock Repaired!"

#### 4️⃣ Step 4: Open the Cabinet
**Objective**: Enter the code to unlock the mysterious cabinet

- Use the **Faded Note** from your inventory
- Enter the code: **376** when prompted
- The cabinet opens with an eerie glow
- Obtain the **Mysterious Black Cube**
- Achievement unlocked: "The Black Cube!"

#### 🎉 Victory!
- The Black Cube is yours!
- Victory modal appears
- Game complete!

## 🔍 Room Items

### Puzzle Items (Required for Completion)
- 🖼️ **Mysterious Portrait**: Hides the key (requires 3 examinations)
- 📚 **Old Desk**: Locked drawer containing the gear (needs key)
- 🕰️ **Antique Clock**: Broken mechanism (needs gear to repair)
- 🗄️ **Mysterious Cabinet**: Code-locked (needs password 376)

### Atmospheric Items (Optional Exploration)
- 🪞 **Ancient Mirror**: Reveals strange reflections
- 🪟 **Window**: Foggy view with mysterious shapes
- 📖 **Bookshelf**: Ancient tomes with cryptic messages
- 🔥 **Fireplace**: Long-extinguished with hidden marks

## 💻 Technical Features

### Architecture
- **Object-Oriented JavaScript**: Clean `RustyLakeGame` class structure
- **State Management**: Comprehensive tracking of items, puzzles, and progress
- **Event System**: Responsive UI updates with smooth animations
- **Data Persistence**: LocalStorage integration for save/load

### Code Structure
```javascript
class RustyLakeGame {
  // Core data structures
  - items: Object          // Room items with states and interactions
  - inventory: Array       // Player's collected items
  - puzzleStates: Object   // Puzzle completion tracking
  - gameState: Object      // Overall game progress
  - tutorialMessages: Object // Step-by-step guidance

  // Key methods
  - examineItem()         // Inspect and interact with items
  - useItem()            // Use inventory items to solve puzzles
  - updateProgress()     // Update visual progress tracker
  - updateTutorial()     // Show context-sensitive hints
  - showAchievement()    // Display achievement notifications
  - saveGame/loadGame()  // Persistence methods
}
```

### Visual Features
- CSS3 animations and transitions
- Gradient backgrounds and shadows
- Responsive grid layouts
- Custom scrollbars
- Keyframe animations for:
  - Progress indicator pulse
  - Item highlights
  - Achievement slides
  - Modal pop-ups
  - New item appearances

## 🚀 Running the Game

1. Clone or download the repository
```bash
git clone <repository-url>
cd siren
```

2. Open `index.html` directly in your browser

**No dependencies, no build process, no installation required!**

Simply double-click the HTML file or open it in any modern web browser.

## 📋 System Requirements

- **Browser**: Modern browser with ES6+ support (Chrome, Firefox, Safari, Edge)
- **Screen**: 1280x720 resolution or higher recommended
- **Storage**: LocalStorage enabled for save functionality
- **JavaScript**: Must be enabled

## 🎮 Gameplay Tips

### For Beginners
1. **Follow the Tutorial**: The tutorial box tells you exactly what to do
2. **Watch the Highlights**: Glowing items and pulsing buttons show the way
3. **Check Progress**: The tracker at the top shows which step you're on
4. **Read Everything**: Item descriptions contain important clues
5. **Use Save Often**: Don't lose your progress!

### For Explorers
1. **Examine Everything**: All items have unique descriptions
2. **Multiple Clicks**: Some items reveal more with repeated examination
3. **Try Random Events**: The "Wait..." button adds atmosphere
4. **Read the Log**: Event log contains all messages and clues
5. **Find Easter Eggs**: Atmospheric items have interesting lore

### Common Questions

**Q: I'm stuck! What do I do?**
- Check the tutorial box for your current objective
- Look for highlighted or pulsing elements
- Review the progress tracker to see your current step
- Examine the portrait 3 times to get started

**Q: How do I use items?**
- Find items in your inventory (right panel)
- Click the "Use" button next to the item
- Pulsing buttons indicate which item to use next

**Q: What's the cabinet code?**
- Repair the clock first (steps 1-3)
- The code appears on the Faded Note
- Enter: **376**

**Q: Can I skip puzzles?**
- No, puzzles must be solved in order (1 → 2 → 3 → 4)
- This ensures a guided, story-driven experience

## 🎨 Design Inspiration

This game pays homage to the acclaimed Rusty Lake series, celebrating their:
- Mysterious and eerie atmosphere
- Clever interconnected puzzle design
- Surrealist narrative style
- Memorable visual presentation
- Point-and-click adventure mechanics

## 📝 Changelog

### Version 2.0.0 - Enhanced Edition
- ✅ **NEW**: Visual progress tracker with step indicators
- ✅ **NEW**: Context-sensitive tutorial system
- ✅ **NEW**: Item highlighting and visual cues
- ✅ **NEW**: Pulsing "Use" buttons for guidance
- ✅ **NEW**: Achievement notification system
- ✅ **NEW**: Interaction counter badges on items
- ✅ **NEW**: New item appearance animations
- ✅ **NEW**: Enhanced statistics (added interaction count)
- ✅ **IMPROVED**: More intuitive progressive gameplay
- ✅ **IMPROVED**: Better visual feedback throughout
- ✅ **IMPROVED**: Smoother animations and transitions
- ✅ **UPDATED**: Full English localization

### Version 1.0.0 - Initial Release
- ✅ Core game logic and puzzle system
- ✅ 4 chained puzzles
- ✅ 8 interactive room items
- ✅ Random mystery event system
- ✅ Save/load functionality
- ✅ Victory condition detection
- ✅ Victorian Gothic UI styling

## 🤝 Contributing

Suggestions and improvements are welcome!

## 📄 License

This project is for educational and entertainment purposes only.

---

**"Memory is a strange thing - it is both the key and the cage."**

*Enjoy your journey through Rusty Lake... 🌙*

---

## Quick Start Summary

1. **Open** `index.html` in your browser
2. **Follow** the glowing portrait hint
3. **Click** the Mysterious Portrait **3 times**
4. **Use** each item in your inventory as you find them
5. **Enter code** 376 when prompted
6. **Find** the Black Cube and win!

The tutorial system will guide you every step of the way! 🎓
