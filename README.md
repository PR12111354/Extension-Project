# Extension-Project

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;


public class ExtensionProject {

    // Define a helper class to show a question
    private static class Question {
        String text;      // The  question text to display
        boolean answer;   // The corect true/false answer to the question

        // Constructor to create a new question object
        Question(String text, boolean answer) {
            this.text = text;
            this.answer = answer;
        }
    }

    public static void main(String[] args) {

        List<Question> pool = new ArrayList<>();

        // The pool of questions that will be randomly chose n from
        pool.add(new Question("Does Neptune have a greater mass than earth?", true));
        pool.add(new Question("Was the first superbowl in 1968?", false));
        pool.add(new Question("Was Abraham Lincoln the 5th president?", false));
        pool.add(new Question("Are frogs an amphibian?", true));
        pool.add(new Question("Is this Mr. Davissons class?", true));
        pool.add(new Question("is Russia the largest country in the world?", true));
        pool.add(new Question("Was the Iphone first introduced in 2009?", false));
        pool.add(new Question("Was Neil Armstrong the first man on the moon?", true));
        pool.add(new Question("Is precipitation the process of liquid turning into gas?", false));
        pool.add(new Question("Does mars have any moons?", true));
        pool.add(new Question("Is plasma part of the periodic table", false));
        pool.add(new Question("Is grass purple?", false));
        pool.add(new Question("Does an octopus have 3 hearts?", true));
        pool.add(new Question("Does the brain have pain receptors", false));
        pool.add(new Question("Do orange watermelons exist?", false));
        pool.add(new Question("Can elephants jump?", false));
        pool.add(new Question("Does sudan have more pyramids than Egypt?", true));
        pool.add(new Question("Do ants have lungs?", false));
        pool.add(new Question("Do fingers have muscles?", false));
        pool.add(new Question("Do green oranges exist?", true));

        // Randomly shuffle the pool list order so the questions appear in a unique sequence each game
        Collections.shuffle(pool);

        // Scanner instance to capture user keyboard inputs
        Scanner scanner = new Scanner(System.in);
        
        // Counter variable to keep track of the total number of correct answers
        int correct = 0;

        // Loop precisely 10 times to present exactly 10 random trivia questions to the user
        for (int i = 0; i < 10; i++) {
            // Retrieve the question object situated at the current index sequence
            Question q = pool.get(i);
            
            // Print out the question number, the text, and input choices
            System.out.println("Question " + (i + 1) + ": " + q.text + " (y/n)");

            // Variable to hold the user's single character selection
            char input = ' '; 
            
            // Input validation loop: repeatedly prompts user until a valid 'y' or 'n' is given
            while (input != 'y' && input != 'n') {
                // Fetch the user string line input, trim whitespace, and normalize to lowercase
                String response = scanner.nextLine().trim().toLowerCase();
                
                // Ensure the string contains text before isolating the first letter to avoid out of bounds errors
                if (!response.isEmpty()) {
                    input = response.charAt(0); // Capture the leading character
                }
            }

            // Convert the validated character input to a matching boolean value (true if 'y')
            boolean userAnswer = (input == 'y');

            // Compare user response against the true factual answer key value
            if (userAnswer == q.answer) {
                correct++; // Increment correct answer tally on direct matching values
            }
        }

        // Calculate final percentage score
        double percentage = (correct / 10.0) * 100;

        // Output final results
        System.out.println("You got " + correct + " right.");
        System.out.println("Your score: " + (int) percentage + "%");

        // The end
        scanner.close();
    }
}
