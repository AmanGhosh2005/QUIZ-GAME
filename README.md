#include <stdio.h>
#include <string.h>
#include <conio.h>  // For clrscr() and getch()

#define MAX_QUESTIONS 10

// Structure to hold the question data
struct Question {
    char question[256];
    char options[4][100];
    char answer;
};

// Function to display the question and get the answer
char askQuestion(struct Question q) {
    char response;
    
    printf("%s\n", q.question);
    int i;  // Declare i outside the loop for Turbo C++ compatibility
    for (i = 0; i < 4; i++) {
        printf("%c) %s\n", 'A' + i, q.options[i]);
    }
    
    printf("Your answer (A/B/C/D): ");
    scanf(" %c", &response);
    
    return response;
}

// Function to run the quiz game
void runQuiz(struct Question questions[], int numQuestions) {
    int score = 0;
    int i;  // Declare i outside the loop for Turbo C++ compatibility

    for (i = 0; i < numQuestions; i++) {
        char answer = askQuestion(questions[i]);
        if (answer == questions[i].answer) {
            printf("Correct!\n");
            score++;
        } else {
            printf("Wrong! The correct answer was %c.\n", questions[i].answer);
        }
        printf("\n");
    }

    printf("Your final score: %d out of %d\n", score, numQuestions);
}

int main() {
    struct Question quiz[MAX_QUESTIONS] = {
        {
            "What does CPU stand for?",
            {"Central Process Unit", "Central Processing Unit", "Computer Personal Unit", "Central Processor Unit"},
            'B'
        },
        {
            "Which one is a valid declaration of a pointer?",
            {"int* p;", "int p*;", "pointer p;", "p: int;"},
            'A'
        },
        {
            "What is the main function in C?",
            {"void main()", "int main()", "main()", "main:void()"},
            'B'
        },
        {
            "Which of the following is not an operating system?",
            {"Windows", "Linux", "Mac OS", "Microsoft Office"},
            'D'
        },
        {
            "What is the size of an int in C?",
            {"2 bytes", "4 bytes", "8 bytes", "Depends on the compiler"},
            'D'
        },
        {
            "What does HTML stand for?",
            {"Hyper Text Markup Language", "High Text Markup Language", "Hyper Tool Markup Language", "High Tool Markup Language"},
            'A'
        },
        {
            "Which company developed the Linux operating system?",
            {"Microsoft", "Apple", "IBM", "Linus Torvalds"},
            'D'
        },
        {
            "What is the primary purpose of an operating system?",
            {"To manage computer hardware", "To run applications", "To provide a user interface", "All of the above"},
            'D'
        },
        {
            "Which programming language is known as the mother of all languages?",
            {"Python", "C", "Java", "Pascal"},
            'B'
        },
        {
            "What does RAM stand for?",
            {"Read Access Memory", "Random Access Memory", "Read and Memory", "Rapid Access Memory"},
            'B'
        }
    };
	printf("Welcome to the Computer Quiz Game!\n");
    runQuiz(quiz, MAX_QUESTIONS);
    
    printf("Press any key to exit...");
    getch();
    
    return 0;
}
