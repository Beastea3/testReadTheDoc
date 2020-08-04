# Regular Expression

## LookAround: Lookbehind / Lookahead

There are 4 pattern operators in this category:

**Positive lookahead**: Matches a group after the main expression without including the result;

**Negative lookahead**: Specifies a group that can not match after the main expression (if it matches, the result is discarded);

**Positive lookbehind**: Matches a group before the main expression without including the result;

**Negative lookabehind**: Specifies a group that can not match before the main expression (if it matches, the result is discarded);

> **Warning**: lookbehind may not be supported by some browsers like Safari and most browsers on mobile devices;

### Eg: Remove invalid chars in A number string

```js
numStr.replace(/[^0-9\-.]|(?!^)-|\.(?=.*\.)/g, '');
```

`[^0-9\-.]` matches all chars which are not numbers, decimal points or minus signs;

`(?!^)-` matches all minus signs which are not at the start of the string;

`\.(?=.*\.)` matches all decimal points which are not the last decimal point;

Sounds like there will be a `lookaround`, could be useful in the future, though it can also be accomplished by binding `lookbehind` and `lookahead`;
