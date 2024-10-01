package samu123;
import java.util.Random;
import java.util.Scanner;
public class numberdemo {

	    public static void main(String[] args) {
	        Scanner scanner = new Scanner(System.in);
	        boolean playAgain = true;
	        int totalScore = 0;
	        int roundsWon = 0;
	        
	        System.out.println("Welcome to the Number Guessing Game!");
	        
	        // Loop for multiple rounds
	        while (playAgain) {
	            int roundScore = playGame(scanner); // Play one round and get the score for that round
	            totalScore += roundScore;
	            
	            if (roundScore > 0) {
	                roundsWon++;
	            }
	            
	            System.out.print("Do you want to play again? (yes/no): ");
	            String userResponse = scanner.next();
	            playAgain = userResponse.equalsIgnoreCase("yes");
	        }
	        
	        // Display final score
	        System.out.println("Thanks for playing!");
	        System.out.println("You won " + roundsWon + " round(s).");
	        System.out.println("Your total score is: " + totalScore);
	        
	        scanner.close();
	    }

	    // Method to play one round of the game
	    public static int playGame(Scanner scanner) {
	        Random random = new Random();
	        int randomNumber = random.nextInt(100) + 1; // Random number between 1 and 100
	        int maxAttempts = 5; // Limit the number of attempts
	        int numberOfTries = 0; 
	        int score = 100; // Base score, decreases with attempts
	        boolean hasGuessedCorrectly = false;
	        
	        System.out.println("I'm thinking of a number between 1 and 100.");
	        System.out.println("You have " + maxAttempts + " attempts to guess it.");
	        
	        // Loop for guessing
	        while (!hasGuessedCorrectly && numberOfTries < maxAttempts) {
	            System.out.print("Enter your guess: ");
	            int guess = scanner.nextInt();
	            numberOfTries++;
	            
	            // Check the user's guess
	            if (guess < randomNumber) {
	                System.out.println("Too low! Try again.");
	            } else if (guess > randomNumber) {
	                System.out.println("Too high! Try again.");
	            } else {
	                hasGuessedCorrectly = true;
	                System.out.println("Congratulations! You guessed the number in " + numberOfTries + " tries.");
	                score -= (numberOfTries - 1) * 10; // Decrease score based on attempts
	            }
	        }
	        
	        // If the player runs out of attempts
	        if (!hasGuessedCorrectly) {
	            System.out.println("Sorry, you've run out of attempts. The number was: " + randomNumber);
	            score = 0; // No points if they didn't guess the number
	        }

	        return score;
	    }
	
	}
