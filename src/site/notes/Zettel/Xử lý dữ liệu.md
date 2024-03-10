---
{"dg-publish":true,"permalink":"/zettel/xu-ly-du-lieu/","created":"2024-03-06T12:06:48.224+07:00","updated":"2024-03-06T16:23:40.212+07:00"}
---

# I. Xử lý dữ liệu

Cho tập dữ liệu sau:

| Tên | Lương ($) |
| --- | --------- |
| A   | NULL      |
| B   | 1000      |
| C   | 200       |
| D   | NULL      |
| E   | -100      |

## 1. Thiếu/mất dữ liệu 

Dựa vào bảng trên, ta có thể thấy ở thuộc tính *lương*, nhân viên $A$ và $B$ bị thiếu/mất dữ liệu. Để xử lý vấn đề này, ta có nhiều phương pháp:
- **Bỏ qua những bản ghi bị thiếu dữ liệu**: Dễ hiểu, ta bỏ luôn $A$ và $D$ khỏi tập dữ liệu trên, giữ lại $B, C, E$.
- **Điền vào dữ liệu thiếu một cách thủ công**: Thủ công ở đây nghĩa là ta sẽ đi khảo sát nhân viên $A$ và $D$ để điền lại dữ liệu thiếu.
- **Dùng hằng số toàn cục để điền vào vị trí thiếu**: 
- **Sử dụng mean hoặc median để điền vào vị trí thiếu**:
- **Sử dụng mean hoặc median của thuộc tính mà ta đang xét để điền**: 
- **Sử dụng giá trị phù hợp nhất để điền**:

---
# References

- [Slide của Minh Khuê](https://drive.google.com/drive/folders/1uV0XUuGgCSGILaI5b3CKPizY_1IK1aTx)
- [Data Mining. Concepts and Techniques, 3rd Edition (The Morgan Kaufmann Series in Data Management Systems) (sabanciuniv.edu)](https://myweb.sabanciuniv.edu/rdehkharghani/files/2016/02/The-Morgan-Kaufmann-Series-in-Data-Management-Systems-Jiawei-Han-Micheline-Kamber-Jian-Pei-Data-Mining.-Concepts-and-Techniques-3rd-Edition-Morgan-Kaufmann-2011.pdf) (chương 2)