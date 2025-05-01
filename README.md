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






