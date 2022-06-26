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
      const pathrname = path + "/" + file.replace(/k/gi, "후");
      fs.rename(pathname, pathrname, (err) => console.log(err));
    });
  }
});
```


정규표현식
---------
