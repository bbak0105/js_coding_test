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

let min = arr.reduce((acc, curr) => Math.min(acc, curr));
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

### 3. 나머지

<br/> 

두 자연수 A와 B가 있을때 A%B는 A를 B로 나눈 나머지이다. <br/>
예를들어, 7, 14, 27, 38를 3으로 나눈 나머지는 1, 2, 0, 2 이다. <br/>
수 10개를 입력받은 뒤, 이를 42로 나눈 나머지를 구한다. <br/>
그 다음 서로 다른 값이 몇 개 있는지 출력하는 프로그램을 작성하시오. 

<br/>

* 첫째 줄에, 42로 나누었을 때 서로 다른 나머지가 몇 개 있는지 출력한다.

<br/>

```javaScript

/* const fs = require('fs'); */
/* const input = fs.readFileSync('/dev/stdin').toString().split("\n"); */

const input = "1\n2\n3\n4\n5\n6\n7\n8\n9\n10";
const arr = input.split("\n").map((n) => Number(n) % 42);

const set = new Set(arr).size;
console.log(set);

```

<br/>

----

<br/>

### 4. 평균은 넘겠지

<br/>

첫째 줄에는 테스트 케이스의 개수 C가 주어진다.
둘째줄 부터 각 테스트 케이스마다 학생의 수가 첫수로 주어지고, 이어서 N명의 점수가 나온다.
각 케이스마다 한줄씩 평균을 넘는 학생들의 비율을 반올림하여 소숫점 셋째자리까지 출력한다. 

<br/>

> 내가 푼 방법

```javaScript

// const fs = require('fs');
// const input = fs.readFileSync('/dev/shin').split(" ").toString();

const input =
  "5\n5 50 50 70 80 100" +
  "\n7 100 95 90 80 70 60 50" +
  "\n3 70 90 80" +
  "\n3 70 90 81" +
  "\n9 100 99 98 97 96 95 94 93 91";

const inputSplit = input.split("\n");
const n = inputSplit[0];
inputSplit.shift();

for (let i = 0; i < n; i++) {
  const arr = inputSplit[i].split(" ").map(Number);
  const n = arr[0];
  arr.shift();

  const sum = arr.reduce((curr, accu) => {
    return curr + accu;
  });

  const avg = sum / n;

  let flag = 0;

  arr.forEach((item) => {
    if (item > avg) {
      flag++;
    }
  });

  console.log(((flag / n) * 100).toFixed(3) + "%");
}

```

<br/>

> 풀이랑 조금 달랐던 점!

```

나는 array 함수를 쓰느라고 shift()를 사용했지만,
풀이에서는 for문을 주로 써서 초기값을 1로 주는 방식으로 많이 사용함.
풀이랑 그렇게 많이 다르지 않아서 그냥 생략

근데 그냥 막쓸때는 몰랐는데 toFixed가 애초에 반올림을 해주는 것이
디폴트라서 Math.round를 쓰지 않고 toFixed만 써도 됨;

```
