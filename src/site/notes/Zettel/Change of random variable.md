---
{"dg-publish":true,"permalink":"/zettel/change-of-random-variable/","noteIcon":"📝","created":"2024-04-25T15:41:21.082+07:00","updated":"2024-05-15T21:34:03.565+07:00"}
---

Xét hai biến ngẫu nhiên $X$ và $Y$ với $X = g(Y)$. Đặt $F_{X}$ là cdf của $X$ và $F_{Y}$ là cdf của $Y$. Tương tự, ta đặt $f_{X}$ là mật độ xác suất của $X$ và $f_{Y}$ là mật độ xác suất của $Y$.

>[!danger]+ Lưu ý
>$g$ phải là một hàm khả nghịch ([[Zettel/Function and Inverse function\|Function and Inverse function]]).

Ta xét 2 trường hợp:
- Nếu $g$ là hàm đồng biến:
$$
\begin{aligned}
F_{X}(z) &= P(X < z) \\
&= P(g(Y) < z) \\ 
&= P(Y < g^{-1}(z)) \\
&= F_{Y}(g^{-1}(z))
\end{aligned}
$$
- Nếu $g$ là hàm nghịch biến:
$$
\begin{aligned}
F_{X}(z) &= P(X < z) \\
&= P(g(Y) < z) \\ 
&= P(Y > g^{-1}(z)) \\
&= 1 - P(Y < g^{-1}(z)) \\
&= 1 - F_{Y}(g^{-1}(z))
\end{aligned}
$$
Lấy đạo hàm $P_x(z)$ ta được:
- Nếu $g$ là hàm đồng biến:
$$
F'_{X}(z) = F'_{Y}(g^{-1}(z)) \frac{d}{dz}g^{-1}(z)
$$
- Nếu $g$ là hàm nghịch biến:
$$
F'_{X}(z) = -F'_{Y}(g^{-1}(z)) \frac{d}{dz}g^{-1}(z)
$$
- Kết hợp cả 2, ta được trường hợp tổng quát nếu $g$ là hàm đơn điệu (ngặt):
$$
F'_{X}(z) = F'_{Y}(g^{-1}(z)) |\frac{d}{dz}g^{-1}(z)|
$$

Thay biến $z$ thành $x$, ta được:
$$
\begin{aligned}
F'_{X}(x) &= F'_{Y}(g^{-1}(x)) \left| \frac{d}{dx}g^{-1}(x) \right| \\
&= F'_{Y}(y) \left| \frac{dy}{dx} \right| \\
\Leftrightarrow F'_{Y}(y) &= F'_{X}(x) \left| \frac{dx}{dy} \right| \\
&= F'_{X}(g(y)) \left| \frac{dg(y)}{dy} \right| \\
\implies f_{Y}(y) &= f_{X}(g(y)) | g'(y) |
\end{aligned}
$$

---
# References

- [integration - Change of variable in a probability density function - Mathematics Stack Exchange](https://math.stackexchange.com/questions/1424388/change-of-variable-in-a-probability-density-function)