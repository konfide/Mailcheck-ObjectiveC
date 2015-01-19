Mailcheck - Objective-C
====================

The Objective-C library that suggests a right domain when your users misspell it in an email address. See the original at https://github.com/mailcheck/mailcheck.

When your user types in "user@hotnail.con", Mailcheck will suggest "user@hotmail.com".

Mailcheck will offer up suggestions for top level domains too, and suggest ".com" when a user types in "user@hotmail.cmo".

Usage
-----

Copy mailcheck.h and mailcheck.m from the Mailcheck folder to your project.

```Objective-C
#import "Mailcheck.h"
NSDictionary *result = [Mailcheck suggest:@"test@hotnail.com"]
```

Result will contain nil if the domain appears to be valid.
Otherwise the suggestion will be a dictionary like this:
```Objective-C
{@"address": @"test",
 @"domain":  @"hotmail.com",
 @"full":    @"test@hotmail.com"}
```

New in 0.2
----------

Now includes a check if the email is valid thanks to https://github.com/NZN/NSString-Email

```Objective-C
#import "Mailcheck.h"
NSDictionary *result = [Mailcheck check:@"test@hotnail.com"]
```

Result will contain keys for "valid" and "suggestion"
```Objective-C
{@"valid": @(YES),
 @"suggestion": {@"address": @"test",
                 @"domain":  @"hotmail.com",
                 @"full":    @"test@hotmail.com"}}
```

Supply your own domain lists:
```Objective-C
NSDictionary *result = [Mailcheck check:@"test@mydomain.co" domains:@[@"mydomain.co"] topLevelDomains:@[@"co"]];
```

Or add to the default list:
```Objective-C
NSDictionary *result = [Mailcheck check:@"test@mydomain.co" extraDomains:@[@"mydomain.co"] extraTopLevelDomains:@[@"co"]];
```

Check the MailcheckDemo or the GHUnit tests in TestMailcheck.m for more usage examples. You can run the tests by loading the demo project and selecting the Tests scheme.

Maintainers
-------

- David Kasper, [@dkasper](http://twitter.com/dkasper). Author.

License
-------

Licensed under the MIT License.
