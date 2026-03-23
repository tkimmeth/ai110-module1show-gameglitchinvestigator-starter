# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
  The game looked fine. It tells me the # of guesses I have and prompts me to guess a number between 1-100 (medium). There is a submit, new game, & show hint button. There is also a title called "Game Glitch Investigator".

- List at least two concrete bugs you noticed at the start  
   (for example: "the secret number kept changing" or "the hints were backwards").
  -> The hints were wrong. When submitting 56 for Secret 57, it told me to "📉 Go LOWER!"
  -> Also the New Game button (does not work) only works if there has been 0 guesses. (This was fixed later, my browser did not allow the site to store so this caused the "secret to stay the same". Later, thanks to instruction, I was able to understand the error better.)
  -> The indexing is wrong for attempts shown as "allowed" vs actually allowed

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
  -> ChatGPT but not for finding the bugs. Only to help find where these mehtods are being called in the code. Then when I found some errors, I gave the code and described the errors.

- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
  -> It told me to look at the numbers and ensure they were correct (I.E. testing for numbers out of the 1-100 bound or Attempts allowed vs Attempts left). I then did that and found that these both caused innacuracies. It was off by one because :

        if "attempts" not in st.session_state:
            st.session_state.attempts = 1 #i just swapped to 0 to fix it

  but the UI says... causing a mismatch

        Attempts left: {attempt_limit - st.session_state.attempts}

- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

It told me to click new game after I failed guessing one of the numbers. This led me to find that the new game button did not work correct. It also told me a set of Input Validation tests but some of these did not create errors such as 16+1 was not read as 17.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
  -> Some bugs were easier to solve than others, but I just used my intuition and test cases to try to reproduce an error in a previously "bad section of code". For example, I tried to do a number of different input validation tests.

- Describe at least one test you ran (manual or using pytest) and what it showed you about your code.

- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
