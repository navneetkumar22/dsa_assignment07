# PPT - DSA Assignment 07

## Answer 1:
```js
const isIsomorphic = (s, t) => {
    if (s.length !== t.length)
        return false;

    // Each string has to have its own dictionary
    let sDict = new Map();
    let tDict = new Map();

    for (let i = 0; i < s.length; i++) {
        let sc = s[i];
        let tc = t[i];

        // If both dictionaries do not have their respective characters mapped yet, then we should set them
        if (!sDict.has(sc) && !tDict.has(tc)) {
            sDict.set(sc, tc);
            tDict.set(tc, sc);
        }

        // If either char does not match then it is not isomorphic 
        if (sDict.get(sc) !== tc || tDict.get(tc) !== sc) {
            return false;
        }
    }
    return true;
};
```

<br/>

## Answer 2:
```js
const isStrobogrammatic = (num) => {
    const map = {
        6: "9",
        9: "6",
        1: "1",
        0: "0",
        8: "8"
    }
    for (let i = 0; i < num.length / 2; i++) {
        if (num[i] !== map[num[num.length - 1 - i]]) {
            return false;
        }
    }
    return true;
};
```

<br/>

## Answer 3:
```js
const addStrings = (num1, num2) => {
    let i = num1.length - 1;
    let j = num2.length - 1;
    const ans = [];
    for (let c = 0; i >= 0 || j >= 0 || c; --i, --j) {
        c += i < 0 ? 0 : parseInt(num1.charAt(i), 10);
        c += j < 0 ? 0 : parseInt(num2.charAt(j), 10);
        ans.push(c % 10);
        c = Math.floor(c / 10);
    }
    return ans.reverse().join('');
};
```

<br/>

## Answer 4:
```js
const reverseWords = (str) => {
    return str.split(' ').map((word) => word.split('').reverse().join('')).join(' ')
};
```

<br/>

## Answer 5:
```js
const reverseStr = (str, k) => {
    // strings are immutable in javascript - converting to an array will allow in place letter swapping
   
    const a = str.split('');
    
    // loop through the array in 2*k increments
    for (let start = 0; start < a.length; start += 2 * k) {
        let i = start;
        let j = Math.min(start + k - 1, a.length - 1);
        
        // reverse first k characters in current increment
        while (i < j) {
            let tmp = a[i];
            a[i++] = a[j];
            a[j--] = tmp;
        }
    }
    // return a string as the result
    return a.join('');
};
```

<br/>

## Answer 6;
```js
const rotateString = (str, goal) => {
    for (let i = 0; i < str.length; i++) {
        if (str.slice(i) + str.slice(0, i) === goal)
            return true;
    }
    return false;
};
```

<br/>

## Answer 7:
```js
const backspaceCompare = (S, T) => {
    return backSpace(S) === backSpace(T);
};

const backSpace = (str) => {
    const result = []

    for (let i = 0; i < str.length; i++) {
        const char = str.charAt(i);

        if (char !== '#')
            result.push(char);
        else
            result.pop();
    }
    return result.join('');
};
```

<br/>

## Answer 8:
```js
const isStraightLinePossible = (arr) => {
    // First pair of point (x0, y0)
    let x0 = arr[0][0];
    let y0 = arr[0][1];

    // Second pair of point (x1, y1)
    let x1 = arr[1][0];
    let y1 = arr[1][1];

    let dx = x1 - x0;
    let dy = y1 - y0;

    // Loop to iterate over the points
    for (let i = 0; i < arr.length; i++) {
        let x = arr[i][0], y = arr[i][1];

        if (dx * (y - y1) != dy * (x - x1)) {
            return false;
        }
    }
    return true;
};
```