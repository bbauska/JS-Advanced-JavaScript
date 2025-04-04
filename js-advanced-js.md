/* The do-while loop */
let numbers = [19, 65, 9, 17, 4, 1, 2, 6, 1, 9, 9, 2, 1];

function sumArray( values ) {
  if ( values.length == 0 ) return 0;
    let sum = 0;
    let i = 0;
    do {
      sum += values[i];
      i += 1;
    } while ( i < values.length );
    console.log( 'The loop was executed ' + i + ' times' );
    return sum;
}

sumArray( numbers );

/* You can create a random number between 1 and 50 using the following code: */
Math.trunc( Math.random() * 50 ) + 1

/* Rewrite the sumArray function using a for loop. Here is the example with the while loop: */
let numbers = [19, 65, 9, 17, 4, 1, 2, 6, 1, 9, 9, 2, 1];

function sumArray( values ) {
  let sum = 0;
  let i = 0;
  while ( i < values.length ) {
    sum += values[i];
    i += 1;
  }
  return sum;
}

sumArray( numbers );

/* Don’t continue reading before you solve this exercise. Please change the while loop into a for loop. */
/* Welcome back! */
/* I hope you liked the exercise. To verify your solution, check this code: */
for ( let i = 0; i < values.length; i += 1 ) {
  sum += values[i];
}

/* This code should go in place of */
let i = 0;
  while ( i < values.length ) {
    sum += values[i];
    i += 1;
  }


/* Let’s simplify the for loop a bit further: you can write i++ or ++i in place of i += 1: */
for ( let i = 0; i < values.length; ++i ) {
  sum += values[i];
}

/* In some programming competitions, people tend to count downwards instead of upwards. The */
/* reason is that computing values.length costs some nanoseconds more than checking if the value */
/* of i is positive: */
for ( let i = values.length - 1; i >= 0; --i ) {
  sum += values[i];
}

/* These wannabe geniuses don’t stop there by the way. They go even further: */
for ( let i = values.length; i; sum += values[--i] );

/* Our next simplification is the for..in loop. Why bother iterating an i variable if a loop can take */
/* care of it for us? */
let values = [19, 65, 9, 17, 4, 1, 2, 6, 1, 9, 9, 2, 1];
let sum = 0;

for ( let i in values ) {
  sum += values[i];
}

console.log( sum );

/* The for..in loop enumerates all the available indices of the values array from 0 to 12 in ascending */
/* order. */
/* I have another simplification for you. What if I said, “why bother using a variable for iteration at */
/* all, if we could enumerate the values of the array?”. In ES6, there is a loop called the for...of loop, */
/* which does exactly that. */

let values = [19, 65, 9, 17, 4, 1, 2, 6, 1, 9, 9, 2, 1];
let sum = 0;

for ( let value of values ) {
  sum += value;
}

console.log( sum );

/* Example: sum every second element of the numbers array: */
let numbers = [19, 65, 9, 17, 4, 1, 2, 6, 1, 9, 9, 2, 1];

function sumArray( values ) {
  let sum = 0;
  for ( let i in values ) {
    if ( i % 2 == 0 ) continue;
    sum += values[i];
  }
  return sum;
}

sumArray( numbers );


