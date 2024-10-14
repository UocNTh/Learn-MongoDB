
**Tìm hiểm về NoSQL** 
- NoSQL là gì?
- Lịch sử phát triển 
- Các thuật ngữ trong NoSQL 
- Phân loại và ứng dụng NoSQl 

**1. NoSQL là gì?**

- Là Not Only SQL 
- Không sử dụng mô hình dữ liệu quan hệ 
- Mô hình lưu trữ {"key":"value"}
- Hệ thống lưu trữ phân tán

--> Hệ cơ sở dữ liệu không ràng buộc, phân tán, mã nguồn mở, khả năng mở rộng theo chiều ngang, có thể chứa hàng petabytes, độ chịu tải và chịu lỗi cao, yêu cầu về tài nguyên phần cứng

**2. Lịch sử phát triển**

- NoSQL storage thông dụng với các mạng xã hội : facebook, twitter (các ứng dụng big data)

**3. Thuật ngữ liên quan**
- ```Ràng buộc (Relational)```: Trong SQL Server, MySQL, sử dụng mô hình khóa: khóa chính, khóa ngoại ràng buộc dữ liệu lại với nhau.

- ```Không ràng buộc (Non-relational)```: Không có khái niệm khóa chính, khóa ngoại

- ```Khả năng mở rộng (High Scalability)```: Đối với NoSQL, không có giới hạn cho dữ liệu. Do sử dụng hệ thống phân tán, khi hệ thống lớn lên có thể mở sung server để chia dữ liệu, chia tải để hệ thống hoạt động tốt hơn. VD Facebook, Google

- ```Khả năng mở rộng chiều dọc```: nâng cấp CPU, nâng cấp RAM, nâng cấp ổ cứng để hiệu suất hoạt động nhanh hơn
- ```Khả năng mở rộng chiều ngang```: Gắn thêm server để tăng hiệu suất. Hệ thống cơ sở phân tán sẽ mở rộng theo chiều ngang

- ```Phân tán dữ liệu```
- ```Triển khai linh hoạt```
- ```Tính sẵn sàng```
- ```Nhất quán cuối```
- ```Lưu trữ tốt```

**4. So sánh NoSQL và SQL**

|Tính năng|SQL|NoSQL|
|:---:|:---:|:---:|
|Hiệu suất| Kém hơn NoSQL vì khi truy vấn phải có tính toán, kiểm tra và xử lý các mối quan hệ các bảng| Tốt hơn SQL vì nó bỏ qua các ràng buộc|
|Mở rộng theo chiều ngang|Có thể thực hiện được nhưng phức tạp| Mở rộng dễ dàng|
|Tốc độ Read/Write|Kém hơn NoSQL do phải đảm bảo tính ràng buộc dữ liệu giữa các bảng|Tốc độ nhanh hơn SQL vì bỏ qua cơ chế ràng buộc giữa các bảng. Vì dữ liệu được lưu trong RAM sau đó mới đẩy xuống HĐ và tính nhất quán cuối|
|Phần cứng|Đòi hỏi phần cứng cao| Không đòi hỏi quá cao về phần cứng|
|Truy vấn và báo cáo|Dễ dàng sử dụng ngôn ngữ SQL query để truy vấn trực tiếp từ database| Chưa được hỗ trợ tốt|
|Mở rộng dữ liệu|Muốn bổ xung phải khai báo trước| Không cần khai báo trước
|Ứng dụng| Để xây dựng những hệ thống có quan hệ chắt chẽ và cần tính thống nhất về dữ liệu như: tài chính, ngân hàng, chứng khoán|Sử dụng xây dựng những hệ thống lưu giữ thông tin lớn, không quá quan trọng về vấn đề đồng nhất dữ liệu trong một thời gian. VD như: báo chí, mạng xã hội, diễn đàn, we mua hàng|

**5. Phân loại NoSQL**




---

**1. Định nghĩa MongoDB**

**MongoDB** là một cơ sở dữ liệu đa nền tảng, hoạt động trên các khái niệm Collection và Document, nó cung cấp hiệu suất cao, tính khả dụng cao và khả năng mở rộng dễ dàng.

**2. Thuật ngữ RDBMS với MongoDB**

|RDBMS|MongoDB|
|:---:|:---:|
|Database|Database|
|Table|Collection|
|Row|Document|
|Column|Field|
|Table Join	|Embedded Documents|
|Primary Key|Primary Key (Default key _id provided by mongodb itself)|

**3. Tại sao nên sử dụng MongoDB?** 

Bởi vì MongoDB:

- Lưu trữ hướng tài liệu - dữ liệu được lưu trữ dưới dạng tài liệu kiểu JSON.
- Chỉ mục trên bất kỳ thuộc tính
- Nhân rộng và sẵn sàng cao.
- Tự động bảo vệ.
- Truy vấn phong phú.
- Cập nhật nhanh tại chỗ.
- Hỗ trợ chuyên nghiệp bởi MongoDB

**4. Sử dụng MongoDB ở đâu?**

- Dữ liệu lớn.
- Quản lý và phân phối nội dung.
- Cơ sở hạ tầng di động và xã hội.
- Quản lý dữ liệu người dùng.
- Trung tâm dữ liệu.
