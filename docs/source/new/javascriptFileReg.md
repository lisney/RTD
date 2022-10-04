파일 시스템
==============

```
import fs from "fs";

// 디렉토리 생성, 제거
// fs.mkdir("생성", (err) => console.log(err));
// fs.rmdir("생성", (err) => console.log(err));

// 파일에 내용 입력
// const file = "text.txt";
// const data = "테스트";
// fs.writeFile(file, data, (err) => console.log(err));//생성, 덮어쓰기
// fs.appendFile(file, "추가", (err) => console.log(err));//내용 추가
// fs.readFile(file, "utf8", (err, data) => {
//   if (err) {
//     console.log(err);
//   } else {
//     console.log(data);
//   }
// });

// 디랙토리 내용 보기
// let path = "C:/Users/3DPrinter/Desktop/HSparts";
// fs.readdir(path, (err, files) => {
//   console.log(files);
// });

// 파일명 변경
// fs.rename(file, "brush.txt", (err) => console.log(err));

//정규표현식
// const test = "가나다가나마";
// const result = test.replace(/가/gi, "후후"); // .replace는 첫번째 문자만 바꾼다. 정규식 플래그 g-global, i-ignoreCase대소문자무시
// console.log(result);

//파일명 일괄 변경
let path = "C:/Users/3DPrinter/Desktop/HSparts";
fs.readdir(path, (err, files) => {
  if (err) {
    console.log("err");
  } else {
    files.filter((file) => {
      const pathname = path + "/" + file;
      // const pathrname = path + "/" + file.replaceAll("a", "후");
      const pathrname = path + "/" + file.replace(/k/gi, "후");// 정규식
      fs.rename(pathname, pathrname, (err) => console.log(err));
    });
  }
});
```


정규표현식
---------

```
const regexp1 = new RegExp("^abc", "gi"); //생성자 함수 방식(표현식,플래그)
const regexp2 = /^abc/gi; //리터럴Literal 방식

const str = "철수야 놀자, 영희야 놀자.";

// console.log(/후자/.exec(str)); // exec 일치하는 하나의 문자열 반환
// console.log(/수야/.exec(str)); // exec 일치하는 하나의 문자열 반환
// console.log(/놀자/i.exec(str)); // i ignoreCase 대소문자구분안함, g 일치하는 모든 문자열 배열로
// console.log(/놀자$/.exec(str)); // 패턴 $ 맨뒤(<-> ^ 맨앞), 놀자 뒤에 '.'은 문자열에 포함된다.
// console.log(/놀자\.$/.exec(str)); // 즉 '놀자.'로 검색해야한다
// console.log(/놀자\./.exec(str));

// console.log(/야 놀자/.test(str)); //일치여부 판별

// console.log(str.match(/놀자/g)); //일치하는 문자열 배열로 반환

console.log(/./gi.exec(str)); // '.' 은 임의의 한 문자를 나타내는 패턴
console.log(/../.exec(str));

// * 반복

const str1 = "이효이 이효이이 이효이이이";

console.log(str1.match(/효이/g)); // '효이'만 매치
console.log(str1.match(/효이이*/g)); // '이...' 패턴 반복 매치(0개도 매치) = 반복 {0,}
console.log(str1.match(/효이이+/g)); // '이...' 패턴 반복 매치(1개이상 매치되는 것만) =  {1,}
console.log(str1.match(/효이이리?/g)); //'리' 무반복 매치(0,1개 있으면 매치) = {1}

console.log(str1.match(/효이이{2}/g)); // {2} '이'가 두 번 반복되는 것만 매치
console.log(str1.match(/(이효이이)+/g)); // (이효이이) 그룹 -'이효이이'가 반복되는 것만 매치

// '\w' - 글자, '\s' - 공백, '\d' - 숫자
console.log(str1.match(/효이\s+/g)); // '효이' 뒤에 공백(\s)이 1개 이상(+) 있는 패턴
```

onChange
------------

```
const selectElement = document.querySelector('.ice-cream');

selectElement.addEventListener('change', (event) => {
  const result = document.querySelector('.result');
  result.textContent = `You like ${event.target.value}`;
});

```

[유튜브 모달](https://codepen.io/captain_yar/full/OJMEmGw)











