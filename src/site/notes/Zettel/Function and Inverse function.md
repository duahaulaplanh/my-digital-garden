---
{"dg-publish":true,"permalink":"/zettel/function-and-inverse-function/","noteIcon":"📝","created":"2024-04-25T15:44:39.064+07:00","updated":"2024-04-25T18:52:46.015+07:00"}
---

Cho $X$ và $Y$ là hai tập hợp. Ta gọi một quan hệ ([[Zettel/Equivalence relation\|Equivalence relation]]) $f$ từ $X$ đến $Y$ là một **hàm số** nếu với mỗi phần tử $x \in X$ thì chỉ có một và chỉ một phần tử $y \in Y$ tương ứng. 

>[!example]+
>Xét $x_{1} \neq x_{2}$ và $x_{1}, x_{2} \in X$ nếu $(x_{1}, y) \in f$ và $(x_{2}, y) \in f$ với $y \in Y$ thì $f$ không làm hàm số.

>[!example]+
>Xét $X = \{ 1, 2, 3 \}$ và $Y = \{ 1, 2 \}$. Khi đó $f = \{ (1, 1), (2, 2) \}$ được gọi là một hàm số.

Ta viết $f: X \to Y$ để chỉ rằng hàm số $f$ từ $X$ đến $Y$. Nếu ta viết $f(x)$ thì nghĩa là giá trị của $f$ tại $x$ và $f(x) \in Y$.

Ta gọi tập hợp $X$ là **tập xác định** (domain) của $f$ và $Y$ là **tập hợp đích** (codomain) của $f$. Ta định nghĩa một tập hợp, kí hiệu là $\text{im}(f)$:
$$
\text{im}(f) \coloneqq \{ y \in Y \mid \exists x \in X \hspace{3pt} \text{s.t.} \hspace{5pt} y = f(x) \}
$$
và tập hợp $\text{im}(f)$ được gọi là **ảnh** (image) của $f$. Ngoài ra ta cũng có thể gọi $\text{im}(f)$ là **miền giá trị** (range) của $f$.

![Pasted image 20240425160554.png](/img/user/Attachment/Pasted%20image%2020240425160554.png)

Ta nói hàm số $f: X \to Y$ là **đơn ánh** (injective) nếu với mỗi $u, v \in X$, $u = v$ thì $f(u) = f(v)$, là **toàn ánh** (surjective) nếu $\text{im}(f) = Y$ và là **song ánh** (bijective) nếu $f$ vừa là đơn ánh, vừa là toàn ánh.

---
# References

- [Analysis I: Amann, Herbert, Escher, Joachim, Brookfield, Gary: 9783764371531: Amazon.com: Books](https://www.amazon.com/Analysis-I-Herbert-Amann/dp/3764371536) (chapter 1)