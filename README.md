# Number-guessing-game
i develop a number guessing code by java programming
import java.util.Random;
import java.util.Scanner;

public class numberGame {

        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);
            Random random = new Random();
            int maxAttempts = 5;
            int round = 1;
            int score = 0;

            System.out.println("Welcome to the Number Guessing Game!");

            while (true) {
                int numberToGuess = random.nextInt(100) + 1; // Generate a random number between 1 and 100
                int attemptsLeft = maxAttempts;

                System.out.println("\n--- Round " + round + " ---");
                System.out.println("I have generated a number between 1 and 100. Can you guess it?");

                boolean hasWon = false;
                while (attemptsLeft > 0) {
                    System.out.println("You have " + attemptsLeft + " attempts left. Enter your guess:");
                    int userGuess = scanner.nextInt();

                    if (userGuess == numberToGuess) {
                        System.out.println("Congratulations! You've guessed the correct number.");
                        hasWon = true;
                        score += attemptsLeft;
                        break;
                    } else if (userGuess < numberToGuess) {
                        System.out.println("Your guess is too low.");
                    } else {
                        System.out.println("Your guess is too high.");
                    }

                    attemptsLeft--;
                }

                if (!hasWon) {
                    System.out.println("Sorry, you've run out of attempts. The correct number was " + numberToGuess + ".");
                }

                System.out.println("Your current score: " + score);

                System.out.println("Do you want to play another round? (yes/no)");
                scanner.nextLine(); // Consume newline
                String playAgain = scanner.nextLine();

                if (!playAgain.equalsIgnoreCase("yes")) {
                    System.out.println("Thank you for playing! Your final score is: " + score);
                    break;
                }

                round++;
            }

            scanner.close();
        }
    }


