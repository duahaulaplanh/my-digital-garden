---
{"dg-publish":true,"permalink":"/zettel/hinh-hoc-chieu/","created":"2024-03-20T00:13:20.862+07:00","updated":"2024-04-06T15:29:05.554+07:00"}
---

- Như chúng ta đã biết, một điểm trong mặt phẳng được viết là $(x, y)$ (trong $\mathbb{R}^2$). Còn nếu ta xem $\mathbb{R}^2$ là một không gian vector thì khi đó **một điểm được xem như một vector**.
- Các vector được ký hiệu bằng chữ in hoa, ví dụ như $\mathbf{x}$ và **mặc định vector là vector cột**, do đó một vector sẽ được viết là $(x, y)^T$, mà một điểm $\Leftrightarrow$ một vector nên ta cũng viết là $(x, y)^T$ thay vì $(x, y)$ như trước.
## 1. Đường thẳng và điểm

**Biểu diễn đồng nhất của đường thẳng** (Homogeneous representation of lines):
- Trong $\mathbb{R}^2$, một đường thẳng sẽ có dạng $ax + by + c = 0 \Rightarrow (x, y, 1)(a, b, c)^T = 0$. Ta có thể thấy một đường thẳng được xác định bằng vector $(a, b, c)^T$. 
- Ta có thể thấy hai đường thẳng $ax + by + c = 0$ và $k(ax + by + c) = (ka)x + (kb)y + (kc) = 0$ giống nhau với mọi $k \neq 0$. Do đó hai vector $(a, b, c)^T$ và $k(a, b, c)^T$ biểu diễn cùng một đường thẳng. 
- Xét quan hệ $\sim$ trên không gian vector $\mathbb{R}^3 \setminus (0, 0, 0)^T$ sao cho hai vector $(a, b, c)^T \sim (d, e, f)^T$ khi $(a, b, c)^T = \lambda (d, e, f)^T$, rõ ràng $\sim$ là một quan hệ tương đương. Những vector mà tương đương với nhau thông qua $\sim$ được gọi là các **vector đồng nhất** (homogenous vector).
>[!note]+ Chứng minh tương đương
>- [[Zettel/Định nghĩa tương đương\|Định nghĩa tương đương]]
>- Đặt $\mathbf{a} = (a_1, a_2, a_3)^T, \mathbf{b} = (b_1, b_2, b_3)^T, \mathbb{c} =  (c_1, c_2, c_3)^T$. 
>- Ta có thể thấy: 
>	- $a \sim a$ bởi vì $(a_1, a_2, a_3)^T = \lambda (a_1, a_2, a_3)^T$ với $\lambda = 1$.
>	- Giả sử $a \sim b$ khi đó $(a_1, a_2, a_3)^T = \lambda (b_1, b_2, b_3)^T$. Đặt $\lambda' = 1/\lambda$, do đó $(b_1, b_2, b_3)^T = \lambda' (a_1, a_2, a_3)^T$  vậy $b \sim a$.
>	- Giả sử $a \sim b$ với  $(a_1, a_2, a_3)^T = \lambda_1 (b_1, b_2, b_3)^T$ và $b \sim c$ với $(b_1, b_2, b_3)^T = \lambda_2 (c_1, c_2, c_3)^T$. Do đó $(a_1, a_2, a_3)^T = \lambda_1 \lambda_2 (c_1, c_2, c_3)^T$, vậy $a \sim c$.
>- Do đó $\sim$ là một quan hệ tương đương.
- Tập hợp các lớp tương đương được xác định bởi $\sim$ của các vector trong $\mathbb{R}^3 \setminus (0, 0, 0)^T$ tạo thành **mặt phẳng chiếu** (projective plane) $\mathbb{P}^2$. Nghĩa là $\mathbb{P}^2$ là tập hợp các đường thẳng trong mặt phẳng 2-chiều, mỗi đường thẳng được biểu diễn bằng một vector 3-chiều.

**Biểu diễn đồng nhất của điểm**: 
- Một điểm $(x, y)^T$ nằm trên đường thẳng $\mathbf{l} = (a, b, c)^T$ nếu $ax + by + c = 0 \Rightarrow (x, y, 1)(a, b, c)^T = 0 \Rightarrow (x, y, 1)\mathbf{l} = 0$. 
- Ta có thể thấy điểm $(x, y)^T$ 2-chiều được biểu diễn trên đường thẳng thành vector $(x, y, 1)^T$ 3-chiều bằng cách thêm $1$ vào chiều mới.
- Theo cách hiểu như trên, nếu ta có một vector $(a, b, 1)^T$ 3-chiều, nó sẽ biểu diễn cho điểm $(a, b)^T$ 2-chiều.
- Hơn nữa, phương trình $k(x, y, 1)\mathbf{l} = (kx, ky, k)\mathbf{l} = 0$ khi và chỉ khi $(x, y, 1)\mathbf{l} = 0$. Do đó hai vector $(kx, ky, k)^T$ và $(x, y, 1)^T$ đều thoả mãn đường thẳng $\mathbf{l}$ nên ta có thể xem hai vector đó cùng đại diện cho điểm $(x, y)^T$ trong $\mathbb{R}^2$. 
- Vậy cũng giống như một đường thẳng, một điểm được đại diện bởi một vector đồng nhất (với chiều lớn hơn nó).
>[!example]+ Ví dụ
>Một vector $(x_1, x_2, x_3)^T$ trong $\mathbb{R}^3$ sẽ đại diện cho điểm $(x_1/x_3, x_2/x_3)^T$ trong $\mathbb{R}^2$ do $(x_1, x_2, x_3)^T \sim (1/x_3)(x_1/x_3, x_2/x_3, 1)^T$.

- Xét một điểm $(a, b)^T$ trong $\mathbb{R}^2$ và có một vector $\mathbf{x} = (d, e, f)^T$ trong $\mathbb{R}^3$ đại diện cho điểm đó thì ta gọi $\mathbf{x}$ là **toạ độ đồng nhất** của điểm đó. Do đó khi ta nói đến một điểm nhưng sử dụng kí hiệu cho vector (chữ in hoa) thì ta sẽ hiểu là đang dùng vector đại diện cho điểm đó.

>[!summary]+ Kết luận
>Một điểm $\mathbf{x}$ nằm trên đường thẳng $\mathbf{l}$ khi và chỉ khi $\mathbf{x}^T\mathbf{l} = 0$.

>[!note]
>Vậy có 2 cách biểu diễn một đường thẳng và điểm:
>- *Không đồng nhất* : $ax + by + c = 0$ với điểm là $(x, y)^T$.
>- *Đồng nhất* : $\mathbf{x}^T\mathbf{l} = 0$ với điểm là $\mathbf{x} = (x, y, 1)^T$ và $\mathbf{l} = (a, b, c)^T$.

**Hệ số tự do** (degree of fredom - **dof**):

---
# References

- [Multiple View Geometry in Computer Vision, Second Edition (r-5.org)](http://www.r-5.org/files/books/computers/algo-list/image-processing/vision/Richard_Hartley_Andrew_Zisserman-Multiple_View_Geometry_in_Computer_Vision-EN.pdf) (Part 0)