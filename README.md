# Bài tập 6: Hệ quản trị CSDL
# Sinh Viên: Lương Hoàng Việt - K225480106073
## Chủ đề: Câu lệnh Select
### Yêu cầu bài tập: 
Cho file sv_tnut.sql (1.6MB)
1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
6. nhập sql để tìm xem có những sv nào trùng tên với em?
7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)

DEADLINE: 23H59:59 NGÀY 25/4/2025

Ghi chú: Giải thích tại sao lại có SQL như vậy.
# Bài làm
## 1. Để Import dữ liệu vào database, dùng 1 Database đã tạo trước đó, open Query sv_tnut.sql, chạy câu lệnh "use [sv_tnut]" để truy cập data base, sau đó chạy toàn bộ phần code còn lại của file .sql<br>
1.1. Thứ tự chạy code để Insert dữ liệu vào Database:![Thứ tự chạy code](https://github.com/user-attachments/assets/90ee9280-0925-42de-9125-01ba5ab5d3d6)<br>
1.2. Sau khi đã chạy code thành công, sẽ xuất hiện table SV:![image](https://github.com/user-attachments/assets/ecb2121d-57fc-4982-b142-11ce817de4d9)<br>
## 2. Dữ liệu của bản thân: ![image](https://github.com/user-attachments/assets/9d052080-0941-43b2-9206-e52a23c92c34)
## 3. Sql tìm sinh viên trùng hoàn toàn ngày/tháng/năm: ![image](https://github.com/user-attachments/assets/6017bc42-871d-4f0b-8785-6eba41ff2a05)
## 4. SQL tìm sinh viên trùng ngày và tháng sinh: ![image](https://github.com/user-attachments/assets/f9994f0d-7596-4f29-8fc8-fcd4d0300cb9)
## 5. SQL tìm sinh viên trùng tháng và năm sinh: ![image](https://github.com/user-attachments/assets/ed0fe619-3831-45a5-bf32-8dec066041bc)
## 6. SQL tìm sinh viên trùng tên: ![image](https://github.com/user-attachments/assets/11087a50-aa9b-458c-b71f-55ed4b7b48b7)
## 7. SQL tìm sinh viên trùng họ và tên đệm: ![image](https://github.com/user-attachments/assets/a7e1089b-ffd3-41d8-afe1-62e5f0e3a5af)
## 8. SQL tìm sinh viên có sđt sai khác chỉ 1 số so với số của bản thân:<br>
8.1. Khác chỉ 1 số thì không có ai: ![image](https://github.com/user-attachments/assets/94d8b730-4c32-46fa-9e9e-3784c77fbd84)
8.2. Khác 4 số thì hiện 4 kết quả: ![image](https://github.com/user-attachments/assets/27c6df7e-0b53-4bc6-8aee-3aec24290207)
Kết luận: Tại phần này với sđt của bản thân là "0385579617" khi tìm trong Database thì khác biệt đến 4 số bất kì (trừ số 0 ở đầu) mới xuất hiện kết quả!
## 9. Liệt kê tất cả các sinh viên ngành KMT, sắp xếp theo tên và họ đệm, kiểu tiếng Việt và giải thích:![image](https://github.com/user-attachments/assets/c2512afc-343d-4a18-a415-bfdf6952ef4d)
Giải thích:
SELECT *
Lấy tất cả các cột từ bảng [SV] (SV có thể là viết tắt của "Sinh viên").

FROM [SV]
Dữ liệu được truy vấn từ bảng tên là SV.

WHERE lop LIKE N'%KTP%' OR lop LIKE N'%KMT%'
Điều kiện lọc các bản ghi:

Chỉ lấy những sinh viên có lớp (trong cột lop) chứa chuỗi "KTP" hoặc "KMT".

N'%KTP%': chữ N dùng để chỉ chuỗi Unicode (phòng trường hợp có ký tự tiếng Việt).

Dấu % đại diện cho bất kỳ chuỗi nào (hoặc không có gì), nghĩa là chỉ cần trong tên lớp có chứa "KTP" hoặc "KMT", không quan trọng ở đầu, giữa hay cuối.

ORDER BY Ten COLLATE Vietnamese_CI_AS, HoDem COLLATE Vietnamese_CI_AS
Sắp xếp kết quả theo thứ tự chữ cái tiếng Việt:

Đầu tiên sắp xếp theo cột Ten (tên gọi).

Sau đó sắp xếp theo HoDem (họ và tên đệm).

COLLATE Vietnamese_CI_AS:

Sử dụng kiểu sắp xếp tiếng Việt.

CI: Case Insensitive (không phân biệt hoa thường).

AS: Accent Sensitive (phân biệt dấu).
## 10. SQL liệt kê sinh viên Nữ của ngành:
Tại bài này bản thân em đưa ra cách nhận diện bằng hodem, nếu là nữ thì đến 70% sẽ có hodem là "Thị",kèm thêm 1 số họ đệm phổ biến khác như "Diệu", "Bích","Mai","Ngọc"....<br>
Bảng liệt kê danh sách nữ ( Theo dự đoán):![image](https://github.com/user-attachments/assets/19c06e78-534a-48f2-90aa-5a86a40b094a)
## KẾT LUẬN: Bài tập trên chủ yếu sử dụng câu lệnh SELECT kèm 1 vài điều kiện để truy xuất các dữ liệu cần thiết và đặc biệt ở P10 phải suy nghĩ các cách để phân biệt khi không có 1 trường dữ liệu phù hợp cho việc nhận dạng!




