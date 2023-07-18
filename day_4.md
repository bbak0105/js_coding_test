<b> 🐰 2023.07.10~2023.07.11 공부시간 1시간 30분 🐰 </b>

<br/>

# [4강] 배열 기본 

<br/>

### 1. 최대/최소

<br/>

첫 번째 줄에 정수의 개수가 주어진다. 둘째 줄에는 N개의 정수를 공백으로 구분해서 주어진다.

<br/> 


> 풀이

```javaScript

// [1]. 첫 번째 풀이
// const fs = require("fs");
// const input = fs.readFileSync().toString().split("\n");

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
// const input = fs.readFileSync().toString().split("\n");

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
// const input = fs.readFileSync().toString().split("\n");

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
// const input = fs.readFileSync('/dev/shin').toString().split("\n");

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
<br/>

----

<br/>

### 5. 평균
https://www.acmicpc.net/problem/1546

<br/>

* 문제 <br/>
세준이는 기말고사를 망쳤다. 세준이는 점수를 조작해서 집에 가져가기로 했다. 일단 세준이는 자기 점수 중에 최댓값을 골랐다. 이 값을 M이라고 한다. 그리고 나서 모든 점수를 점수/M * 100으로 고쳤다. <br/> 예를 들어, 세준이의 최고점이 70이고, 수학점수가 50이었으면 수학점수는 50/70*100이 되어 71.43점이 된다. <br/> 세준이의 성적을 위의 방법대로 새로 계산했을 때, 새로운 평균을 구하는 프로그램을 작성하시오.

<br/>

* 입력 <br/> 첫째 줄에 시험 본 과목의 개수 N이 주어진다. 이 값은 1000보다 작거나 같다. 둘째 줄에 세준이의 현재 성적이 주어진다. 이 값은 100보다 작거나 같은 음이 아닌 정수이고, 적어도 하나의 값은 0보다 크다. <br/>

<br/>

* 출력 <br/>
첫째 줄에 새로운 평균을 출력한다. 실제 정답과 출력값의 절대오차 또는 상대오차가 10-2 이하이면 정답이다.

<br/>

* 예제입력 <br/>
9 <br/>
10 20 30 40 50 60 70 80 90

* 예제출력 <br/>
55.55555555555556

<br/>

> 내가 푼 방법

```javaScript

// const fs = require('fs');
// const input = fs.readFileSync('dev/shin').toString().split("\n");
// const input = "9\n10 20 30 40 50 60 70 80 90".split("\n");
// const input = "4\n10 20 0 100".split("\n");

const input = "3\n10 20 30".split("\n");
const n = Number(input[0]);
const arr = input[1].split(" ").map(Number);
const max = Math.max(...arr);

const newArr = arr.map((item, index) => {
	return (item/max)*100;
});

const sum = newArr.reduce((curr, accu) => curr + accu);

console.log(Number(sum/n));

```