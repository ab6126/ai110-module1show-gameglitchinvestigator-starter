# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

The first time I ran the game, it loaded successfully in Streamlit and displayed a number guessing interface. While testing the game, I noticed several issues. The most obvious bug was that the hint logic appeared to be reversed. For example, when I guessed 25 and the secret number was 97, the game told me to "GO LOWER!" even though the correct hint should have been "GO HIGHER!". I also noticed that the score could become negative after losing. Finally, the game still displayed the input controls after the game was over.

| Input                       | Expected Behavior                                             | Actual Behavior                                                | Console Output / Error |
| --------------------------- | ------------------------------------------------------------- | -------------------------------------------------------------- | ---------------------- |
| Guess 25 when secret was 97 | Game should say "GO HIGHER!"                                  | Game said "GO LOWER!"                                          | none                   |
| Ran out of attempts         | Score should remain non-negative or have a reasonable penalty | Score became -30                                               | none                   |
| Game over state             | User should not be able to continue guessing after losing     | Input field and submit button remained visible after game over | none                   |

---

## 2. How did you use AI as a teammate?

I used ChatGPT throughout this project to help me understand bugs, debug errors, and learn how Streamlit session state works. One suggestion that was correct was moving the helper functions from app.py into logic_utils.py and testing them separately. I verified this by running the Streamlit application and confirming that the game still worked correctly after the refactor. One suggestion that was initially misleading involved the automated tests because the tests expected a different return value from check_guess() than my implementation provided. I verified the issue by reading the test file and comparing it with my code before updating the tests.

---

## 3. Debugging and testing your fixes

I decided a bug was fixed only after testing it manually and checking that the game behaved as expected. For example, after fixing the hint logic, I guessed a number lower than the secret number and confirmed that the game displayed "Go HIGHER!" instead of the incorrect hint. I also used pytest to test the check_guess() function. The tests showed that the function correctly returned winning, too high, and too low outcomes. ChatGPT helped me understand why the tests were failing and how to update them to match the behavior of my code.

---

## 4. What did you learn about Streamlit and state?

I learned that Streamlit reruns the entire script whenever a user interacts with the app, such as clicking a button. Because of this behavior, regular variables can reset every time the page reruns. Session state allows values such as the secret number, score, and attempts to be stored between reruns. I would explain it to a friend by saying that session state works like memory that survives page refreshes and user actions.

---

## 5. Looking ahead: your developer habits

I learned that Streamlit reruns the entire script whenever a user interacts with the app, such as clicking a button. Because of this behavior, regular variables can reset every time the page reruns. Session state allows values such as the secret number, score, and attempts to be stored between reruns. I would explain it to a friend by saying that session state works like memory that survives page refreshes and user actions.
