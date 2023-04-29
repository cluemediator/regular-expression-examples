# Regular Expressions Examples: A Comprehensive List

> Thank you for checking out this project! If you find it useful, please consider giving it a star ⭐. Pull requests are always welcome and greatly appreciated. For more technical updates, follow us on Twitter [@ClueMediator](https://twitter.com/cluemediator).


**Note:** This repository is dedicated to showcasing JavaScript Regular Expression examples only. If you're interested in more technical content, please visit [Clue Mediator's GitHub profile](https://github.com/cluemediator).


### Quick Guide

```
\	// the escape character - used to find an instance of a metacharacter like a period, brackets, etc.
.	// match any character except newline
x	// match any instance of x
^x	// match any character except x
[x]	// match any instance of x in the bracketed range - [abxyz] will match any instance of a, b, x, y, or z
|	// an OR operator - [x|y] will match an instance of x or y
()	// used to group sequences of characters or matches
{}	// used to define numeric quantifiers
{x}	// match must occur exactly x times
{x,}	// match must occur at least x times
{x,y}	// match must occur at least x times, but no more than y times
?	// preceding match is optional or one only, same as {0,1}
*	// find 0 or more of preceding match, same as {0,}
+	// find 1 or more of preceding match, same as {1,}
^	// match the beginning of the line
$	// match the end of a line

[:alpha:]	// Represents an alphabetic character. Use [:alpha:]+ to find one of them.
[:digit:]	// Represents a decimal digit. Use [:digit:]+ to find one of them.
[:alnum:]	// Represents an alphanumeric character ([:alpha:] and [:digit:]).
[:space:]	// Represents a space character (but not other whitespace characters).
[:print:]	// Represents a printable character.
[:cntrl:]	// Represents a nonprinting character.
[:lower:]	// Represents a lowercase character if Match case is selected in Options.
[:upper:]	// Represents an uppercase character if Match case is selected in Options.

\d	// matches a digit, same as [0-9]
\D	// matches a non-digit, same as [^0-9]
\s	// matches a whitespace character (space, tab, newline, etc.)
\S	// matches a non-whitespace character
\w	// matches a word character
\W	// matches a non-word character
\b	// matches a word-boundary (NOTE: within a class, matches a backspace)
\B	// matches a non-wordboundary
```


### Table of Contents

- [Email Address](#email-address)
- **Number**
    - [Number](#number)
    - [Number for 10 digit](#number-for-10-digit)
    - [Allow symbols in number](#allow-symbols-in-number)
- [URL](#url)
- [Percentage](#percentage)
- [Username (Alphanumeric with underscore)](#username-alphanumeric-with-underscore)
- [Password (At least 8 characters, one uppercase, one lowercase, one digit, and one special character)](#password-at-least-8-characters-one-uppercase-one-lowercase-one-digit-and-one-special-character)
- [Phone Number (US)](#phone-number-us)
- [ZIP Code (US)](#zip-code-us)
- [Hexadecimal Color Code (3 or 6 digits)](#hexadecimal-color-code-3-or-6-digits)
- [IP Address (IPv4)](#ip-address-ipv4)
- **Date & Time**
    - [Date (YYYY-MM-DD)](#date-yyyy-mm-dd)
    - [24 Hour Time (hh:mm)](#24-hour-time-hhmm)
- **Card Validation**
    - [Card CVV](#card-cvv)
    - [Credit Card Expiration Date (MM/YYYY)](#credit-card-expiration-date-mmyyyy)
    - [Credit Card Expiry Date (MM/YY)](#credit-card-expiry-date-mmyy)
    - [Credit Card Number (Visa, Mastercard, American Express, Discover)](#credit-card-number-visa-mastercard-american-express-discover)
    - [Amex Card Number](#amex-card-number)
    - [BCGlobal Card Number](#bcglobal-card-number)
    - [Carte Blanche Card Number](#carte-blanche-card-number)
    - [Diners Club Card Number](#diners-club-card-number)
    - [Discover Card Number](#discover-card-number)
    - [Insta Payment Card Number](#insta-payment-card-number)
    - [JCB Card Number](#jcb-card-number)
    - [Korean Local Card Number](#korean-local-card-number)
    - [Laser Card Number](#laser-card-number)
    - [Maestro Card Number](#maestro-card-number)
    - [Master Card Number](#master-card-number)
    - [Solo Card Number](#solo-card-number)
    - [Switch Card Number](#switch-card-number)
    - [Union Pay Card Number](#union-pay-card-number)
    - [Visa Card Number](#visa-card-number)
    - [Visa Master Card Number](#visa-master-card-number)


## Regular Expression with Example


- ### Email Address

    RegEx: **`^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,3}$`**

    ```javascript
    const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,3}$/;
    console.log(emailRegex.test('example@example.com')); // true
    console.log(emailRegex.test('example@.com')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Number

    RegEx: **`^[0-9]*$`**

    ```javascript
    const numberRegex = /^[0-9]*$/;
    console.log(numberRegex.test('abc')); // false
    console.log(numberRegex.test('012345')); // true
    console.log(numberRegex.test('0123456789')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Number for 10 digit

    RegEx: **`^[0-9]{10}$`**

    ```javascript
    const number10Regex = /^[0-9]{10}$/;
    console.log(number10Regex.test('abc')); // false
    console.log(number10Regex.test('012345')); // false
    console.log(number10Regex.test('0123456789')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Allow symbols in number 

    Allow symbols: `-,+,(,)`

    RegEx: **`^(?=.*[0-9])[- +()0-9]{10,14}$`**

    ```javascript
    const symbolsNumberRegex = /^(?=.*[0-9])[- +()0-9]{10,14}$/;
    console.log(symbolsNumberRegex.test('(999) 999-9999')); // true
    console.log(symbolsNumberRegex.test('(999) 999-99.99')); // false
    console.log(symbolsNumberRegex.test('56789')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### URL

    RegEx: **`^(?:http(s)?:\/\/)?[\w.-]+(?:\.[\w\.-]+)+[\w\-\._~:/?#[\]@!\$&'\(\)\*\+,;=.]+$`**

    ```javascript
    const urlRegex = /^(?:http(s)?:\/\/)?[\w.-]+(?:\.[\w\.-]+)+[\w\-\._~:/?#[\]@!\$&'\(\)\*\+,;=.]+$/;
    console.log(urlRegex.test('https://example.com')); // true
    console.log(urlRegex.test('example.com')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Percentage

    RegEx: **`^((\d{0,2}(\.\d{1,4})?)|100)$`**

    ```javascript
    const percentageRegex = /^((\d{0,2}(\.\d{1,4})?)|100)$/;
    console.log(percentageRegex.test('67.22')); // true
    console.log(percentageRegex.test('999')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Username (Alphanumeric with underscore)

    RegEx: **`^[a-zA-Z0-9_]+$`**

    ```javascript
    const usernameRegex = /^[a-zA-Z0-9_]+$/;
    console.log(usernameRegex.test('user_123')); // true
    console.log(usernameRegex.test('user@123')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Password (At least 8 characters, one uppercase, one lowercase, one digit, and one special character)

    RegEx: **`^(?=.[a-z])(?=.[A-Z])(?=.\d)(?=.[@$!%?&])[A-Za-z\d@$!%?&]{8,}$`**

    ```javascript
    const passwordRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/;
    console.log(passwordRegex.test('Password123!')); // true
    console.log(passwordRegex.test('password123')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Phone Number (US)

    RegEx: **`^(\d{3}-\d{3}-\d{4}|\d{10})$`**

    ```javascript
    const phoneRegex = /^(\d{3}-\d{3}-\d{4}|\d{10})$/;
    console.log(phoneRegex.test('123-456-7890')); // true
    console.log(phoneRegex.test('1234567890')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### ZIP Code (US)

    RegEx: **`^\d{5}$|^\d{5}-\d{4}$`**

    ```javascript
    const zipCodeRegex = /^\d{5}$|^\d{5}-\d{4}$/;
    console.log(zipCodeRegex.test('12345')); // true
    console.log(zipCodeRegex.test('12345-6789')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Hexadecimal Color Code (3 or 6 digits)

    RegEx: **`^#([A-Fa-f0-9]{6}|[A-Fa-f0-9]{3})$`**

    ```javascript
    const colorCodeRegex = /^#([A-Fa-f0-9]{6}|[A-Fa-f0-9]{3})$/;
    console.log(colorCodeRegex.test('#FFA500')); // true
    console.log(colorCodeRegex.test('#ABC')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### IP Address (IPv4)

    RegEx: **`^(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$`**

    ```javascript
    const ipv4Regex = /^(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$/;
    console.log(ipv4Regex.test('192.168.0.1')); // true
    console.log(ipv4Regex.test('256.0.0.0')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Date (YYYY-MM-DD)

    RegEx: **`^(\d{4})-(\d{2})-(\d{2})$`**

    ```javascript
    const dateRegex = /^(\d{4})-(\d{2})-(\d{2})$/;
    console.log(dateRegex.test('2022-04-25')); // true
    console.log(dateRegex.test('22-04-25')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### 24 Hour Time (hh:mm)

    RegEx: **`^(0[0-9]|1[0-9]|2[0-3]):[0-5][0-9]$`**

    ```javascript
    const timeRegex = /^(0[0-9]|1[0-9]|2[0-3]):[0-5][0-9]$/;
    console.log(timeRegex.test('23:59')); // true
    console.log(timeRegex.test('24:59')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Card CVV

    RegEx: **`^[0-9]{3,4}$`**

    ```javascript
    const cardCVVRegex = /^[0-9]{3,4}$/;
    console.log(cardCVVRegex.test('123')); // true
    console.log(cardCVVRegex.test('1234')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Credit Card Expiration Date (MM/YYYY)

    RegEx: **`^(0[1-9]|1[0-2])\/(20)\d{2}$`**

    ```javascript
    const expirationDateRegex = /^(0[1-9]|1[0-2])\/(20)\d{2}$/;
    console.log(expirationDateRegex.test('06/2022')); // true
    console.log(expirationDateRegex.test('13/2022')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Credit Card Expiry Date (MM/YY)

    RegEx: **`(0[1-9]|10|11|12)\/[0-9]{2}|\.`**

    ```javascript
    const expiryDateRegex = /(0[1-9]|10|11|12)\/[0-9]{2}|\./;
    console.log(expiryDateRegex.test('06/22')); // true
    console.log(expiryDateRegex.test('13/23')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Credit Card Number (Visa, Mastercard, American Express, Discover)

    RegEx: **`^(?:4[0-9]{12}(?:[0-9]{3})?|[25][1-7][0-9]{14}|6(?:011|5[0-9][0-9])[0-9]{12}|3[47][0-9]{13}|3(?:0[0-5]|[68][0-9])[0-9]{11}|(?:2131|1800|35\d{3})\d{11})$`**

    ```javascript
    const creditCardRegex = /^(?:4[0-9]{12}(?:[0-9]{3})?|[25][1-7][0-9]{14}|6(?:011|5[0-9][0-9])[0-9]{12}|3[47][0-9]{13}|3(?:0[0-5]|[68][0-9])[0-9]{11}|(?:2131|1800|35\d{3})\d{11})$/;
    console.log(creditCardRegex.test('4111111111111111')); // true
    console.log(creditCardRegex.test('6011123456789011')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Amex Card Number

    RegEx: **`^3[47][0-9]{13}$`**

    ```javascript
    const amexCardRegex = /^3[47][0-9]{13}$/;
    console.log(amexCardRegex.test('377400111111115')); // true
    console.log(amexCardRegex.test('376000000000006')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### BCGlobal Card Number

    RegEx: **`^(6541|6556)[0-9]{12}$`**

    ```javascript
    const bcglobalCardRegex = /^(6541|6556)[0-9]{12}$/;
    console.log(bcglobalCardRegex.test('6556123456789012')); // true
    console.log(bcglobalCardRegex.test('6556123456789006')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Carte Blanche Card Number

    RegEx: **`^389[0-9]{11}$`**

    ```javascript
    const carteBlancheCardRegex = /^389[0-9]{11}$/;
    console.log(carteBlancheCardRegex.test('38912345678909')); // true
    console.log(carteBlancheCardRegex.test('30569309025904')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Diners Club Card Number

    RegEx: **`^3(?:0[0-5]|[68][0-9])[0-9]{11}$`**

    ```javascript
    const dinersClubCardRegex = /^3(?:0[0-5]|[68][0-9])[0-9]{11}$/;
    console.log(dinersClubCardRegex.test('30569309025904')); // true
    console.log(dinersClubCardRegex.test('38520000023237')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Discover Card Number

    RegEx: **`^65[4-9][0-9]{13}|64[4-9][0-9]{13}|6011[0-9]{12}|(622(?:12[6-9]|1[3-9][0-9]|[2-8][0-9][0-9]|9[01][0-9]|92[0-5])[0-9]{10})$`**

    ```javascript
    const discoverCardRegex = /^65[4-9][0-9]{13}|64[4-9][0-9]{13}|6011[0-9]{12}|(622(?:12[6-9]|1[3-9][0-9]|[2-8][0-9][0-9]|9[01][0-9]|92[0-5])[0-9]{10})$/;
    console.log(discoverCardRegex.test('6011111111111117')); // true
    console.log(discoverCardRegex.test('6011000990139424')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Insta Payment Card Number

    RegEx: **`^63[7-9][0-9]{13}$`**

    ```javascript
    const instaPaymentCardRegex = /^63[7-9][0-9]{13}$/;
    console.log(instaPaymentCardRegex.test('6377820200251698')); // true
    console.log(instaPaymentCardRegex.test('6377820200251011')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### JCB Card Number

    RegEx: **`^(?:2131|1800|35\d{3})\d{11}$`**

    ```javascript
    const jcbCardRegex = /^(?:2131|1800|35\d{3})\d{11}$/;
    console.log(jcbCardRegex.test('3566000020000410')); // true
    console.log(jcbCardRegex.test('3530111333300000')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Korean Local Card Number

    RegEx: **`^9[0-9]{15}$`**

    ```javascript
    const koreanLocalCardRegex = /^9[0-9]{15}$/;
    console.log(koreanLocalCardRegex.test('9111111111111111')); // true
    console.log(koreanLocalCardRegex.test('9011123456789011')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Laser Card Number

    RegEx: **`^(6304|6706|6709|6771)[0-9]{12,15}$`**

    ```javascript
    const laserCardRegex = /^(6304|6706|6709|6771)[0-9]{12,15}$/;
    console.log(laserCardRegex.test('6304111111111111')); // true
    console.log(laserCardRegex.test('6709123456789011')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Maestro Card Number

    RegEx: **`^(5018|5020|5038|6304|6759|6761|6763)[0-9]{8,15}$`**

    ```javascript
    const maestroCardRegex = /^(5018|5020|5038|6304|6759|6761|6763)[0-9]{8,15}$/;
    console.log(maestroCardRegex.test('5018111111111111')); // true
    console.log(maestroCardRegex.test('6759123456789011')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Master Card Number

    RegEx: **`^(5[1-5][0-9]{14}|2(22[1-9][0-9]{12}|2[3-9][0-9]{13}|[3-6][0-9]{14}|7[0-1][0-9]{13}|720[0-9]{12}))$`**

    ```javascript
    const masterCardRegex = /^(5[1-5][0-9]{14}|2(22[1-9][0-9]{12}|2[3-9][0-9]{13}|[3-6][0-9]{14}|7[0-1][0-9]{13}|720[0-9]{12}))$/;
    console.log(masterCardRegex.test('5425233430109903')); // true
    console.log(masterCardRegex.test('2223000048410010')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Solo Card Number

    RegEx: **`^(6334|6767)[0-9]{12}|(6334|6767)[0-9]{14}|(6334|6767)[0-9]{15}$`**

    ```javascript
    const soloCardRegex = /^(6334|6767)[0-9]{12}|(6334|6767)[0-9]{14}|(6334|6767)[0-9]{15}$/;
    console.log(soloCardRegex.test('6334101999990016')); // true
    console.log(soloCardRegex.test('6767123456789011')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Switch Card Number

    RegEx: **`^(4903|4905|4911|4936|6333|6759)[0-9]{12}|(4903|4905|4911|4936|6333|6759)[0-9]{14}|(4903|4905|4911|4936|6333|6759)[0-9]{15}|564182[0-9]{10}|564182[0-9]{12}|564182[0-9]{13}|633110[0-9]{10}|633110[0-9]{12}|633110[0-9]{13}$`**

    ```javascript
    const switchCardRegex = /^(4903|4905|4911|4936|6333|6759)[0-9]{12}|(4903|4905|4911|4936|6333|6759)[0-9]{14}|(4903|4905|4911|4936|6333|6759)[0-9]{15}|564182[0-9]{10}|564182[0-9]{12}|564182[0-9]{13}|633110[0-9]{10}|633110[0-9]{12}|633110[0-9]{13}$/;
    console.log(switchCardRegex.test('6331101999990016')); // true
    console.log(switchCardRegex.test('6011123456789011')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Union Pay Card Number

    RegEx: **`^(62[0-9]{14,17})$`**

    ```javascript
    const unionPayCardRegex = /^(62[0-9]{14,17})$/;
    console.log(unionPayCardRegex.test('6292270001349812')); // true
    console.log(unionPayCardRegex.test('629227000134981211')); // true
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Visa Card Number

    RegEx: **`^4[0-9]{12}(?:[0-9]{3})?$`**

    ```javascript
    const visaCardRegex = /^4[0-9]{12}(?:[0-9]{3})?$/;
    console.log(visaCardRegex.test('4111111111111111')); // true
    console.log(visaCardRegex.test('6011123456789011')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


- ### Visa Master Card Number

    RegEx: **`^(?:4[0-9]{12}(?:[0-9]{3})?|5[1-5][0-9]{14})$`**

    ```javascript
    const visaMasterCardRegex = /^(?:4[0-9]{12}(?:[0-9]{3})?|5[1-5][0-9]{14})$/;
    console.log(visaMasterCardRegex.test('4111111111111111')); // true
    console.log(visaMasterCardRegex.test('6011123456789011')); // false
    ```

    **[⬆ Back to Top](#table-of-contents)**


---

### **Happy Coding...!! 😊**
