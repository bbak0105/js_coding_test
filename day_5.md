<b> 🐰 2023.07.12 공부시간 1시간 🐰 </b>

<br/>

# [5강] 문자열 기본 

<br/>

### 1. 문자열 반복

<br/>

* 문제 <br/>
문자열 S를 입력받은 후에, 각 문자를 R번 반복해 새 문자열 P를 만든 후 출력하는 프로그램을 작성하시오. 즉, 첫 번째 문자를 R번 반복하고, 두 번째 문자를 R번 반복하는 식으로 P를 만들면 된다. S에는 QR Code "alphanumeric" 문자만 들어있다. <br/> QR Code "alphanumeric" 문자는 0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ\$%*+-./: 이다.

<br/>

* 입력 <br/>
첫째 줄에 테스트 케이스의 개수 T(1 ≤ T ≤ 1,000)가 주어진다. 각 테스트 케이스는 반복 횟수 R(1 ≤ R ≤ 8), 문자열 S가 공백으로 구분되어 주어진다. S의 길이는 적어도 1이며, 20글자를 넘지 않는다. 

<br/>

* 예제 입력 <br/>
2 <br/>
3 ABC <br/>
5 /HTP <br/>

* 예제 출력 <br/>
AAABBBCCC <br/>
/////HHHHHTTTTTPPPPP

<br/> 

> 내가 푼 방법 

```javaScript

const input = "2\n3 ABC\n5 /HTP".toString().split("\n");
const n = input[0];

for(let i=1; i<=n; i++) {
	const arr = input[i].split(" ");
	
	const count = Number(arr[0]);
	let result = "";
	
	arr[1].split("").forEach(item => {
		result += item.repeat(count);
	});
	
	console.log(result);
}

```

<br/>

> 풀이 (아니근데.. 왜 jsfiddle에서 안돌아가지..?)

```javaScript

let testCase = Number(input[0]);

for (let i=1; i<=testCase; i++) {
    let [r, s] = input[i].split(" ");
    let result = "";

    for (let j=0; i<=s.length; j++) {
        result += s.chartAt(j).repeat(r);
    }

    console.log(result);
}

```

<br/>

----

<br/>

### 2. 거꾸로 뒤집은 뒤에 더 큰 값 찾기

<br/> 

* 입력 <br/> 
첫째 줄에 상근이가 칠판에 적은 두 수 A와 B가 주어진다. 두 수는 같지 않은 세 자리 수이며, 0이 포함되어 있지 않다.

<br/> 

* 출력 <br/> 
첫째 줄에 상수의 대답을 출력한다.

<br/> 

* 예제입/출력 <br/> 
734 893 => 437 <br/> 
221 231 => 132

<br/> 

> 내가 푼 방법
```javaScript

const input = '734 893'.split(" ");

input.reduce((curr, accu) => {
	const currReverse = Number(curr.split("").reverse().join(""));
	const accuReverse = Number(accu.split("").reverse().join(""));

	console.log(Math.max(currReverse, accuReverse))
});

```

<br/>

> 풀이

```javaScript

const input = '734 893'.split("\n");

let a = input[0].split(' ')[0];
let b = input[0].split(' ')[1];

let newA = a[2] + a[1] + a[0];
let newB = b[2] + b[1] + b[0];

console.log(Math.max(Number(newA), Number(newB)));

```

<br/>

----

<br/>

### 3. 그룹 단어 체커 (졸려서 내일)

<br/> 

* 문제 <br/> 
그룹 단어란 단어에 존재하는 모든 문자에 대해서, 각 문자가 연속해서 나타나는 경우만을 말한다. 예를 들면, ccazzzzbb는 c, a, z, b가 모두 연속해서 나타나고, kin도 k, i, n이 연속해서 나타나기 때문에 그룹 단어이지만, aabbbccb는 b가 떨어져서 나타나기 때문에 그룹 단어가 아니다.
단어 N개를 입력으로 받아 그룹 단어의 개수를 출력하는 프로그램을 작성하시오.

<br/> 

* 입력 <br/> 
첫째 줄에 단어의 개수 N이 들어온다. N은 100보다 작거나 같은 자연수이다. 둘째 줄부터 N개의 줄에 단어가 들어온다. 단어는 알파벳 소문자로만 되어있고 중복되지 않으며, 길이는 최대 100이다.

<br/> 

* 출력 <br/> 
첫째 줄에 그룹 단어의 개수를 출력한다.

<br/> 

* 예제 입/출력 <br/> 
3 <br/> 
happy <br/> 
new <br/> 
year

<br/>

* 예제 입/출력 <br/> 
9 <br/> 
aaa <br/> 
aaazbz <br/> 
babb <br/> 
aazz <br/> 
azbz <br/> 
aabbaa <br/> 
abacc <br/> 
aba <br/> 
zzaz 

> 내가 푼 방법

```javaScript

const input = "9\naaa\naaazbz\nbabb\naazz\nazbz\naabbaa\nabacc\naba\nzzaz".split('\n');
input.shift(); // 첫 번째 그냥 날려버리기
let count = 0;

for(let i=0; i<input.length; i++) {
	// 약간 여기서 꼼수..ㅋㅋ 리듀스 한번 더 돌기위해서 띄어쓰기함
	const item = input[i]+" ";  
	const arr = [];
	
	item.split("").reduce((curr, accu) => {
		// 같은 애들 넘기고 다를 경우 curr를 arr로 추가해줌
		// 그러면 연속된 애들 무시하고 aaabba => ['a','b','a'] 처럼 담김 
		if(curr !== accu) arr.push(curr);
		return accu;
	});
	
	const compareCount = new Set(arr).size;
	if(arr.length === compareCount) count++;
}

console.log(count);

```

> 풀이

```javaScript

function check(data) {
	let setData = new Set(data[0]);

	for(let i=0; i<data.length-1; i++) {
		// 오른쪽 단어와 다르다면 
		if(data[i] != data[i+1]) {
			// 이미 등장한 적 있는 알파벳이라면 
			if(setData.has(data[i+1])) {
				return false;
			} else {
				// 등장한적이 없다면 더해줌
				setData.add(data[i+1]);
			}
		}
	}

	return true;
}

let fs = require("fs");
let input = fs.readFileSync("/dev/stdin").toString().split("\n");

let n = Number(input[0]);
let summary = 0;

for (let i=1; i<=n; i++) {
	let data = input[i];
	if (check(data)) summary += 1;
}

console.log(summary);

```