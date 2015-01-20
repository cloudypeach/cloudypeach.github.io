---
title: Objective-C Guessing Game
layout: codepost
excerpt: "A basic command-line obj-c guessing game"
---
{% highlight objc %}
//
//  main.m
//  My First Project
//
//  creds to http://www.raywenderlich.com/38557/learn-to-code-ios-apps-1-welcome-to-programming
//

#import <Foundation/Foundation.h> //minimum foundational framework for any app

//main method, like in Java
int main(int argc, const char * argv[]) {
    @autoreleasepool {
        //autoreleasepool is used to manage memory
        
        //random examples
        int num = 400;
        num = num + 100;
        NSLog(@"num equals %i", num); //NSLog is the equivalent of console.log() in Javascript, logs text in console
        NSString *name = @"Elana"; //* and @ are weird syntax features denoting the type of object that will follow them
        NSLog(@"%A", name); //%A stands in for String variable
        int x = 10;
        NSString *myString = [NSString stringWithFormat:@"The variable x stores the number %i", x];
        
        //guessing game
        int guess = 0;
        int turn = 0;
        int answer = arc4random() % 100 + 1;  //arc4random() = random number generator
        while (guess != answer) {
            
            turn++;
            
            NSLog(@"Guess #%i: Enter a number between 1 and 100", turn);
            scanf("%i", &guess);
            
            if (guess > answer) {
                NSLog(@"Lower!");
            }
            else if (guess < answer) {
                NSLog(@"Higher!");
            }
            else {
                NSLog(@"Correct! The answer was %i", answer);
            }
        }
        
        NSLog(@"It took you %i tries", turn);
    }
    return 0; //terminates
}
{% endhighlight %}
