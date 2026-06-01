# 📚 Lessons Learned - Automation Testing

> Ghi chú các bài học, kinh nghiệm, tips & tricks trong quá trình làm automation testing

---

## 🗓️ Tháng 05/2026

### ✅ Lesson #1: Tại sao dùng PlayWright với TypeScript?
**Ưu điểm:**
- Viết code một lần nhưng chạy được trên nhiều trình duyệt/thiết bị
- Cấu hình đơn giản chỉ từ 3 đến 5 dòng code
- Chạy trên tất cả các hệ điều hành phổ biến
- Tính năng xịn: Auto waiting 
- Report đầu đủ, rõ ràng
- Code gen: Thao tác là sinh ra code

**Tại sao học?**
- Dễ cài đặt -> giảm rào cản tiếp cận
- Các cú pháp đơn giản và dễ học

**Giải thích các công cụ:**
- nvm: node version management dùng để quản lý phiên bản code
- NodeJS: Công cụ chạy code
- Git: Quản lý code
- Github: Chia sẻ code và làm việc nhóm
- node_modules: thư viện
- tests: chứa code test
- playwright.config.ts: file cấu hình (quay video, chụp ảnh ...)

---

### ✅ Lesson #2: GIT 1

**Ba trạng thái của GIT**:  
- Working Directory (WD): File mới hoặc file mới có thay đổi
- Staging Area (SA): Các file được đưa vào vùng chuẩn bị commit
- Repository (Re): Các commit (Các phiên bản) - Bao gồm tất cả các file từ SA tổng hợp lại thành 1 phiên bản

**Các câu lệnh**:  
1. git init : Tạo ra ba vùng lưu trữ (ba trạng thái của git) - tất cả các file ban đầu ở vùng WD
2. git add <tên file> : Đưa file từ WD qua SA
3. git commit -m "Tên commit" : Commit các file từ SA vào Re. Các phiên bản mới nhất sẽ nằm bên trên các phiên bản trước đó.

**Triển khai thực tế**:
```java
// ---LÀM MỘT LẦN DUY NHẤT---
// 1. Khởi tạo Repo local
    git init

// 2. Tạo repo gitHub và liên kết với Repo local
    git remote add origin <url>

    git remote -v  //kiểm tra remote

// ---LÀM MỖI KHI CÓ THAY ĐỔI MỚI---
// 3. Thêm file vào Staging
    git add .  //Thêm toàn bộ file thay đổi
    git add file2.txt file3.txt  //add hai file 1 lúc
    git add folder/file4.txt. //add file nằm trong folder

// 4. Commit file
    git commit -m "<message>"

// 5. Push code lên gitHub
    git push origin main

```

**Commit convention**: Đặt tên commit cho đẹp  
Type: Short_description 
- Type: Loại commit
    - Chore: Sửa nhỏ lẻ, chính tả, xóa file không dùng
    - Feat: Thêm tính năng mới, test case mới
    - Fix: Sửa lỗi một test trước đó
- Short_description: Mô tả ngắn gọn (50 ký tự) 

    VD: "Chore: Remove unuse file"


**Cấu hình cho git biết mình là ai?**:
- Cấu hình Global (Mặc định)
    - git config --global user.email "youremail"
    - git config --global user.name "yourname"
- Cấu hình riêng lẻ cho từng thư mục
    - git config user.email "youremail"
    - git config user.name "yourname"

**Một số câu lệnh khác**: 
``` Java
// Trạng thái các file mới thay đổi 

    git status
    // Nếu xanh là đang ở Staging
    // Nếu đỏ là đang ở Working Directory 

// Danh sách các commit: 
    git log

```
---

### ✅ Lesson #3: JavaScript 1

**1. In ra một dùng chữ**: 
```JavaScript
    console.log("Hello word")
```

**2. Comment**: 
```Javascript
    // Đầu dòng

    /* 
        cmt nhiều dòng
                        */

    //Có thể cmt nhanh bằng cách bôi đen một đoạn code sau đó sử dụng tổ hợp cmd + /
```
**3. Biến**: Thay đổi được 
- Khai báo: <Từ khóa> <Tên biến> = <Giá trị>
- var cho phép khai báo lại và có phạm vi global
- let không cho phép khai báo lại và chỉ có phạm vi trong một block 

=> Ưu tiên sử dụng let hơn vì an toàn hơn

```javascript
// Ví dụ
var centerName = "Better Bytes"; //Kiểu string
let isLovePlaywright = true;  //Kiểu boolean
```

**4. Hằng số**:
- Không thể thay đổi được nội dung sau khi khai báo 
```Javascript
const slogan = "Học kỹ - Hiểu sâu";
// slogan không thể thay đổi được
```

**5. Kiểu dữ liệu**: 
<br>JavaScript có 8 kiểu dữ liệu và được chia làm hai nhóm chính:
- Kiểu nguyên thủy: 
    - Number: Số nguyên và số thực (không phân biệt)
    - String: Chuỗi ký tự
    - Boolean: Giá trị logic (True-False)
    - Undefined
    - Null
    - Symbol 
    - Big Int
- Kiểu tham chiếu:
    - Object
- Sử dụng hàm "typeof<variable>" để kiểm tra kiểu dữ liệu của biến
```Javascript
//Ví dụ 1:
    const age = 18;
    const message = `I am ${age} years old`;

//Ví dụ 2: 
    const isActive = True;
    const isComplete = False;

// Ví dụ 3: Kiểm tra kiểu dữ liệu
    console.log(typeof age);
    //Output = Number
```
 **6. Các toán tử**:  
**6.1. Toán tử so sánh**: Kết quả trả về là kiểu Boolean  
- So sánh bằng: == và ===
- So sánh không bằng: !==
- So sánh lớn hơn, nhỏ hơn: >, <, >=, <=

Notes:
- So sánh hai bằng: Không chặt chẽ lắm
    - 5==5 //True (Chuyển string thành number)
    - 6==5 //False (Chuyển string thành number)
    - True = 1  //True (chuyển true thành 1)
    - False = 0  //True (chuyển false thành 0)
- So sánh ba bằng: Đúng giá trị và đúng kiểu (nên dùng)
    - 5==="5"  //False (Vì khác kiểu)

**6.2. Toán tử logic**: && (And), || (Or)
- AND: Thỏa mãn khi cả hai đều đúng 
- OR: Thỏa mãn khi một trong hai đúng là đủ

**6.3. Toán tử một ngôi**: 1 toán hạng để thực hiện
```Javascript
let x = 5;

y = x++; 
//postfix: Gán x cho y rồi mới tăng x lên một
// Output: x=6; y=5

y = ++x; 
//postfix: Tăng x lên một rồi mới gán cho y
// Output: x=6; y=6

y = x--; 
//postfix: Gán x cho y rồi mới giảm x một
// Output: x=4; y=5

y = --x; 
//postfix: Giảm x một rồi mới gán cho y
// Output: x=4; y=4
```
**6.4. Toán tử toán học**: +, -, *, /
- % là chia lấy dư
- Chia cho 0 kết quả là Infinity 

**7. Câu điều kiện**: 
- if
- if...else
- if...elseif...else
- switch...case
```Javascript
if (điều kiệu){
    //code...
}
```
**8. Vòng lặp**: 
```Javascript
for (<điều kiệu khởi tạo>; <điều kiện lặp>; <update>)
{
    //code...
}

//Ví dụ: 
for(let i=0; i<1000; i++){
    console.log('Xin chào');
}
```
- for(i)
- for(of)
- for(each)
- for(in)
- while
- do...while
---

