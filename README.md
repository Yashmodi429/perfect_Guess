Number Guessing Game

 Description

A simple number guessing game built using Python's `tkinter` library and `Pillow` for image handling. The game generates a random number between 1 and 99, and the player has to guess the number within a limited number of attempts. The game provides hints whether the guess is too high or too low.

Features

- User-Friendly Interface:** Designed with `tkinter` for a straightforward and interactive user experience.
- Background Image:** Custom background image for an enhanced visual appeal.
- Guessing Logic:** Provides hints to help the player guess the number.
- Reset Functionality:** Automatically resets the game once the correct number is guessed.

 Prerequisites

- Python 3.x
- `tkinter` module (usually included with Python)
- `Pillow` library for image handling

 Installation

1. Clone the Repository**

   ```bash
   git clone https://github.com/your-username/number-guessing-game.git
   cd number-guessing-game
   ```

2. Install Pillow Library**

   ```bash
   pip install Pillow
   ```

 Usage

1. Run the Game**

   ```bash
   python perfect_guess.py
   ```

2. Play the Game**

   - Enter your guess in the input box.
   - Click the "Guess" button to submit your guess.
   - Receive hints to guess higher or lower.
   - Win the game by guessing the correct number.

Code Overview

- `perfect_guess.py`**: Main game logic and GUI implementation.

```python
import tkinter as tk
from PIL import Image, ImageTk
import random

class NumberGuessingGame:
    def __init__(self, root):
        self.root = root
        self.root.title("Number Guessing Game")
        self.root.geometry("600x400")
        self.root.resizable(False, False)

        self.number = random.randint(1, 99)
        self.guesses = 0

        # Load the background image
        self.load_background_image()

        # Create GUI elements with enhanced styles
        self.create_widgets()
        self.create_footer()

    def load_background_image(self):
        img_path = "/path/to/your/image/yash.png"  # Update this path as needed
        img = Image.open(img_path)
        self.bg_image = ImageTk.PhotoImage(img)
        self.bg_label = tk.Label(self.root, image=self.bg_image)
        self.bg_label.place(x=0, y=0, relwidth=1, relheight=1)

    def create_widgets(self):
        frame = tk.Frame(self.root, bg='lightblue', bd=10)
        frame.place(relx=0.5, rely=0.5, anchor='center')

        self.instructions = tk.Label(frame, text="Guess the number between 1 and 99", font=('Arial', 16, 'bold'), bg='lightblue', fg='darkblue')
        self.instructions.pack(pady=10)

        self.entry = tk.Entry(frame, font=('Arial', 14), width=10, justify='center', bd=5)
        self.entry.pack(pady=5)

        self.guess_button = tk.Button(frame, text="Guess", command=self.check_guess, font=('Arial', 14, 'bold'), bg='darkgreen', fg='white', bd=5)
        self.guess_button.pack(pady=10)

        self.result_label = tk.Label(frame, text="", font=('Arial', 14, 'italic'), bg='lightblue', fg='darkred')
        self.result_label.pack(pady=10)

    def create_footer(self):
        footer_frame = tk.Frame(self.root, bg='lightblue', bd=5)
        footer_frame.place(relx=0.5, rely=0.95, anchor='center')

        self.footer_label = tk.Label(footer_frame, text="Developed by Yash", font=('Arial', 12, 'italic'), bg='lightblue', fg='darkblue')
        self.footer_label.pack(pady=5)

    def check_guess(self):
        try:
            guess = int(self.entry.get())
            self.guesses += 1
            if guess < self.number:
                self.result_label.config(text="Higher number please")
            elif guess > self.number:
                self.result_label.config(text="Lower number please")
            else:
                self.result_label.config(text=f"Congratulations! You guessed the number {self.number} in {self.guesses} attempts.")
                self.reset_game()
        except ValueError:
            self.result_label.config(text="Please enter a valid number")

    def reset_game(self):
        self.number = random.randint(1, 99)
        self.guesses = 0
        self.entry.delete(0, tk.END)

if __name__ == "__main__":
    root = tk.Tk()
    game = NumberGuessingGame(root)
    root.mainloop()
```

 Contributing

Feel free to fork the repository and submit pull requests with your enhancements or bug fixes. Please adhere to the code style and guidelines.

License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
