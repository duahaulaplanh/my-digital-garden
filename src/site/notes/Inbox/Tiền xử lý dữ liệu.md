---
{"dg-publish":true,"permalink":"/inbox/tien-xu-ly-du-lieu/","created":"2024-02-27T13:27:25.662+07:00","updated":"2024-02-29T10:17:24.674+07:00"}
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

Giá trị của một thuộc tính tại một đối tượng dữ liệu nào đó được gọi là một **quan sát** (observation).
## Phân loại thuộc tính

### 1. Định danh (nominal)

- Là những thuộc tính liên quan đến việc "phân loại" (categorize) đối tượng dữ liệu. 
- Thuộc tính định danh không thể dùng tính toán, đo đạc hay sắp thứ tự.

>[!example]+ Ví dụ
>Thuộc tính *Eye color* của SH, các giá trị của eye color là *yellow, blue, green, ...*
### 2. Nhị phân (binary)

- Là thuộc tính nominal nhưng thay vì có nhiều giá trị thì chỉ có thể có 2 giá trị (0 hoặc 1, đúng hoặc sai, nam hoặc nữ, ...)
- Thuộc tính nhị phân được gọi là **đối xứng** (symmetric) nếu cả hai giá trị đều ngang nhau. Ví dụ **nam** hoặc **nữ** thì gán 0 cho nam cũng được, nữ cũng được (và ngược lại) vì cả hai giá trị đều ngang nhau.
- Còn ngược lại là **không đối xứng** (asymmetric) nếu hai giá trị không ngang nhau. Ví dụ trong bài test HIV, kết quả dương tính thường hiếm xuất hiện hơn nên ta gán giá trị là 1, còn âm tính xuất hiện nhiều hơn nên ta gán giá trị là 0.
### 3. Thứ tự (ordinal)

- Là các thuộc tính mà giá trị của nó có tính thứ tự nào đó.

>[!example]+ Ví dụ
>Thuộc tính **drink_size** (kích thước ly nước) sẽ có các giá trị là *small, medium, large*. Có thể thấy các giá trị có thứ tự tăng dần. Ngoài ra thuộc tính **grade** (điểm) có các giá trị $[0, 0.5, 1, 1.5, ..., 9.5, 10]$ cũng là thuộc tính thứ tự.
### 4. Số (numeric)

>[!note]
>Các thuộc **nominal, binary, ordinal** đều là thuộc tính **định tính** (qualitative). Giá trị của các thuộc tính này thường là chữ, nếu là số (ví dụ như $0$ là nam, $1$ là nữ) thì chỉ có nghĩa là cách viết gọn hơn để dễ máy tính dễ xử lý chứ không thể dùng tính toán.

Gồm 2 loại:
- **Interval-Scaled** (theo khoảng): 
- **Ratio-Scaled** (theo tỉ lệ):
# II. Các phương pháp đánh giá dữ liệu

## 1. Theo xu hướng tập trung (central tendency)

### a. Trung bình (mean)

Xét một thuộc tính $X$ có giá trị là $x_1, x_2, ..., x_n$ với $n$ đối tượng dữ liệu. Khi đó giá trị trung bình của thuộc tính $X$ là:
$$
\overline{X} = \dfrac{\sum_{i=1}^n x_i}{n}
$$
>[!example]+ Ví dụ
>Suppose we have the following values for salary (in thousands of dollars), shown in increasing order: $30, 36, 47, 50, 52, 52, 56, 60, 63, 70, 70, 110$. Khi đó:
>$$
>\overline{X} = \dfrac{30 + 36 + 47 + 50 + 52 + 52 + 56 + 60 + 63 + 70 + 70 + 110}{12} = 58
>$$
### b. Trung vị (median)

>[!note] Giả sử dữ liệu được sắp tăng dần hoặc giảm dần (theo thứ tự).

- Là giá trị mà chia dữ liệu thành 2 phần, một phần thấp một phần cao (các giá trị phần thấp đều thấp hơn phần cao). 
- Nếu số lượng dữ liệu là lẻ thì median là giá trị **chính giữa**, nếu là chẵn thì median là trung bình của hai giá trị nằm giữa.

>[!example]+ Ví dụ
>Cho dữ liệu sau: $30, 36, 47, 50, 52, 52, 56, 60, 63, 70, 70, 110$. Do số lượng dữ liệu là chẵn nên lấy hai trung bình hai giá trị nằm giữa.
>$$
>\text{median} = \dfrac{52+56}{2} = 54
>$$

- Ví dụ nếu ta có rất nhiều dữ liệu thì khi đó tìm giá trị nằm giữa sẽ rất *expensive* do vậy ta sẽ không tìm trực tiếp mà **xấp xỉ** nó. Ta sẽ gộp dữ liệu lại thành từng khoảng, mỗi khoảng sẽ có tần số (số giá trị trong khoảng đó) rồi dùng công thức sau:
$$
\text{median} \approx L_1 + \dfrac{N/2 + (\sum \text{freq})_l}{\text{freq}_{\text{median}}} \times \text{width}
$$
- Trong đó:
	- $L_1$ là cận dưới của khoảng giá trị ở giữa (gọi là khoảng median).
	- $N$ là số lượng giá trị của cả dữ liệu.
	- $(\sum \text{freq})_l$ là tổng tần số của các khoảng nhỏ hơn khoảng median.
	- $\text{width}$ là độ rộng của khoảng median.
	- $\text{freq}_{\text{median}}$ là tần số của khoảng median.

>[!example]+ Ví dụ
>Giả sử ta có dữ liệu đánh giá IQ của 72.000 người, thay vì ghi ra là 72.000 dòng dữ liệu thì ta sẽ gộp chỉ số IQ theo các khoảng và số người (tần số) trong khoảng đó như sau:
> 
> | IQ      | Số người |
> | ------- | -------- |
> | 118-125 | 32.344   |
> | 126-133 | 13.433   |
> | 134-142 | 15.334   |
> | 143-149 | 8.234    |
> | 150-157 | 2.655    |
> 
> Khi đó:
> - $L_1 = 134$
> - $N = 72000$
> - $(\sum \text{freq})_l = 32344 + 13433$
> - $\text{width} = 142-134 = 8$
> - $\text{freq}_{\text{median}} = 15334$
> 
> Vậy:
> $$
> \text{median} \approx 134 + \dfrac{72000/2 + (32344+13433)}{15334} \times 8
> $$
### c. Mode

- (tiếng việt là số yếu vị) Là giá trị xuất hiện nhiều nhất trong dữ liệu (hay có tần số xuất hiện cao nhất).

>[!example]+ Ví dụ
>Ta có dữ liệu sau: $30, 36, 47, 50, 52, 52, 56, 60, 63, 70, 70$. Khi đó mode là $52$ và $70$ do $52$ với $70$ xuất hiện 2 lần (nhiều nhất).

- Dữ liệu mà có một mode thì được gọi là **unimodal**, đúng hai mode gọi là **bimodal**, nhiều hơn 2 là **bimodal**. Có thể nhìn hình dưới (điểm nhô lên cao là mode):

![Pasted image 20240229091103.png](/img/user/Attachment/Pasted%20image%2020240229091103.png)

- Nếu dữ liệu mà có mean, median với mode **đều nằm ở center** thì được gọi là **dữ liệu đối xứng**.
- Nếu $\text{mode} < \text{median}$ thì được gọi là **lệch dương** (positively skewed) (ngoài ra còn gọi là *lệch phải*).
- Nếu $\text{mode} > \text{median}$ thì được gọi là **lệch âm** (negatively skewed) (ngoài ra còn gọi là *lệch trái*).

![Pasted image 20240229092230.png](/img/user/Attachment/Pasted%20image%2020240229092230.png)
### d. Midrange
- Là giá trị trung bình giữa giá trị lớn nhất trong dữ liệu ($x_{\max}$) và nhỏ nhất trong dữ liệu ($x_{\min}$).
$$
\text{midrange} = \dfrac{x_{\max} - x_{\min}}{2} 
$$
## 2. Theo xu hướng phân tán

### a. Range

- Là hiệu giữa giá trị lớn nhất trong dữ liệu ($x_{\max}$) và nhỏ nhất trong dữ liệu ($x_{\min}$).
$$
\text{range} = x_{\max} - x_{\min}
$$
### b. Quartiles (tứ phân vị)

- 
### c. Variance (phương sai) và Standard Deviation (độ lệch chuẩn)

- 

# III. Phép đo độ tương đồng và khác biệt của dữ liệu

## 1. Proximity nominal


---

# References

- [Data Mining. Concepts and Techniques, 3rd Edition (The Morgan Kaufmann Series in Data Management Systems) (sabanciuniv.edu)](https://myweb.sabanciuniv.edu/rdehkharghani/files/2016/02/The-Morgan-Kaufmann-Series-in-Data-Management-Systems-Jiawei-Han-Micheline-Kamber-Jian-Pei-Data-Mining.-Concepts-and-Techniques-3rd-Edition-Morgan-Kaufmann-2011.pdf) (chương 2)
- Note trên lớp của bạn [Phạm Thái Huy](https://drive.google.com/file/d/1CYyAvVTZRllo2Js0npYOVF1x5YzQDLTd/view?usp=sharing)