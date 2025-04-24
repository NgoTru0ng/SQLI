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

