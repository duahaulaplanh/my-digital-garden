---
{"dg-publish":true,"permalink":"/zettel/xu-ly-du-lieu/","created":"2024-03-06T12:06:48.224+07:00","updated":"2024-03-10T15:16:47.165+07:00"}
---

# I. Xử lý dữ liệu

## 1. Thiếu/mất dữ liệu 

Cho tập dữ liệu sau:

| Tên | Lương ($) |
| --- | --------- |
| A   | NULL      |
| B   | 1000      |
| C   | 200       |
| D   | NULL      |
| E   | NULL      |

Dựa vào bảng trên, ta có thể thấy ở thuộc tính *lương*, nhân viên $A$ và $B$ bị thiếu/mất dữ liệu. Để xử lý vấn đề này, ta có nhiều phương pháp:
- **Bỏ qua những bản ghi bị thiếu dữ liệu**: Dễ hiểu, ta bỏ luôn $A$ và $D$ khỏi tập dữ liệu trên, giữ lại $B, C, E$. Thế nhưng phương pháp này không hiệu quả, ví dụ có quá nhiều hàng dữ liệu thiếu mà bỏ hết thì toang 🥲.
- **Điền vào dữ liệu thiếu một cách thủ công**: Thủ công ở đây nghĩa là ta sẽ đi khảo sát nhân viên $A$ và $D$ để điền lại dữ liệu thiếu (hoặc cách khác) nhưng cách này sẽ rất mất thời gian.
- **Dùng hằng số toàn cục để điền vào vị trí thiếu**:  Ví dụ như ta chọn giá trị NULL là $-\infty$ hoặc $\infty$ hoặc là gì đó (giả sử $-1$) và sau đó điền tất cả NULL bằng giá trị ta chọn. Giả sử ta điền NULL là $\infty$ sau đó dùng thuật toán ML lên dữ liệu, lúc này thuật toán sẽ hiểu giá trị NULL mà ta điền rất quan trọng (có giá trị lớn = $\infty$) nhưng mà thực tế thì hên xui.
- **Sử dụng mean hoặc median để điền vào vị trí thiếu**: Đối với *data đối xứng* thì ta có thể dùng mean, còn nếu data bị *lệch* (âm hoặc dương) thì điền median sẽ tốt hơn.
- **Sử dụng mean hoặc median của thuộc tính của các mẫu mà cùng một label**: Thay vì điền mean của tất cả các mẫu cùng thuộc tính (ví dụ *lương*), ta chỉ điền mean của các mẫu mà *cùng label* với mẫu ta đang xét (ví dụ mean của thuộc tính *lương* của những mẫu cùng thuộc label *nghèo* 🥲).
- **Sử dụng giá trị phù hợp nhất để điền**: Lúc này ta sẽ dùng đến những thuật toán ML (hoặc gì đó khác) để tìm ra trị phù hợp rồi điền vào (ví dụ như *decision trees*, *regression*, ...).
## 2. Dữ liệu bị nhiễu (noise)

Xét tập dữ liệu sau đây, với thuộc tính *play* là label.

| ID  | outlook  | temperature | humidity | windy | windspeed | play |
| --- | -------- | ----------- | -------- | ----- | --------- | ---- |
| 1   | overcast | hot         | high     | FALSE | 10        | yes  |
| 2   | overcast | cool        | normal   | TRUE  | 14        | yes  |
| 3   | overcast | mild        | high     | TRUE  | 24        | yes  |
| 4   | rainy    | mild        | high     | FALSE | 12        | yes  |
| 5   | rainy    | cool        | normal   | TRUE  | 543       | no   |
| 6   | rainy    | mild        | high     | TRUE  | 27        | no   |
| 7   | sunny    | hot         | high     | FALSE | 39        | no   |
| 8   | sunny    | hot         | high     | FALSE | 39        | yes  |
| 9   | sunny    | mild        | normal   | TRUE  | 10        | yes  |

- Ta có thể thấy:
	- Mẫu 7 và 8 có các giá trị thuộc tính như nhau thế nhưng label lại khác, ta xem đây là một dữ liệu *nhiễu* và thuộc dạng *class noise*.
	- Tiếp theo mẫu 5 có giá trị *windspeed = 543* cao bất thường so với các mẫu còn lại, đây cũng là một dữ liệu *nhiễu* và thuộc dạng *attribute noise*. 

>[!note] 
>Thông thường các noise sẽ chiếm từ vài phần trăm trong dữ liệu (nếu nhiều hơn thì nó là real đấy không phải noise đâu).
### a. Binning 
- Hay còn gọi là *chia bin*, mục đích chia giá trị thuộc tính thành các *bin*, mỗi *bin* chứa số lượng giá trị bằng nhau (riêng bin cuối cùng thì ít hơn cũng được, ví dụ có 14 bin, mỗi bin là 3 thì bin cuối cùng là 2). Sau đó thay thế các dữ liệu trong bin bằng một giá trị mới.
- Đầu tiên sắp xếp thuộc tính có dữ liệu bị nhiễu (ở đây là *windspeed*) tăng dần, vậy ta có $[10, 10, 12, 14, 24, 27, 39, 39, 543]$. Sau đó chọn độ lớn cho bin (thường là chia đều) ở đây là $9$ giá trị nên chọn size bin là $3$ vậy có $3$ bin tất cả.
$$
\begin{aligned}
\text{bin1} &= [10, 10, 12] \\
\text{bin2} &= [14, 24, 27] \\
\text{bin3} &= [39, 39, 543]
\end{aligned}
$$
- Sau đó thay thế giá trị trong bin bằng các phương pháp sau:
	- **Thay thế bằng mean của bin**: Ta có $\text{mean}(\text{bin1}) = (10 + 10 + 12) / 3 \approx 10.67$ vậy $\text{bin1} = [10.67, 10.67, 10.67]$ tương tự với $\text{bin2}$ và $\text{bin3}$.
	- **Thay thế bằng median của bin**: tương tự mean.
	- **Thay thế bằng giá trị biên**: Các giá trị biên của một bin là giá trị lớn nhất và nhỏ nhất của bin đó và sau đó thay thế từng giá trị trong bin bằng giá trị biên gần nó nhất. Xét ví dụ $\text{bin2}$ thì $\max = 27$ và $\min = 14$, lúc này ta có $\text{bin2} = [14, 27, 27]$ (ta thay thế $24 \to 27$ vì $24$ gần $27$ hơn là $14$).

>[!example]+ Ví dụ
>
>| ID  | windspeed |
>| --- | --------- |
>| 1   | 10        |
>| 2   | 14        |
>| 3   | 24        |
>| 4   | 12        |
>| 5   | 543       |
>| 6   | 27        |
>| 7   | 39        |
>| 8   | 39        |
>| 9   | 10        |
>
>Chọn phương pháp thay thế bằng giá trị mean và size của bin = 3, khi đó:
>
>| ID  | windspeed (after) | bin | windspeed (before)
>| --- | --------- | --- | --- |
>| 1   | 10.67        | 1 | 10 |
>| 9  | 10.67       | | 10 |
>| 4  | 10.67        | | 12 |
>| 2   | 22.7        | 2 | 14 |
>| 3   | 22.7   | |  24 |
>| 6   | 22.7       | |  27 |
>| 7   | 207        | 3 | 39 |
>| 8   | 207      | | 39 |
>| 5  | 207        | | 543 |e
>
>Cuối cùng ta được:
>
>| ID  | windspeed |
>| --- | --------- |
>| 1   | 10 .67  |
>| 2   | 22.7    |
>| 3   | 22.7    |
>| 4   | 10.67   |
>| 5   | 207    |
>| 6   | 22.7       |
>| 7   | 207       |
>| 8   | 207        |
>| 9   | 10.67      |

### b. Gom nhóm (Clustering)

Các giá trị gần nhau sẽ được gom thành một nhóm, còn các giá trị *không có nhóm* thì được xem như là *ngoại lai* (outlier, cũng là cách gọi khác của noise) thì ta có thể xem xét bỏ nó luôn.

![Pasted image 20240310140642.png](/img/user/Attachment/Pasted%20image%2020240310140642.png)

Lấy ví dụ hình trên, sau khi thực hiện clustering ta được 3 nhóm (3 hình tròn), các dữ liệu còn lại (nằm ngoài hình tròn) là outlier.
### c. Hồi quy 

- Đầu tiên dùng hồi quy tuyến tính để tìm ra một hàm dựa trên thuộc tính bị noise.
- Sau đó dựa vào hàm này để tìm ra giá trị mới cho các mẫu mà tại thuộc tính ta vừa tìm bị noise.
## 3. Tích hợp dữ liệu (data integration)

>[!warning]
>Mình chưa biết viết gì vào đây

# II. Biến đổi dữ liệu (Data Transformation)

## 1. Chuẩn hoá (normalization)

Xét một thuộc tính $A$ nào đó, gọi giá trị của mẫu $i$ tại $A$ là $v_i$.

**Chuẩn hoá min-max**: 
- Ta có giá trị lớn nhất của $A$ là $\max_A$ và nhỏ nhât là $\min_A$. Chuẩn hoá min-max sẽ đưa mỗi giá trị $v_i$ có miền là $[\min_A, \max_A]$ thành $v_i'$ nằm trong miền $[\text{new\_min}_A, \text{new\_max}_A]$:
$$
v_i' = \dfrac{v_i - \min_A}{\max_A - \min_A}(\text{new\_max}_A - \text{new\_min}_A) + \text{new\_min}_A
$$
- Ta có thể thấy chuẩn hoá min-max biến đổi tuyến tính $v_i$ thành $v_i'$ thế nên các mối quan hệ giữa các giá trị gốc $v_i$ vẫn được giữ nguyên.

**Chuẩn hoá z-score**:
- Các giá trị $v_i$ sẽ được chuẩn hoá dựa trên mean và độ lệch chuẩn của $A$:
$$
v_i' = \dfrac{v_i - \overline{A}}{\sigma_A}
$$
- Z-score được dùng thay min-max nếu ta không biết được min/max của $A$ hoặc có các outlier quá lớn (hoặc quá nhỏ) làm ta nhầm tưởng bọn outlier đó là min/max của $A$.

**Chuẩn hoá bằng tỉ lệ thập phân**:
- Phương pháp này chuẩn hoá bằng cách "di chuyển" điểm thập phân (dấu chấm) của các giá trị trong $A$.
- Đầu tiên tìm giá trị tuyệt đối lớn nhất trong $A$, gọi là $\text{max\_abs}_A$. Sau đó tìm giá trị $j$ nhỏ nhất sao cho:
$$
\dfrac{\text{max\_abs}_A}{10^j} < 1
$$
- Cuối cùng ta chuẩn hoá như sau:
$$
v_i' = \dfrac{v_i}{10^j}
$$

>[!example]+ Ví dụ
>Giả sử $A = [-986, 917]$ khi đó $\text{max\_abs}_A = 986$ do $|-986| > |917|$. Với $j = 3, 4, ...$ thì:
>$$
>\dfrac{986}{10^j} < 1
>$$ 
>Vậy ta chọn $j = 3$ (nhỏ nhất), sau đó ta chuẩn hoá được $A = [-0.986, 0.917]$.


---
# References

- Slide của bạn Minh Khuê
- Data Mining: Concepts and Techniques (4th edition) (chương 2)
- [Noisy Data in Data Mining | Soft Computing and Intelligent Information Systems (ugr.es)](https://sci2s.ugr.es/noisydata)