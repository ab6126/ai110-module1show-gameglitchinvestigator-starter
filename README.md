# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable.

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: _"How do I keep a variable from resetting in Streamlit when I click a button?"_
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] Describe the game's purpose.
- [ ] Detail which bugs you found.
- [ ] Explain what fixes you applied.

### Game Purpose

The purpose of this game is to let the player guess a randomly generated secret number within a limited number of attempts. The game provides hints after each guess and tracks the player's score.

### Bugs Found

1. The hint logic was reversed. When the player's guess was lower than the secret number, the game incorrectly displayed "Go LOWER!" instead of "Go HIGHER!".
2. A TypeError occurred when the game attempted to compare integers and strings.
3. The game logic functions were located in `app.py` instead of being separated into `logic_utils.py`.
4. Several parts of the game required testing to verify that the logic worked correctly after fixes were applied.

### Fixes Applied

1. Fixed the higher/lower hint logic in the `check_guess()` function.
2. Fixed the type mismatch issue that caused comparison errors.
3. Refactored the game logic functions into `logic_utils.py`.
4. Created and updated automated tests in `tests/test_game_logic.py`.
5. Ran pytest repeatedly and fixed issues until all tests passed successfully.

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. Started a new game and opened the Developer Debug Info panel.
2. The secret number was 49.
3. Entered a guess of 25 and received the hint "Go HIGHER!".
4. Entered a guess of 75 and received the hint "Go LOWER!"
5. Entered a guess of 49.The game displayed "Correct!" and a winning message.
6. The final score was updated correctly, and the game ended successfully.

**Screenshot** _(optional)_: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

$ python -m pytest ============================= test session starts ============================= collected 3 items tests/test_game_logic.py ... ============================== 3 passed ======================================

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
