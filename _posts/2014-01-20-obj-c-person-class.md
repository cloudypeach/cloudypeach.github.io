---
title: Objective C Person Class
layout: codepost
excerpt: "Objective C Person Class"
---
##Main.m
{% highlight objc %}
//
//  main.m
//  PeopleDatabase
//
//  Created by Fahim Farook on 15/7/13.
//  Copyright (c) 2013 Fahim Farook. All rights reserved.
//

#import <Foundation/Foundation.h>
#import "Person.h"

int main(int argc, const char * argv[])
{

	@autoreleasepool {
		char response;
		NSMutableArray *people = [[NSMutableArray alloc] init];
		
		do {
			Person *newPerson = [[Person alloc] init];
			[newPerson enterInfo];
			[newPerson printInfo];
			[people addObject:newPerson];
			
			NSLog(@"Do you want to enter another name? (y/n)");
			scanf("\n%c", &response);
		} while(response == 'y');
		NSLog(@"Number of people in the database: %li", [people count]);
		for (Person *onePerson in people) {
			[onePerson printInfo];
		}
	}
    return 0;
}
{% endhighlight %}
##Person.h
{% highlight objc %}
//  Person.h
//  PeopleDatabase
//
//  Created by Fahim Farook on 15/7/13.
//  Copyright (c) 2013 Fahim Farook. All rights reserved.
//

#import <Foundation/Foundation.h>
//interface: defines methods and attributes
@interface Person : NSObject {
	NSString *firstName;
	NSString *lastName;
	int age;
}
//method signatures
- (void)enterInfo;
- (void)printInfo;

@end
{% endhighlight %}
##Person.m
{% highlight objc %}
//
//  Person.m
//  PeopleDatabase
//
//  Created by Fahim Farook on 15/7/13.
//  Copyright (c) 2013 Fahim Farook. All rights reserved.
//

#import "Person.h"

@implementation Person

- (void)enterInfo {
    NSLog(@"What is the first name?");
    char cstring[40];
    scanf("%s", cstring);
    
    firstName = [NSString stringWithCString:cstring encoding:1];
	
	NSLog(@"What is %@'s last name?",firstName);
	scanf("%s",cstring);
	lastName = [NSString stringWithCString:cstring encoding:1];
	
	NSLog(@"How old is %@ %@?", firstName, lastName);
	scanf("%i", &age);
	
}

- (void)printInfo {
    NSLog(@"%@ %@ is %i years old", firstName, lastName, age);
}

@end
{% endhighlight %}