<b> 🐰 2023.07.10 공부시간 40분 🐰 </b>

<br/>

### 1. 최대/최소
<br/>

첫 번째 줄에 정수의 개수가 주어진다. 둘째 줄에는 N개의 정수를 공백으로 구분해서 주어진다.

<br/> 


> 풀이

```javaScript

// [1]. 첫 번째 풀이
// const fs = require("fs");
// const input = fs.readFileSync().split(" ").toString();


const input = "5\n20 10 35 30 7".split("\n");
const n = Number(input[0]);
const arr = input[1].split(" ").map(Number);

let min = 1000001;  // 큰 수로 초기화
let max = -1000001; // 작은 수로 초기화

for(let i=0; i<n; i++) {
	if(min > arr[i]) min = arr[i];
	if(max < arr[i]) max = arr[i];
}

console.log(min, max)


// [2]. 두 번째 풀이
// const fs = require("fs");
// const input = fs.readFileSync().split(" ").toString();

const input = "5\n20 10 35 30 7".split("\n");
const n = Number(input[0]);
const arr = input[1].split(" ").map(Number);

let min = arr.reduce((acc, curr, index) => Math.min(acc, curr));
let max = arr.reduce((acc, curr) => Math.max(acc, curr));

console.log(min, max);


```

<br/>

----

<br/>

### 2. 위에랑 똑같은데 인덱스 찾는거

<br/> 

```javaScript

// const fs = require("fs");
// const input = fs.readFileSync().split(" ").toString();

const input = "5\n20 10 35 30 7".split("\n");
const n = Number(input[0]);
const arr = input[1].split(" ").map(Number);

let min = arr.reduce((acc, curr) => Math.min(acc, curr));
let max = arr.reduce((acc, curr) => Math.max(acc, curr));

console.log('minIndex', arr.indexOf(min));
console.log('maxnIndex', arr.indexOf(max));

```

<br/>

> <b>💡💡💡 굳이 리듀스 안쓰고 이렇게 가능</b>
```javaScript

console.log('Max', Math.max(...arr))
console.log('Min', Math.min(...arr))

```

<br/>

----

<br/>

### 3. 졸려서 내일,,,,,,ㅠ

<br/> 