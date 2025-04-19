# TASK-1Hangman-Game
import random

word_list = ['banana', 'guitar', 'rocket', 'jungle', 'wizard', 'planet']
secret = random.choice(word_list)
used_letters = set()
lives = 6

print("⚔️ Let's play Hangman!")
print("_ " * len(secret))

while lives > 0:
    letter = input("Guess a letter: ").lower()

    if letter in used_letters or not letter.isalpha() or len(letter) != 1:
        print("❗ Pick a new single letter.")
        continue

    used_letters.add(letter)

    if letter not in secret:
        lives -= 1
        print("✖️ Wrong guess! Lives left:", lives)

    current = [ch if ch in used_letters else "_" for ch in secret]
    print(" ".join(current))

    if "_" not in current:
        print("🎉 You guessed it! The word was:", secret)
        break

if "_" in current:
    print("💀 Game over! The word was:", secret)
