---
{"dg-publish":true,"permalink":"/zettel/polynomial-curve-fitting/","created":"2024-04-15T11:06:21.892+07:00","updated":"2024-04-15T12:39:03.647+07:00"}
---

Giả sử bạn LN có số tiền là $x \in \mathbb{R}$ và LN muốn dự đoán xem với số tiền $x$ này, LN có thể mua được bao nhiêu cái bánh xèo, bởi vì bà bán bánh xèo bả không muốn tiết lộ giá 1 cái bánh xèo và giá có thể mỗi ngày thay đổi (nhưng bánh xèo ngon).

Gọi số bánh xèo mua được là $y \in \mathbb{R}$ (trong thực tế số bánh sẽ là số nguyên, nhưng mà mình giả sử bà bán bánh có khả năng nào đó bán được số bánh xèo là số thực).

>[!important]
>Bài toán dùng một giá trị đầu vào $x$ để dự đoán một giá trị số thực $y$ nào đó được gọi là bài toán **hồi quy** (regression).

Giả sử LN thu thập dữ liệu cho việc dự đoán của mình thông qua $N$ lần mua, đặt là $\mathbf{x} \equiv (x_1, ..., x_N)^T$. Với mỗi $x_i$, LN biết được số bánh xèo mua được là $y_i$, vậy ta có $\mathbf{y} \equiv (y_1, ..., y_N)^T$. Ta gọi dữ liệu mà LN thu thập được $\{ (x_1, y_1), ..., (x_N, y_N) \}$ là **tập huấn luyện** (training set). Dựa trên tập huấn luyện ấy, LN muốn dự đoán giá trị $\hat{y}$ cho một giá trị $\hat{x}$ mới (lần mua mới). Vì vậy LN cần tìm ra một mô hình nào đó, để khi đưa vào input $\hat{x}$, mô hình cho ra được giá trị $\hat{y}$ phù hợp.

![Pasted image 20240415114059.png](/img/user/Attachment/Pasted%20image%2020240415114059.png)
			Hình: Dữ liệu mà LN thu thập được sau $N = 10$ lần mua

>[!note]
>Đường cong màu xanh tương ứng với hàm $f(x) = \sin(2x) + 2$, mình dùng hàm này để sinh ra data, sau đó cộng thêm với giá trị random được lấy từ phân phối chuẩn với $\mu = 0$ và $\sigma = 0.3$ để cho ra các giá trị $y$ màu xanh lá. Mục đích của chúng ta là dựa trên data để tìm ra hàm $f$ tốt nhất, thế nhưng data thông thường sẽ có rất nhiều noise và hàm $f$ trong thực tế rất khó tìm.

>[!info]+ Code
>```python
>import numpy as np
>import matplotlib.pyplot as plt
>
>plt.style.use("ggplot")
>np.random.seed(1234)
>
>def f(x):
>	return np.sin(2*x) + 2
>	
>x = np.random.uniform(low=0, high=10, size=10)
>xs = np.linspace(0, 10, 1000)
>
>plt.scatter(x, f(x), color="blue")
>plt.scatter(x, f(x) + np.random.normal(0, 0.3, 10), marker="s", color="green")
>plt.plot(xs, f(xs), color="blue")
>plt.show()
>```

LN đoán rằng, việc dùng một hàm đa thức như dưới có thể dự đoán được số bánh:
$$
f(x, \mathbf{w}) = w_{0} + w_{1}x + \dots w_{M}x^M = \sum_{i=0}^M w_{i}x^i
$$
trong đó $\mathbf{w} = (w_0, w_1, ..., w_M)^T$ là bộ tham số của hàm đa thức $f(x, \mathbf{w})$ mà LN chọn.

---

Phần sau: [[Zettel/Probability Theory (Bishop)\|Probability Theory (Bishop)]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.1)
- [ISLR] Introduction to Statistical Learning