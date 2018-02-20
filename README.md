# Unit-test-for-Angular
this is my report

# I. Unit Testing là gì?
## 1. Khái niệm
- Unit Test là kỹ thuật kiểm nghiệm các hoạt động của mã code giúp phát hiện sai sót kịp thời. Unit Test còn có thể giúp phát hiện các vấn đề tiềm ẩn và các lỗi thời gian thực ngay cả trước khi QA tìm ra, thậm chí có thể sửa lỗi ngay từ ý tưởng thiết kế.
- Unit Test là các đoạn mã có cấu trúc giống như các đối tượng được xây dựng để kiểm tra từng bộ phận trong hệ thống. Mỗi Unit Test sẽ gửi đi một thông điệp và kiểm tra câu trả lời nhận được đúng hay không, bao gồm: Các kết quả trả về mong muốn, các lỗi ngoại lệ mong muốn. Các đoạn mã Unit Test hoạt động liên tục hoặc định kỳ để thăm dò và phát hiện các lỗi kỹ thuật trong suốt quá trình phát triển, do đó Unit Test còn được gọi là kỹ thuật kiểm nghiệm tự động.
- Unit Test là do chính lập trình viên viết, để kiểm tra các hàm do chúng ta viết ra có sai hay không. Unit test kiểm tra từng bộ phận nhỏ (unit) trong source code và đảm bảo các hàm này chạy đúng mỗi khi chúng ta sửa, cập nhật source code.
- Ở mức độ cao hơn, để đảm bảo toàn bộ hệ thống chúng ta hoạt động trơn tru như mong đợi, E2E test ra đời diups chúng ta kiểm thử toàn bộ hệ thống, từ giao diện cho đến các business logic trong hệ thống, giống như một người dùng thực thụ. (User flow)

## 2. Các đặc điểm của Unit Test
- Đóng vai trò như những người sử dụng đầu tiên của hệ thống.
- Chỉ có giá trị khi chúng có thể phát hiện các vấn đề tiềm ẩn hoặc lỗi kỹ thuật.
- Giảm thiểu các rủi ro khi phát triển feature mới hay giảm thiểu bug trong quá trình thay đổi các chức năng có sẵn.
- Cải thiện thiết kế và cho phép refactoring code tốt hơn.

# II. Unit Test trong Angular
## Có rất nhiều các framework, tool test hỗ trợ cho Angular điển hình như: Karma, Jasmine, angular-mocks
 - Jasmine:
   + Là một javascript testing framework hỗ trợ BDD (Behavior Driven Development), nó cố gắng mô tả các tests trong một định dạng chúng ta có thể dễ dàng đọc hiểu, ngay cả đối với những người không am hiểu kĩ thuật cũng có thể hiểu những gì đang test ở đây.
   + Jasmine là công cụ được chọn nhiều nhất cho việc test ứng dụng Angular. Jasmine cung cấp các tính năng cho phép cấu trúc test cũng như tạo ra assertions.
   + Jamine sử dụng describe để nhóm các function test lại với nhau, cung cấp nhiều các matcher cho phép bạn tạo các assertions.
 - Karma:
   + Karma là một Javascript tool được sử dụng để load ứng dụng và thực thi test của bạn. Karma sẽ được thực thi bằng dòng lệnh và sẽ hiển thị kết quả cho bạn biết mỗi khi bạn chạy trình duyệt.
   + Karma được viết bằng NoteJS và nó phải được cài thông qua npm
 - Angular-mocks: angular-mocks là một module ngMock của Anguar, nó cung cấp các kiểu mock cho việc test của bạn.

# III. Setup project angular cơ bản và môi trường.
## 1. Cài đặt NodeJS
## 2. Tạo file package.json
<img width="332" alt="1" src="https://user-images.githubusercontent.com/35052781/36428220-ee80c79c-1681-11e8-9e57-d142d69c676c.png">

<img width="332" alt="2" src="https://user-images.githubusercontent.com/35052781/36428257-070a4888-1682-11e8-8ffd-d6c481bee353.png">

## 3. Tạo file tsconfig.json
<img width="330" alt="3" src="https://user-images.githubusercontent.com/35052781/36428300-22f715ee-1682-11e8-8a3f-b7bb0955b91d.png">

## 4. Tạo file typings.json
<img width="332" alt="4" src="https://user-images.githubusercontent.com/35052781/36428326-385373ba-1682-11e8-869e-83071c9b57ad.png">

## 5. Tạo file systemjs.config.js
<img width="332" alt="5" src="https://user-images.githubusercontent.com/35052781/36428366-53a97650-1682-11e8-8c40-752f730b06e2.png">

<img width="332" alt="6" src="https://user-images.githubusercontent.com/35052781/36428367-53e8ce54-1682-11e8-8e5e-3b5166a057f2.png">

## 6. Cài các modules bằng lệnh npm install

# IV. Ví dụ
## Tạo ứng dụng cơ bản
## 1. Tạo thư mục app
## 2. Tạo file app.module.ts trong thư mục app
<img width="332" alt="7" src="https://user-images.githubusercontent.com/35052781/36428593-e7582680-1682-11e8-8953-fccf033ee2a8.png">

## 3. Tạo file app.component.ts trong thư mục app
<img width="292" alt="1" src="https://user-images.githubusercontent.com/35052781/36428646-0c71fb26-1683-11e8-9584-45b3184fa346.png">

## 4. Tạo file main.ts trong thư mục app
<img width="332" alt="2" src="https://user-images.githubusercontent.com/35052781/36428678-25669498-1683-11e8-9552-3d18ff6f040a.png">

## 5. Tạo file index.html trong thư mục gốc
<img width="332" alt="3" src="https://user-images.githubusercontent.com/35052781/36428723-3fa60118-1683-11e8-8ba4-f467efc70fda.png">

   Đến đây ta đã thiết lập xong project cơ bản rồi. Mình tiếp tục thiết lập cho các unit test
## Thiết lập môi trường cho Unit Test
## 1. Tạo file karma-test-shim.js
<img width="332" alt="1" src="https://user-images.githubusercontent.com/35052781/36430006-b348497a-1686-11e8-8c22-846a49060d67.png">

<img width="332" alt="2" src="https://user-images.githubusercontent.com/35052781/36430007-b38020ca-1686-11e8-8003-da957a81d3e0.png">

<img width="332" alt="3" src="https://user-images.githubusercontent.com/35052781/36430008-b3b32b3c-1686-11e8-9ef8-66d75dfe62b6.png">

## 2. Tạo file karma.config.js
<img width="332" alt="1" src="https://user-images.githubusercontent.com/35052781/36430159-0aca9b1c-1687-11e8-8236-11f0d6a34375.png">

<img width="332" alt="2" src="https://user-images.githubusercontent.com/35052781/36430160-0b05fd92-1687-11e8-96ce-1e46c344210e.png">

<img width="332" alt="3" src="https://user-images.githubusercontent.com/35052781/36430155-0a35ecd8-1687-11e8-9122-3bc377c1ff82.png">

<img width="332" alt="4" src="https://user-images.githubusercontent.com/35052781/36430157-0a91cddc-1687-11e8-9863-ddb104ae1e8e.png">

## 3. Cài karma: npm install karma
## 4. Cài plugin: npm install karma-jasmine karma-chrome-launcher
## 5. Tạo file simple test simple.spec.ts
<img width="258" alt="1" src="https://user-images.githubusercontent.com/35052781/36430916-d8eaa1da-1688-11e8-8b45-d13cfbec07c1.png">

## 6. Bây giờ mình sẽ test thử bằng lệnh npm test







 
