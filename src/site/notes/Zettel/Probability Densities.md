---
{"dg-publish":true,"permalink":"/zettel/probability-densities/","noteIcon":"📝","created":"2024-04-19T10:19:39.732+07:00","updated":"2024-04-19T13:55:40.787+07:00"}
---

>[!example]+
>Giả sử mình đang xét biến ngẫu nhiên liên tục $X$ với $X$ đại diện cho chiều cao của công dân Việt Nam. Như thông thường, mình sẽ tìm xác suất $P(X = x)$ với $x$ là một số thực, nhưng ai lại quan tâm xác suất để chiều cao là $1.8072003 \hspace{3pt} (m)$ chứ 🥲. Vậy nên khi nói đến biến ngẫu nhiên liên tục, ta sẽ quan tâm xác suất để $X$ nằm trong một khoảng hơn, ví dụ xác suất để một công dân Việt Nam có chiều cao từ $1.6$ đến $1.9$, tức là $P(1.6 \leq X \leq 1.9)$. 

Xét $X$ là một biến ngẫu nhiên liên tục, nếu xác suất của $X$ nằm trong khoảng $(x, x + \delta x)$ được xác định bằng công thức $p(x)\delta x$ với $\delta x \to 0$, thì $p(x)$ được gọi là **mật độ xác suất** (probabilty density) trên $x$.

Xác suất để $x$ nằm trong khoảng $(a, b)$ được xác định bằng:
$$
p(x \in (a, b)) = p(a < x < b) = \int_{a}^{b} p(x)dx
$$
>[!danger]
>Mình cảm thấy kí hiệu khá là weird, thông thường người ta kí hiệu mật độ xác suất là $f(x)$. Nhưng tác giả kí hiệu hai xác suất trùng nhau, mặc dù nó khác nhau. Giả sử $p(x)$ (đang nói đến mật độ xác suất) sẽ có thể khác không, thế nhưng, mình sẽ đặt mật độ xác suất là $f(x)$, nguyên hàm là $F(x)$:
>$$
p(x) = p(x \in (x, x)) = \int_{x}^x f(x)dx = F(x) - F(x) = 0
>$$
>Xác suất $p(x)$ (mình đang nói đến xác suất nằm trong một khoảng) tại một điểm $x$ sẽ luôn là $0$ với mọi $x$.

>[!note]+
>![Pasted image 20240419135539.png](/img/user/Attachment/Pasted%20image%2020240419135539.png)

---

Phần trước: [[Zettel/Introduction (Prob)\|Introduction (Prob)]]
Phần sau: [[Zettel/Expectations and covariances\|Expectations and covariances]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.2)
- [The idea of a probability density function - Math Insight](https://mathinsight.org/probability_density_function_idea)
- [calculus - Intuitive idea behind the probability density function - Mathematics Stack Exchange](https://math.stackexchange.com/questions/709209/intuitive-idea-behind-the-probability-density-function)
- [integration - Change of variable in a probability density function - Mathematics Stack Exchange](https://math.stackexchange.com/questions/1424388/change-of-variable-in-a-probability-density-function)
- [3.7: Transformations of Random Variables - Statistics LibreTexts](https://stats.libretexts.org/Bookshelves/Probability_Theory/Probability_Mathematical_Statistics_and_Stochastic_Processes_(Siegrist)/03%3A_Distributions/3.07%3A_Transformations_of_Random_Variables)