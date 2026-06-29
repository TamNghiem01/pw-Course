# 📚 Lessons Learned - Automation Testing

1. Git  
    1.1. Git undo action  
    1.2. Git branching  
    1.3. Git amend  
    1.4. Git ignore  
2. Javascript  
    2.1. Convention  
    2.2. console.log()  
    2.3. Object  
    2.4. Array  
    2.5. Function  


---

## 🗓️ Tháng 05/2026

### ✅ Lesson #1: GIT 2

#### **1.1 Git Undo Action**

***Chuyển file từ staging về lại working directory***:  
- ```git restore --staged <file name>``` : Chuyển một file bất kỳ
- ```git restore --staged .``` : Chuyển toàn bộ các file
- Untracked file là những file đang ở vùng working directory 

***Chuyển file từ Repository về lại Working Directory***: ```git reset HEAD ~<số commit>```  
VD: ```git reset HEAD ~2``` : Chuyển hai commit mới nhất về lại Working Directory 


***Thực tế:***
- Các câu lệnh trên được sử dụng khi thêm vào Staging nhưng chưa cần thiết commit
- Commit đầu tiên không thể reset. Nếu muốn reset thì xóa thư mục git rồi init lại

#### **1.2 Git: Branching**
- Cấu hình nhánh chính (nhánh mặc định):
    ```git config --global init.defaultBranch main```
- Lấy code từ server về:
    ```git pull origin main```
- Xem danh sách nhánh: Phải có ít nhất một commit thì mới hiện danh sách nhánh
    ```git branch```
- Tạo nhánh mới: Nhánh mới copy giống hệt nhánh hiện tại, khi làm việc sẽ không ảnh hưởng đến nhánh khác
    ```git branch <Tên_nhánh>```
- Chuyển sang nhánh mới:
    ```git checkout <Tên_nhánh>```
- Vừa tạo vừa chuyển sang nhánh mới:
    ```git checkout -b <Tên_nhánh>```
- Xóa branch: Đứng ở nhánh khác trước khi xóa
    ```git branch -D <Tên_nhánh>```

**Lưu ý:** Luôn pull code về trước khi tạo nhánh mới


#### **1.3 Git amend**
- ```git commit --amend``` là lệnh cho phép sửa đổi commit gần nhất. Thay vì tạo commit mới, nó viết lại commit cuối cùng
- Dùng git amend khi:
    - Viết sai commit message: Sai chính tả, thiếu thông tin ...
    - Quên thêm một file vào commit
    - Muốn bỏ bớt file khỏi commit cuối
    - Cần sửa nhỏ mà không muốn tạo commit mới (rác)
1. Sửa commit message:  
    - ```git commit --amend -m "message mới chính xác hơn"```
    - Hoặc chỉ chạy ```git commit --amend``` để mở editor và sửa
2. Thêm file quên stage: VD tên file: utils.py
    - ```git add utils.py``` : Thêm file vào staging
    - ```git commit --amend --no-edit```: --no-edit là giữ nguyên message cũ và chỉ thêm file vào cùng commit cuối
3. Vừa thêm file vừa sửa message: VD tên file: forgotten.py
    - ```git add forgotten.py```: Thêm file vào staging
    - ```git commit --amend -m "Message mới chính xác hơn"```
4. Bỏ file khỏi commit cuối
    - ```git reset HEAD~ -- file_to_remove.py```
    - ```git commit --amend --no-edit```
5. amend với commit đã push: Không được khuyến khích, chỉ nên làm trên branch cá nhân
    - ```git commit --amend -m "message đã sửa"```
    - ```git push --force-with-lease```: Nó kiểm tra xem remote có được thay đổi bởi người khác không trước khi ghi đè

#### **1.4 Git Ignore: .gitignore**
- Là file cấu hình quan trọng trong git, giúp chỉ định những file hoặc thư mục nào sẽ không được theo dõi bởi git (untracked)
- Trong dự án có nhiều file không cần git quản lý như:
    - File tạm thời
    - Thư mục dependencies 
    - File build
    - File cấu hình cá nhân
    - File log
    - File nhạy cảm ...
- Dùng ```#``` để comment trong file .gitignore


---

### ✅ Lesson #2: JavaScript 2

**1. Convention: Quy tắc đặt tên file**: Giúp code theo format chung, dễ nhìn, đẹp
- snake_case: vd: tam_nghiem (Không dùng)
- kebab-case: vd: tam-nghiem (Tên file, folder)
- camelCase: vd: tamNghiem (Tên biến, hàm)
- PascalCase: vd: TamNghiem (Tên class)
- UPPER_CASE: vd: TAM_NGHIEM

**2. Dùng console.log**: 
- Sử dụng được với nháy đơn và nháy kép
- Sử dụng với variable 
- Sử dụng cộng chuỗi

**3. Object**: Dùng để lưu trữ dữ liệu dạng key-values
- Key: 
    - Giống quy tắc đặt tên biến, luôn có kiểu string. 
    - Có thể lược bỏ ngoặc kép, nhưng bắt buộc có nếu chứa dấu cách. 
    - Không nên đặt tên key có dấu cách. Ưu tiên dấu đơn hơn. 
- Truy vấn giá trị của Object:
    - Sử dụng chấm nếu key không chứa dấu cách
    - Ngược lại thì bắt buộc dùng ngoặc vuông

```javascript
// Ví dụ
const myInfo = {
    name: "Tam",
    favoriteNumber: 5,
    address: "TP.HCM"
}

// Truy vấn giá trị của Object:
// Ví dụ 1: 
myInfo.name;

// Ví dụ 2:
myInfo["name"];
myInfo["codingClass"]["name"]

```

**4. Array: Mảng**:

```Javascript
const arr = [3,7,8,0,5];
// arr là tên mảng
// [3,7,8] là các phần tử mảng

// Truy xuất: kết quả là 3
console.log(arr[0])

// Lấy độ dài mảng: kết quả là 5
arr.length 

```

**5. Function: Hàm**: 
- Tên hàm bắt đầu bằng động từ: tinhDienTich
- Tên biến là danh từ: dienTich
```Javascript
// Cú pháp ví dụ:
function tinhDienTich(dai,rong) {
    const dienTich = dai*rong;
    return dienTich;
}

```
