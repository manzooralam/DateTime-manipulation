# DateTime-manipulation
 
 (See more about )[https://www.toptal.com/software/definitive-guide-to-datetime-manipulation]
 
 ## DateTime Libraries:
  You can find a reliable date library for both the front-end and the back-end to do most of the heavy lifting for you.
  
   If you are sending and receiving data through a REST API, you will eventually need to convert the date to a string and vice versa because JSON doesn’t have a native data structure to represent DateTime. 
   
 ## so now we disscuss in javascript:
 
 > Standardizing the Time:
  A DateTime is a very specific point in time. Let’s think about this. As I scribble this article, the clock on my laptop shows July 21      1:29 PM. This is what we call “local time”, the time that I see on wall clocks around me and on my wrist watch.
  
  > Standardizing the Format:
  Standardizing the time is wonderful because I only need to store the UTC time 
  
   if I know a user’s local time and know their timezone, I can convert that to UTC.
   
   <a href="https://ibb.co/BfJvkKr"><img src="https://i.ibb.co/BfJvkKr/time.png" alt="time" border="0"></a>
   
   For 00:00 or UTC, we use “Z” instead, which means Zulu time, another name for UTC.
   
   
 ## Date Manipulation and Arithmetic in JavaScript:
 
  > Date Object:
  
  ` var currentDate = new Date(); // get current date `
  If you don’t pass anything to the Date constructor, the date object returned contains the current date and time.
  
  > You can then format it to extract only the date part as follows::
  
  ```
  var currentDate = new Date();

var date = currentDate.getDate();
var month = currentDate.getMonth(); //Be careful! January is 0 not 1
var year = currentDate.getFullYear();

var dateString = date + "-" +(month + 1) + "-" + year;
```

> Getting the Current Timestamp:

If you instead want to get the current timestamp, you can create a new Date object and use the getTime() method.
```
var date = new Date();
var timestamp = date.getTime();
```
### Note:
In JavaScript, a timestamp is the number of milliseconds that have passed since January 1, 1970.

## Parsing a Date:
Converting a string to a JavaScript date object is done in different ways.

```
var date = new Date("Wed, 27 July 2016 13:30:00");
var date = new Date("Wed, 27 July 2016 07:45:00 GMT");
var date = new Date("27 July 2016 13:30:00 GMT+05:45");
```

## Formatting a Date:

Date formatting is tougher in Javascript because it doesn’t have standard date formatting functions like strftime in Python or PHP.
 
 > best to extract individual bits using the JavaScript functions
 
 ```
 var currentDate = new Date();
var date = currentDate.getDate();
var month = currentDate.getMonth(); 
var year = currentDate.getFullYear();
```
We can get the date in Month/Date/Year format as
var monthDateYear  = (month+1) + "/" + date + "/" + year;

The problem with this solution is that it can give an inconsistent length to the dates because some months and dates are single-digit and others double-digit

```
function doubleDigit(n) {
    return n<10 ? '0'+n : n;
}
```

Now, we get the correct date in MM/DD/YYYY format using:
` var mmddyyyy = pad(month + 1) + "/" + pad(date) + "/" + year; `

If we want DD-MM-YYYY instead, the process is similar:
` var ddmmyyyy = doubleDigit(date) + "-" + doubleDigit(month + 1) + "-" + year ;`

## Using JavaScript Date Object’s Localization Functions:

```
var today = new Date().toLocaleDateString('en-GB', {  
	day : 'numeric',
	month : 'short',
	year : 'numeric'
})
```
gives us something like  “26 Jul 2016”.

```
var today = new Date().toLocaleDateString(undefined, {
    day: '2-digit',
    month: '2-digit',
    year: 'numeric'
})
```
This outputs “07/26/2016”.

<a href="https://ibb.co/ZS98fGH"><img src="https://i.ibb.co/ZS98fGH/time-t.png" alt="time-t" border="0"></a>


## Reference:

(See)[https://www.toptal.com/software/definitive-guide-to-datetime-manipulation]




 
