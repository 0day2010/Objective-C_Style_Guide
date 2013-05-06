# Objective-C_Style_Guide
=======================

This is my Objective-C Style Guide. There will be more examples than talk!

## Quicklook
=======================
### What should a Class looks like?
Firstly, Person.h
```
#import <Foundation/Foundation.h>

typdef enum {
	kPersonGenderUnknow = 0,
	kPersonGenderMale,
	kPersonGenderFemale
} PersonGender;

@interface Person : NSObject
<
NSCopying
>

@property (nonatomic, copy) NSString *name;
@property (nonatomic, assign) PersonGender gender;

- (BOOL)isEqualToPerson:(Person *)another;

@end
```

Secondly, Person.m
```
#import "Person.h"

@implementation Person

#pragma mark - Memory

- (void)dealloc {
	[_name release];
	[super dealloc];
}

#pragma mark - Public

- (BOOL)isEqualToPerson:(Person *)another {
	if (self == _another)
		return YES;

	return NO;
}

@end
```