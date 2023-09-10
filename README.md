# Hangman-Game
# Example code: Hangman Game
import random

def choose_word():
    words = ["python", "programming", "hangman", "challenge", "developer"]
    return random.choice(words)

def display_word(word, guessed_letters):
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter
        else:
            display += "_"
    return display

word_to_guess = choose_word()
guessed_letters = []
attempts = 6

while attempts > 0:
    print("Word:", display_word(word_to_guess, guessed_letters))
    guess = input("Guess a letter: ").lower()

    if guess in guessed_letters:
        print("You've already guessed that letter.")
    elif guess in word_to_guess:
        guessed_letters.append(guess)
        if word_to_guess == display_word(word_to_guess, guessed_letters):
            print(f"Congratulations! You guessed the word: {word_to_guess}")
            break
    else:
        guessed_letters.append(guess)
        attempts -= 1
        print(f"Wrong guess! You have {attempts} attempts left.")

if attempts == 0:
    print(f"Out of attempts. The word was: {word_to_guess}")
