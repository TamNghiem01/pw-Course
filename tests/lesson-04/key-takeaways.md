# 📚 Lessons Learned - Automation Testing

**JAVASCRIPT**
1. Phạm vi của biến
2. Break and continue
3. Câu điều kiện nâng cao
4. Vòng lặp nâng cao
5. Utils fuction: gọn hơn và nhanh hơn: Xử lý chuỗi và xử lý mảng sử dụng hàm có sẵn

---

## 🗓️ Tháng 06/2026

### ✅ Lesson: JAVASCRIPT 3

#### **1. Phạm vi của biến**

- Khối: Khai báo trong ngoặc nhọn
    - var: không bị giới hạn 
    - let: bị giới hạn trong khối
- Hàm: Ngoài hàm, tất cả đều undefined
- Toàn cục (Global): Dòng code tự do, không nằm trong khối hoặc trong hàm
    - Biến chỉ dùng trong hàm thì nên giới hạn trong hàm
    - Nên giới hạn khai báo biến trong phạm vi nhỏ nhất có thể



#### **2. Break and Continue**
- Chạy vòng lặp linh hoạt hơn, tùy theo ý muốn
- Break dùng để thoát hỏi vòng lặp ngay lập tức
- Ví dụ:
```Javascript
for(let i = 0; i < 10; i++) {
    if(i === 5){
        break; //Thoát khỏi vòng lặp khi i=5
    }
    console.log(i);
}
```
- Continue: Bỏ qua vòng lặp hiện tại và chuyển qua vòng tiếp theo. Continue bỏ qua tất cả câu lệnh bên dưới trong vòng lặp.
```Javascript
for(let i = 0; i < 10; i++>){
    if(i%2 === 0){
        continue; //Bỏ qua số chẵn
    };
    console.log(i);
}
```


#### **3. Câu điều kiện nâng cao**
- Câu điều kiện if...else: Thực thi code khác nhau trong từng trường hợp khác nhau
- Câu điều kiện if...elde...if:
```Javascript
if(score >= 90){
    console.log("Xuất sắc");
} else if(score >= 80){
    console.log("Giỏi");
} else if(score >= 70){
    console.log("khá");
} else if(score >= 50){
    console.log("Trung bình");
} else if(score >= 30){
    console.log("Yếu");
} else{
    console.log("Kém");
}
```
- Toán tử điều kiện: Tương tự if...else
```Javascript
let xepHang = age>18? "Người lớn" : "Trẻ em"
/* age>18 là điều kiện
"Người lớn" là giá trị trả về khi điều kiện đúng
"Trẻ em" là giá trị trả về khi điều kiện sai
Có thể lồng nhau giống if...else...if
*/

//Ví dụ:
let score = 75;
let grade = score >=90? "A" :
            score >=80? "B" :
            score >=70? "C" :
            score >=60? "D" : "F";
```


#### **4. Vòng lặp nâng cao:**
- for...in loop: dùng để duyệt qua các thuộc tính object
```Javascript
const person = {
    name: "Jonh",
    age: 30,
    city: "Hà nội"
};

for(let key in person){
    console.log(key+ ": " + person.key);
}
/*Output:
name: "Jonh",
age: 30,
city: "Hà nội"
*/
```
- forEach: Không dùng được break hoặc continue. forEach dùng để thực thi 1 function cho mỗi phần từ mảng
- Ví dụ:
```Javascript
const numbers = [1,2,3,4,5];
numbers.forEach(function(Value){
    console.log(value);
});
```

#### **5. Utils function:** Gọn hơn và nhanh hơn
- Tiện ích, là các hàm có sẵn của JS, giúp code nhanh hơn và tiện hơn.
- 2 loại thường dùng:
    - String utils: Các hàm xử lý chuỗi
    - Array utils: Các hàm xử lý mảng 

**XỬ LÝ CHUỖI:**
- Bỏ khoảng trắng:
    - ```trim()```: Bỏ hai đầu
    - ```trimStart()```: Bỏ bên trái
    - ```trimEnd()```: Bỏ bên phải
    ```Javascript
    let text = "Hello Word";
    console.log(text.trim());
    ```
- Chuyển chữ hoa và chữ thường:
    - Thường thành hoa: ```toUpperCase()```
    - Hoa thành thường: ```toLowerCase()```
- Kiểm tra chuỗi con có tồn tại trong chuỗi cha:
    - ```includes("Chuỗi con")```
    - Có phân biệt hoa thường (đúng tuyệt đối)
    - Trả về giá trị True/False
    - Ví dụ:
    ```Javascript
    let text = "Hello Word";
    console.log(text.includes("Word"));
    //Output: True
    ```
- Cắt chuỗi: 
    - ```split("biên giới cắt")```
    ```Javascript
    let text = "Hello Word Javascript"
    console.log(text.split(" ")) //Cắt theo khoảng trắng
    /*Output: 
    0: "Hello"
    1: "Word"
    2: "Javascript"
    length: 3
    */
    ```
- Thay thế chuỗi bằng chuỗi con khác:
    - ```replace("chuỗi muốn thay", "chuỗi mới")```
    - Nếu không tìm được chuỗi muốn thay thì vẫn trả về chuỗi gốc, không báo lỗi.

**XỬ LÝ MẢNG:**
- Thêm phần tử vào mảng:
    - Thêm vào cuối: ```push(<phần tử>)```
    - Thêm vào đầu: ```unshift(<Phần tử>)```
    - Thêm vào giữa: ```splice(<vị trí>, <số phần tử cần xóa>, <phần tử thêm>)```
    - Ví dụ: 
    ```Javascript
    let arr = [1,2,3];
    arr.push(4); //[1,2,3,4]
    arr.unshift(0); //[0,1,2,3,4]
    arr.splice(2,0,1.5); // [0,1,1.5,2,3,4]
    console.log(arr);
    //Output: 0,1,1.5,2,3,4
    ```
- Xóa phần tử khỏi mảng:
    - Xóa cuối: ```pop()```
    - Xóa đầu: ```shift()```
    - Xóa từ vị trí đã cung cấp: ```slice(<vị trí>, <số phần tử>)```
    - Ví dụ:
    ```Javascript
    let arr = [1,2,3,4,5];
    arr.pop(); //[1,2,3,4]
    arr.shift(); // [2,3,4]
    arr.slice(1,1); //[2,4]
    ```
- Tìm kiếm phần tử:
    - Trả về phần tử đầu tiên hợp lệ: ```find(<biến>, <điều kiện>)``` => Trả về số
    - Trả về tất cả phần tử hợp lệ: ```filter(<biến>, <điều kiện>)``` => Trả về mảng
- Biến đổi mảng:
    - ```map(<biến>, <hàm>)```: Tạo mảng mới bằng cách áp dụng một hàm lên từng phần tử của mảng gốc
    - Trả về mảng mới cùng độ dài
    - Ví dụ: Nhân mỗi phần tử của mảng với 2
    ```Javascript
    const numbers = [1,2,3,4,5];
    let doubled = number.map(num => num*2);  //num là biến tự đặt
    console.log(doubled);
    //Output: [2,4,6,8,10]
    ```
- Sắp xếp mảng:
    - Tăng dần: ```sort((a,b) => a-b)```  
    B1: So sánh a và b  
    B2:  
    nếu a-b âm, a trước b hay a<b  
    nếu a-b dương, b trước a hay a>b  
    trả về 0 -> Giữ nguyên thứ tự 
    - Giảm dần: ```sort((a,b) => b-a)```
    - Ví dụ: 
    ```Javascript
    const numbers = [40,100,1,10,5];
    number.sort((a,b) => a-b);
    //Output: [1,5,10,40,100]
