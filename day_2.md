<b> 🐰 2023.07.04 공부시간 40분 🐰 </b>

<br/>

# [2강] 입출력 기본 

<br/>

### 1. 세자리수 곱하고 다 곱하기

<br/>

> 내가 푼 방법 (괜히 포문까지..)

```javaScript

let a = 472;
let b = 385;

let arr = b.toString().split("");

for(let i=0; i<arr.length; i++) {
	console.log(a * Number(arr[i]));
} 

console.log(a*b);

```

<br/>

> 풀이

```javaScript

let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let a = input[0]; // 첫번째 3자리수
let b = input[1]; // 두번째 3자리수

let x_1 = b[2]; // 일의 자리
let x_2 = b[1]; // 십의 자리
let x_3 = b[0]; // 백의 자리

console.log(Number(a) * Number(x_1));
console.log(Number(a) * Number(x_2));
console.log(Number(a) * Number(x_3));
console.log(Number(a) * Number(b));

```

<br/>

----

<br/>

### 2. 시간 더하기
<br/> 

첫째 줄에는 현재 시각이 나온다. 현재 시각은 A시 B분이며 두번째 줄에는 이를 더할 C분이 나온다.

<br/> 

> 내가 푼 방법
```javaScript

// let fs = require('fs');
// let input = fs.readFileSync().toString().split('\n');
let input = '17 40 \n80'.split('\n');

let inputArr = input[0].split(' '); // 17 40
let addTime = input[1];             // 80

let hour = inputArr[0];             // 17
let minutes = inputArr[1];          // 40

function getTime(hour, minutes, ovenTime) {
	let takingMinutes = Number(minutes) + Number(ovenTime);
	let value = 0;
	let remain = 0;
	
	if(takingMinutes >= 60) {
		value = parseInt(takingMinutes / 60); // 몫은 parseInt 처리
		remain = takingMinutes % 60;
		
		takingMinutes = remain;
	} 
	
	console.log('시', Number(hour) + value);
	console.log('분', takingMinutes);
} 

getTime(hour, minutes, addTime);

```

<br/>

> 풀이
```javaScript

let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// *** 나름 혁신적
let [a, b] = input[0].split(' ').map(Number); // 정수 형태로 바꾼다
let c = Number(input[1]);

let totalMinute = a * 60 + b + c;
totalMinutes %= 1440;
let hour = parseInt(totalMinute/60);
let minute = totalMinute % 60;

console.log(hour + " " + minute);

```

<br/>

> <b>💡💡💡 중요 풀이</b>
```javaScript
let [a, b] = input[0].split(' ').map(Number);
```

<br/>

----

<br/>

### 3. 주사위 던지기
<br/> 

* 주사위를 총 세 번 던진다. <br/>
첫 번째 줄에 세 번 던진 결과가 나온다. <br/>
같은눈 3개 = 10000 + 같은눈 * 1000 <br/>
같은눈 2개 = 1000 + 같은눈 * 100 <br/>
모두다른눈 = 가장큰눈 * 100

<br/>

> 내가 푼 방법

```javaScript
// let fs = require('fs');
// let input = fs.readFileSync().toString();

let input = '3 6 3';
let niceArr = input.split(" ").map((item) => {
	return Number(item);
}).sort();
let money = 0;

let [first, second, last] = niceArr;

// => first === second && second && last 가 더 간결하고 좋았을 것
if (first === second && second === last && first === last) {
	money = 10000 + (first * 1000);
} else if (first === second || last === second) {
	money = 1000 + (second * 100)
} else {
	money = Math.max(first, second, last) * 100
} 

console.log(money);

```

<br/>

> 풀이
```javaScript

let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let a = Number(input[0].split(' ')[0]);
let b = Number(input[0].split(' ')[1]);
let c = Number(input[0].split(' ')[2]);

// 세 개의 수가 모두 같은 경우
if (a==b && b==c) console.log(10000 + a * 1000);
// 세 개의 수가 전부 같지는 않지만, 두 개의 수가 같은 경우
else if (a==b) console.log(1000 + a * 100);
else if (a==c) console.log(1000 + a * 100);
else if (b==c) console.log(1000 + b * 100);
// 세 개의 수가 전부 다른 경우
else console.log(Math.max(a,b,c)*100);

```

<br/>

> 💡💡💡 중요 풀이
```javaScript
// Before) first === second && second && last 가 더 간결하고 좋았을 것
if (first === second && second === last && first === last) {
	money = 10000 + (first * 1000);
}

// After)
if (first === second && second === last) {
	money = 10000 + (first * 1000);
}
```
