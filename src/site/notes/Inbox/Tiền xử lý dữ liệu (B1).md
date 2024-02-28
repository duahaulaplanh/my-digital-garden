---
{"dg-publish":true,"permalink":"/inbox/tien-xu-ly-du-lieu-b1/","created":"2024-02-27T13:27:25.662+07:00","updated":"2024-02-28T00:52:46.429+07:00"}
---

# I. Khái niệm dữ liệu

Cho tập dữ liệu khảo sát siêu anh hùng (gọi tắt là SH) dưới đây:

| Name          | Gender | Eye color | Race              | Hair | Height (cm) | Publisher         |
| ------------- | ------ | --------- | ----------------- | ---- | ----------- | ----------------- |
| A-Bomb        | Male   | yellow    | Human             | No   | 203         | Marvel Comics     |
| Abe Sapien    | Male   | blue      | Icthyo Sapien     | No   | 191         | Dark Horse Comics |
| Abin Sur      | Male   | blue      | Ungaran           | No   | 185         | DC Comics         |
| Abomination   | Male   | green     | Human / Radiation | No   | 203         | Marvel Comics     |
| Abraxas       | Male   | blue      | Cosmic Entity     | Yes  | 99          | Marvel Comics     |
| Absorbing Man | Male   | blue      | Human             | No   | 193         | Marvel Comics     |

>[!abstract]+ Định nghĩa
>Một **tập dữ liệu** (dataset) được tạo thành từ nhiều **đối tượng dữ liệu** (data object). Ví dụ trong tập dữ liệu bán hàng, các đối tượng dữ liệu có thể là khách hàng, các món hàng trong cửa hàng, ...

Dựa vào SH ta có thể thấy các đối tượng dữ liệu là những siêu anh hùng mà ta cần khảo sát ví dụ như *A-Bomb, Abe Sapien, ...*.

>[!note]
>Ta có thể gọi *đối tượng dữ liệu* là *mẫu* (sample), *dữ liệu điểm* (data point), *thể hiện* (instance).

>[!abstract]+ Định nghĩa
>Một **thuộc tính** (attribute) đại diện cho một đặc trưng của đối tượng dữ liệu mà ta muốn khảo sát.

Ví dụ trong SH, các thuộc tính của siêu anh hùng mà ta khảo sát là *gender, eye color, race, hair color, height, publisher*. 

>[!note]
>Trong machine learning, ta gọi thuộc tính là **đặc trưng** (feature), trong thống kê ta gọi là **biến** (variable) còn trong data engineering ta gọi là **chiều** (dimension).
## Phân loại thuộc tính

### 1. Định danh (nominal)

- Là những thuộc tính liên quan đến việc "phân loại" (categorize) đối tượng dữ liệu. 
- Thuộc tính định danh không thể dùng tính toán, đo đạc hay sắp thứ tự.

# II. Các phương pháp đánh giá dữ liệu

## 1. Theo xu hướng tập trung (central tendency)

Xét một thuộc tính $X$ có giá trị là $x_1, x_2, ..., x_n$ với $n$ đối tượng dữ liệu. Khi đó các phương pháp đánh giá dữ liệu theo xu hướng tập trung bao gồm:
- **Trung bình** (mean): Là giá trị trung bình của thuộc tính $X$. 
$$
\overline{X} = \dfrac{\sum_{i=1}^n x_i}{n}
$$
>[!example]+ Ví dụ
>Suppose we have the following values for salary (in thousands of dollars), shown in increasing order: 30, 36, 47, 50, 52, 52, 56, 60, 63, 70, 70, 110. Khi đó:
>$$
>\overline{X} = \dfrac{30 + 36 + 47 + 50 + 52 + 52 + 56 + 60 + 63 + 70 + 70 + 110}{12} = 58
>$$
- **Trung vị** (median): Là giá trị "chính giữa" trong $n$ giá trị của $X$.

## 2. Theo xu hướng phân tán


# III. Phép đo độ tương đồng và khác biệt của dữ liệu

## 1. Proximity nominal



---

# References

- [Data Mining. Concepts and Techniques, 3rd Edition (The Morgan Kaufmann Series in Data Management Systems) (sabanciuniv.edu)](https://myweb.sabanciuniv.edu/rdehkharghani/files/2016/02/The-Morgan-Kaufmann-Series-in-Data-Management-Systems-Jiawei-Han-Micheline-Kamber-Jian-Pei-Data-Mining.-Concepts-and-Techniques-3rd-Edition-Morgan-Kaufmann-2011.pdf) (chương 2)
- Note trên lớp của [Phạm Thái Huy](https://drive.google.com/file/d/1CYyAvVTZRllo2Js0npYOVF1x5YzQDLTd/view?usp=sharing)