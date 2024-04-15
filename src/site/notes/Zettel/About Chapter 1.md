---
{"dg-publish":true,"permalink":"/zettel/about-chapter-1/","created":"2024-04-15T16:40:01.637+07:00","updated":"2024-04-15T19:30:00.573+07:00"}
---

## Phân phối nhị thức (binomial distribution)

Một đồng xu không đồng chất (tức là xác suất ra mặt ngửa và mặt xấp không đều nhau) có xác suất ra mặt ngửa là $f$. Đặt biến ngẫu nhiên $X$ là số mặt ngửa khi tung đồng xu $N$ lần, khi đó, phân phối xác suất của $X$ sẽ là:
$$
P(X = r \mid f, N) = P(r \mid f, N) = {N \choose r} f^r (1-f)^{N- r} 
$$
`\begin{proof}`
Giả sử rằng mỗi lần tung đồng xu là độc lập với nhau, đặt biến cố lần tung đầu tiên là $A_1$, tương tự, tung lần thứ $i$ là $A_i$ và tung sau $N$ là $A$ vậy:
$$
P(A) = P(A_{1} \cap \dots \cap A_{n}) = P(A_{1})\dots P(A_{n})
$$
Vậy nếu tung $N$ lần, trong đó $r$ lần là mặt ngửa, tức là tại lần $i$ nào đó, ta tung được mặt ngửa, tức là $P(A_i) = f$, có $r$ lần như vậy. Ngoài ra khi tung $N$ lần mà $r$ lần mặt ngửa nên $N-r$ lần còn lại là mặt xấp với xác suất $1-f$. 
$$
(A) = f^r (1-f)^{N-r}
$$
Nếu ta xem mỗi lần tung thứ $i$ là một "ô" thứ $i$ trong $N$ ô, thì số cách mà tung $N$ lần có $r$ mặt ngửa ta xem như số cách để chọn $r$ ô trong $N$ ô, vậy số cách sẽ là:
$$
N \choose r
$$
Do $P(A)$ chỉ là xác suất của 1 cách trong $N \choose r$ cách, vì vậy, xác suất để mặt ngửa xuất hiện $r$ lần trong $N$ lần tung là:
$$
{N \choose r} f^r (1-f)^{N-r}
$$
`\end{proof}`
Trung bình của phân phối trên, kí hiệu là $\mathcal{E}[r]$, được định nghĩa như sau:
$$
\mathcal{E}[r] \equiv \sum_{r=0}^N P(r \mid f, N)r
$$
>[!thm]
>Với $n$ biến ngẫu nhiên $x_1, x_2, ..., x_n$, ta có:
>$$
>\mathcal{E}\left[ \sum_{i=1}^n \right] = \sum_{i=1}^n \mathcal{E}[x_{i}]
>$$



---

Phần sau:

---
# References

- [Deriving the Binomial PMF (dcgerard.github.io)](https://dcgerard.github.io/stat234/14_binomial_distribution.pdf)
- Information Theory, Inference and Learning Algorithms - MacKay (chapter 1)