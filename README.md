# Objective-C_Style_Guide
=======================

这是我个人的 Objective-C Code Style.

## 快速预览
=======================
### 一个类应该长什么样子
Person.h
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

@property (nonatomic, copy)   NSString      *name;
@property (nonatomic, assign) PersonGender  gender;

- (BOOL)isEqualToPerson:(Person *)another;

@end
```

Person.m
```
#import "Person.h"

@implementation Person

#pragma mark - Memory

- (void)dealloc {
	[_name release];
	[super dealloc];
}

#pragma mark - NSCopying

- (id)copyWithZone:(NSZone *)zone {
	Person *copy = [[Person alloc] init];
	copy.gender = self.gender;
	copy.name = self.name;

	return copy;
}

#pragma mark - Public

- (BOOL)isEqualToPerson:(Person *)another {
	if (self == _another)
		return YES;

	return NO;
}

@end
```

## 仔细说说
### 方法名的规范
- Public 方法名一定小写字母开头

	```
	// Elegant Style
	+ (void)classMethod;
	- (void)instanceMethod;
	
	// Ugly Style
	+ (void)ClassMethod;
	- (void)InstanceMethod;
	```

- Private 方法名一定 _ 开头
- 方法中小心使用 get 开头的字样
- 命名不要使用缩写（专有名次除外）

### 几个方法名的例子
