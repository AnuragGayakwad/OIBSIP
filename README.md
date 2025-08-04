# OIBSIP
Created a number guessing game with limit between 1 to 200.

import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGameConsole {

    public static void main(String[] args) {
        final int MAX_ATTEMPTS = 10;
        final int MAX_SCORE = 100;
        int attempts = 0;
        int score = 0;

        Random rand = new Random();
        int numberToGuess = rand.nextInt(200) + 1;

        boolean hasGuessedCorrectly = false;
        Scanner scanner = new Scanner(System.in);

        System.out.println("Hii We Welcome you to the Number Guessing Game!");
        System.out.println("Have a good game..");
        System.out.println("Guess a number between 1 to 200.");
        System.out.println("You have " + MAX_ATTEMPTS + " attempts.\n");

        while (attempts < MAX_ATTEMPTS && !hasGuessedCorrectly) {
            System.out.print("Attempt " + (attempts + 1) + ": Enter your guess: ");

            int userGuess;
            try {
                userGuess = Integer.parseInt(scanner.nextLine());
            } catch (NumberFormatException e) {
                System.out.println("Oops! you guessed incorrect number. Please guess the correct number.\n");
                continue;
            }

            if (userGuess < 1 || userGuess > 200) {
                System.out.println("Please enter a number between 1 and 200.\n");
                continue;
            }

            attempts++;

            if (userGuess == numberToGuess) {
                hasGuessedCorrectly = true;
                score = MAX_SCORE - (attempts - 1) * 5;
                if (score < 0) score = 0;
                System.out.println("\nCorrect! You guessed the number in " + attempts + " attempts.");
                System.out.println("Your score: " + score);
            } else if (userGuess < numberToGuess) {
                System.out.println("Too low! Try again.\n");
            } else {
                System.out.println("Too high! Try again.\n");
            }
        }

        if (!hasGuessedCorrectly) {
            System.out.println("\nYou've used all " + MAX_ATTEMPTS + " attempts.");
            System.out.println("The correct number was: " + numberToGuess);
            System.out.println("Better luck next time!");
        }

        scanner.close();
    }
}
