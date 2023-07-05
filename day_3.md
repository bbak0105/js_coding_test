<b> 🐰 2023.07.05 공부시간 50분 🐰 </b>

<br/>

### 1. 1부터 n까지의 합

<br/>


```javaScript

/* [1]. for문으로 이용하기 */
let fs = require('fs');
let input = fs.readFileSync('/dev/stdin').toString().split('\n');

// parseInt에 비해서 Number가 더 속도가 빠르다!
let n = Number(input[0]);
let answer = 0;

for(let i=1; i<=n; i++) {
	answer += i;
}

console.log(answer);
// 시간 복잡도는 O(N)이다.


/* [2]. 등차수열 식으로 이용하기 */
let n = Number(input[0]);

console.log(n*(n+1) / 2);

```

<br/>

> <b>💡💡💡 중요 풀이</b>
```javaScript
// parseInt에 비해서 Number가 더 속도가 빠르다!
let n = Number(input[0]);
```

<br/>

----

<br/>

### 2. 별 찍기

<br/> 

너무 쉬운 문제라 대충 적고 넘기기

<br/> 

> 내가 푼 방법 & 풀이
```javaScript

let n = 5;
let star = '*';

// [1]. 내가 푼 방법
for(i=1; i<=5; i++) {
	console.log(star);
	star += '*';
} 

// [2]. 풀이
let result = "";
for (let i=0; i<n; i++) {
    for (let j=0; j<=i; j++) {
        result += "*";
    }
    result += "\n";
}
console.log(result);

```

<br/>

----

<br/>

### 3. 빠르게 출력하기 

<br/> 

첫 줄에 테스트케이스의 개수 T가 주어진다. <br/>
T는 최대 1,000,000 이다. (제한시간 1초) <br/>
두번째 줄부터 n째줄까지 2개의 수가 나오고, 이를 더하는 것을 출력한다.

<br/> 

> 내가 푼 방법
```javaScript

//let fs = require('fs');
//let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let input = '5\n1 1\n12 34\n5 500\n40 60\n1000 1000'.toString().split('\n');
let n = Number(input[0]);
let answer = "";

for(let i=1; i<=n; i++) {
	let [first, second] = input[i].split(' ').map(Number);
	answer += `${first+second}\n`
}

console.log(answer);

```
뭐.. 한꺼번에 출력하는 것은 잘 하긴 했는데 제한시간이 촉박한 상황에서 굳이 map을 써야했나 싶다. 
어차피 2자리 수밖에 없으니 풀이대로 하는 것이 더 빠를 것임. <br/>
그리고 <u>초반에 숫자를 더하고 마지막에 문자열을 더해주면 어차피 문자열로 바뀌기 때문에 템플릿 문자열을 쓸 이유도 없었다.</u>

<br/>

> 풀이

```javaScript

//let fs = require('fs');
//let input = fs.readFileSync('/dev/stdin').toString().split('\n');

let testCase = Number(input[0]);
let answer = '';

for(let t=1; t<=testCase; t++) {
    let data = input[t].split(' ');
    let a = Number(data[0]);
    let b = Number(data[1]);
    answer += a + b + '\n';
}

console.log(answer);

```
