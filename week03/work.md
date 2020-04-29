```js
const convertStringToNumber = (string, hex = 10) => {
  const chars = string.split('');
  let number = 0;

  let i = 0;
  while (i < chars.length && chars[i] !== '.') {
    number = number * hex;
    number += chars[i].codePointAt(0) - '0'.codePointAt(0);
    i++;
  }

  if (chars[i] === '.') {
    i++;
  }

  let fraction = 1;
  while (i < chars.length) {
    fraction = fraction / hex;
    number += (chars[i].codePointAt(0) - '0'.codePointAt(0)) * fraction;
    i++;
  }

  return number;
}
```


```js
const convertNumberToString = (number, radix) => {
  let integer = Math.floor(number);
  let fraction = String(number).match(/\.\d+$/);
  if (fraction) {
    fraction = fraction[0].replace('.', '');
  }
  let string = '';
  while (integer > 0) {
    string = String(integer % radix) + string;
    integer = Math.floor(integer / radix);
  }
  return fraction ? `${string}.${fraction}` : string;
}
```