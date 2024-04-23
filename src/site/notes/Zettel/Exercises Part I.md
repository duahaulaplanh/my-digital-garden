---
{"dg-publish":true,"permalink":"/zettel/exercises-part-i/","noteIcon":"📝","created":"2024-04-23T09:04:07.504+07:00","updated":"2024-04-23T11:02:01.692+07:00"}
---

>[!example]+ Giải bài 1.1
>
>![Pasted image 20240423100559.png](/img/user/Attachment/Pasted%20image%2020240423100559.png)

Phương trình (1.1) như sau:
$$
y(x, \mathbf{w}) = \sum_{j=0}^M x^j w_{j}
$$
Phương trình (1.2) như sau:
$$
E(\mathbf{w}) = \frac{1}{2} \sum_{n=1}^N \left\{ y(x_{n}, \mathbf{w}) - t_{n} \right\}^2
$$
với $(x_1, \dots, x_{n})$ là các dữ liệu, $(t_{1}, \dots, t_{n})$ là các nhãn (hay là target) và $\mathbf{w}$ là bộ tham số. Để cực tiểu được hàm lỗi $E(\mathbf{w})$, ta chỉ cần tìm giá trị $\hat{\mathbf{w}} = (\hat{w}_{1}, \dots, \hat{w}_{M})^T$, sao cho:
$$
\nabla E(\hat{\mathbf{w}}) = \mathbf{0}
$$
với $\mathbf{0}$ là vector $0$. Do $\nabla E(\mathbf{w})$ là một vector nên để vector bằng $0$ thì từng phần tử bằng $0$, vậy ta cần tìm $\hat{w}_{i}$ sao cho:
$$
\frac{\partial{E(\hat{\mathbf{w}})}}{\partial w_{i}} = 0
$$
Giờ bắt đầu biến đổi để tìm được $\hat{w}_i$ thôi nào. Ta có:
$$
\begin{aligned}
\frac{\partial{E(\hat{\mathbf{w}})}}{\partial w_{i}} &= \frac{1}{2} \sum_{n=1}^N \frac{\partial \{y(x_{n}, \mathbf{w}) - t_{n}\}^2}{\partial w_{i}} \\
&= \frac{1}{2} \sum_{n=1}^N \left[ \frac{\partial y(x_{n}, \mathbf{w})^2}{\partial w_{i}} - 2t_{n} \frac{\partial y(x_{n}, \mathbf{w})}{\partial w_{i}} + \frac{\partial t_{n}^2}{\partial w_{i}} \right] \\
&= \frac{1}{2} \sum_{n=1}^N \left[ 2y(x_{n}, \mathbf{w})\frac{\partial y(x_{n}, \mathbf{w})}{\partial w_{i}} - 2t_{n}x_{n}^i +0 \right] \\
&= \frac{1}{2} \sum_{n=1}^N [2y(x_{n}, \mathbf{w})x_{n}^i -2t_{n}x_{n}^i] \\
&= \sum_{n=1}^N \left[ \sum_{j=0}^M x_{n}^{i+j} w_{j} \right] - \sum_{n=1}^Nt_{n}x_{n}^i
\end{aligned}
$$
Ở phương trình trên, tách phần trước dấu trừ, ta được:
$$
\begin{aligned}
\sum_{n=1}^N \left[ \sum_{j=0}^M x_{n}^{i+j} w_{j} \right] &= \sum_{n=1}^N (x_{n}^{i}w_{0} + \dots x_{n}^{i+M}w_{M}) \\
&= \sum_{n=1}^N x_{n}^iw_{0} + \dots + \sum_{n=1}^N x_{n}^{i+M}w_{M} \\
&= \sum_{j=0}^M \left( \sum_{n=1}^N x_{n}^{i+j} \right) w_{j}
\end{aligned}
$$
Thay vào lại phương trình chỗ ta có:
$$
\begin{aligned}
\frac{\partial{E(\hat{\mathbf{w}})}}{\partial w_{i}} &= \sum_{n=1}^N \left[ \sum_{j=0}^M x_{n}^{i+j} w_{j} \right] - \sum_{n=1}^Nt_{n}x_{n}^i \\
&= \sum_{j=0}^M \left( \sum_{n=1}^N x_{n}^{i+j} \right) w_{j} - \sum_{n=1}^N t_{n}x_{n}^i
\end{aligned}
$$
Đặt $\sum_{n=1}^N x_{n}^{i+j} = A_{ij}$ và $\sum_{n=1}^Nt_{n}x_{n}^i = T_{i}$. Khi đó:
$$
\begin{aligned}
\frac{\partial E(\mathbf{w})}{\partial w_{i}} &= 0 \\
\Leftrightarrow \sum_{j=0}^M A_{ij}w_{j} &= T_{i}
\end{aligned}
$$
Vậy giá trị $\hat{w}_i$ cần tìm chính là nghiệm của phương trình trên.

>[!example]+ Giải bài 1.2
>
>![Pasted image 20240423100741.png](/img/user/Attachment/Pasted%20image%2020240423100741.png)

Phương trình (1.122) là phương trình nghiệm $\hat{w}_i$ ở bài 1.1. Còn phương trình (1.4) như sau:
$$
\tilde{E}(\mathbf{w}) = \frac{1}{2} \sum_{n=1}^N \{y(x_{n}, \mathbf{w}) - t_{n}\}^2 + \frac{\lambda}{2}||\mathbf{w||^2}
$$
trong đó $||\mathbf{w}||$ được gọi là **chuẩn** của vector $\mathbf{w}$ và có công thức là:
$$
||\mathbf{w}|| = \sqrt{ w_{0}^2 + \dots + w_{M}^2 }
$$
Ta có:
$$
\begin{aligned}
\frac{\partial{E(\hat{\mathbf{w}})}}{\partial w_{i}} &= \frac{1}{2} \sum_{n=1}^N \frac{\partial \left( \{y(x_{n}, \mathbf{w}) - t_{n}\}^2 +\frac{\lambda}{2}||\mathbf{w}|| \right)}{\partial w_{i}} \\
&= \frac{1}{2} \sum_{n=1}^N \left[ \frac{\partial y(x_{n}, \mathbf{w})^2}{\partial w_{i}} - 2t_{n} \frac{\partial y(x_{n}, \mathbf{w})}{\partial w_{i}} + \frac{\partial t_{n}^2}{\partial w_{i}} + \frac{\lambda}{2} \frac{\partial||\mathbf{w}||^2}{\partial w_{i}} \right] \\
&= \sum_{j=0}^M A_{ij}w_{j} -T_{i} + \sum_{n=1}^N \lambda w_{i} \\
&= \sum_{j=0}^M A_{ij}w_{j} -T_{i} + N\lambda w_{i} \\
\end{aligned}
$$
Vậy giá trị $\hat{w}_i$ chính là nghiệm của phương trình:
$$
\sum_{j=0}^M A_{ij}w_{j} + N\lambda w_{i} = T_{i}
$$

>[!example]+ Giải bài 1.3
>
>![Pasted image 20240423103443.png](/img/user/Attachment/Pasted%20image%2020240423103443.png)

Bài này giải khá tương tự bài trong phần [[Zettel/Introduction (Prob)\|Introduction (Prob)]]. Mình đặt biến ngẫu nhiên $B$ đại diện cho các hộp màu, biến ngẫu nhiên $F$ đại diện cho trái cây, $F= a$ là trái táo (apple), $F = o$ là trái cam (orange) và $F = l$ là trái chanh (lime). Ta có:
$$
\begin{aligned}
p(B = r) &= 0.2 \\
p(B = b) &= 0.2 \\
p(B = g) &= 0.6
\end{aligned}
$$
Tiếp theo, ta có xác suất chọn được trái táo khi đã chọn được một hộp màu lần lượt là:
$$
\begin{aligned}
p(F = a \mid B = r) &= \frac{3}{10} = 0.3 \\
p(F = a \mid B = b) &= \frac{1}{2} = 0.5 \\
p(F = a \mid B = g) &= \frac{3}{10} = 0.3
\end{aligned}
$$
Dùng sum rule, ta lại có:
$$
\begin{aligned}
p(F = a) &= \sum_{B} p(F=a, B) \\
&= \sum_{B} p(F=a \mid B)p(B) \\
&= p(F=a \mid B = r)p(B = r) + p(F=a \mid B=b)p(B=b) \\
&+ p(F=a \mid B=g)p(B = g) \\
&= 0.3 \times 0.2 + 0.5 \times 0.2 + 0.3 \times 0.6 \\
&= 0.34
\end{aligned}
$$
Vậy xác suất để chọn được một quả táo là $0.34$. Để tìm xác suất hộp ta chọn là hộp xanh lá $g$ khi đã chọn được quả táo, ta tìm xác suất $p(B = g \mid F = a)$ bằng cách dùng định lý Bayes:
$$
p(B = g \mid F= a) = \frac{p(F=a \mid B=g)p(B =g)}{p(F=a)} = \frac{0.3 \times 0.6}{0.34} \approx 0.52
$$

---

Phần trước: 
Phần sau: 

---
# References

- [Bishop] Pattern Recoginition and Machine Learning (exercises of I.Introduction).
- [prml-web-sol.dvi (microsoft.com)](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/05/prml-web-sol-2009-09-08.pdf)