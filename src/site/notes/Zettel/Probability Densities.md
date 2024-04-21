---
{"dg-publish":true,"permalink":"/zettel/probability-densities/","noteIcon":"📝","created":"2024-04-19T10:19:39.732+07:00","updated":"2024-04-21T12:37:42.438+07:00"}
---

>[!example]+
>Giả sử mình đang xét biến ngẫu nhiên liên tục $X$ với $X$ đại diện cho chiều cao của công dân Việt Nam. Như thông thường, mình sẽ tìm xác suất $P(X = x)$ với $x$ là một số thực, nhưng ai lại quan tâm xác suất để chiều cao là $1.8072003 \hspace{3pt} (m)$ chứ 🥲. Vậy nên khi nói đến biến ngẫu nhiên liên tục, ta sẽ quan tâm xác suất để $X$ nằm trong một khoảng hơn, ví dụ xác suất để một công dân Việt Nam có chiều cao từ $1.6$ đến $1.9$, tức là $P(1.6 \leq X \leq 1.9)$. 

Xét $X$ là một biến ngẫu nhiên liên tục, nếu xác suất của $X$ nằm trong khoảng $(x, x + \delta x)$ được xác định bằng công thức $p(x)\delta x$ với $\delta x \to 0$, thì $p(x)$ được gọi là **mật độ xác suất** (probabilty density) trên $x$.

Xác suất để $x$ nằm trong khoảng $(a, b)$ được xác định bằng:
$$
p(x \in (a, b)) = p(a < x < b) = \int_{a}^{b} p(x)dx
$$
>[!danger]
>Mình cảm thấy kí hiệu khá là weird, thông thường người ta kí hiệu mật độ xác suất là $f(x)$. Nhưng tác giả kí hiệu hai xác suất trùng nhau, mặc dù nó khác nhau. Giả sử $p(x)$ (đang nói đến mật độ xác suất) có thể khác không, thế nhưng (mình sẽ đặt mật độ xác suất là $f(x)$, nguyên hàm là $F(x)$):
>$$
p(x) = p(x \in (x, x)) = \int_{x}^x f(x)dx = F(x) - F(x) = 0
>$$
>Xác suất $p(x)$ (mình đang nói đến xác suất nằm trong một khoảng) tại một điểm $x$ sẽ luôn là $0$ với mọi $x$.
>
>Nhưng mà ta sẽ theo tác giả nhé, mình nghĩ khi tác giả nói đến $p(x)$ (với $x$ là số thực) thì $p(x)$ là mật độ xác suất, còn nói đến $p(x \in (a, b))$ thì tức là xác suất $x$ thuộc đoạn nào đó.

>[!note]+
>Như đã nói phía trên $p(x) = 0$ với mọi $x$, do đó $p(a) = p(b) = 0$ nên:
>$$
p(a < x < b) = p(a \leq x \leq b) = p(a \leq x < b) = p(a < x \leq b)
>$$

Tiếp theo, mật độ xác suất $p(x)$ phải thoả mãn một vài điều kiện:
- Xác suất là không âm:
$$
p(x) \geq 0
$$
- Ta đã biết, $p(x \in (a, b))$ là xác suất $x$ nằm trên khoảng $a, b$. Biến ngẫu nhiên $x$ mà ta đang xét là một số thực, do đó $x$ luôn nằm trong $\mathbb{R}$, tức là nằm trong đoạn $(-\infty, \infty)$. Vậy:
$$
p(x \in \mathbb{R}) = \int_{-\infty}^{\infty} p(x)dx = 1
$$
Ta có xác suất để $x$ nằm trong đoạn từ $(-\infty, z)$ là:
$$
P(z) = \int_{-\infty}^z p(x)dx
$$
ta gọi $P(z)$ là **phân phối xác suất tích luỹ** (cumulative distribution function) của $x$ (viết tắt là **cdf**). Trong đó $P'(x) = p(x)$.

>[!note]+ Xác minh lại
>Việc $P'(x) = p(x)$ được suy ra dựa vào **Fundamental Theorem Of Calculus** ([Fundamental theorem of calculus - Wikipedia](https://en.wikipedia.org/wiki/Fundamental_theorem_of_calculus#:~:text=The%20fundamental%20theorem%20of%20calculus,cumulative%20effect%20of%20small%20contributions)), trong đó nói rằng, nếu $f(x)$ là một hàm số liên tục trên đoạn $[a, b]$. Ta định nghĩa hàm $F(x)$ như sau:
>$$
>F(x) = \int_{a}^x f(t)dt
>$$
>Thì $F'(x) = f(x)$ trên đoạn $[a,b]$. Nếu ta thay $[a, b]$ thành $(-\infty, \infty)$ thì ta vẫn có được $P'(x) = p(x)$ trên $\mathbb{R}$. Thông thường, ta sẽ cố gắng định nghĩa $p(x)$ (mật độ xác suất) sao cho $p(x)$ liên tục trên $\mathbb{R}$. Một ví dụ điển hình là 

>[!danger]+ Lưu ý nhỏ
>Mật độ xác suất khác với xác suất, mật độ xác suất đại diện cho xác suất trên một đơn vị chiều dài của biến ngẫu nhiên $x$, giống như khối lượng riêng của một vật (tiếng anh khối lượng riêng là *density*) đại diện cho khối lượng trên một đơn vị thể tích. Do đó mật độ xác suất có thể lớn hơn $1$, nhưng điều quan trọng đó là diện tích nằm dưới đồ thị của mật độ xác suất $p(x)$ luôn là $1$ ([Can a probability distribution value exceeding 1 be OK? - Cross Validated (stackexchange.com)](https://stats.stackexchange.com/questions/4220/can-a-probability-distribution-value-exceeding-1-be-ok/4223#4223)) 

>[!info]+ Một chút giải thích của mình
>Đây hoàn toàn là giải thích của mình nên có thể có sai sót trong đây.
>
>Các bạn có thể thấy, xác suất để $x$ nằm trong khoảng $(x, x + \delta x)$ được xấp xỉ bởi giá trị $p(x)\delta x$, bởi vì xác suất để $x$ nằm trong khoảng là phần diện tích dưới đồ thị $p(x)$ từ $x \to x + \delta x$, dựa theo tích phân Riemann, ta có thể xấp xỉ:
>$$
p(x \in (x , x+ \delta x)) = \int_{x}^{x + \delta x}p(x) dx \approx p(x)\delta x
>$$
>Tiếp tục dựa theo tích phân riemann, nếu chia đoạn $[a, b]$ thành $n$ điểm, ta có:
> $$
p(x \in (a, b)) = \int_{a}^b p(x)dx = \lim_{ \delta x \to 0 } \sum_{k=0}^{n-1} p(a + k \delta x) \delta x
> $$
>
>![Pasted image 20240419135539.png](/img/user/Attachment/Pasted%20image%2020240419135539.png)

Đặt $x = g(y)$. Đặt $P_x$ là cdf của $x$ và $P_y$ là cdf của $y$. Tương tự, đặt $p_x$ là mật độ xác suất của $x$ và $p_y$ là mật độ xác suất của $y$. 

>[!danger]+ Lưu ý
>$g$ phải là một hàm đơn điệu (ngặt) để có thể tồn tại một hàm ngược $g^{-1}$.  Khi đó mọi công thức phía dưới mới đúng.

Ta xét 2 trường hợp:
- Nếu $g$ là hàm đồng biến:
$$
\begin{aligned}
P_{x}(z) = p(x \in (-\infty, z)) &= p(x < z) \\
&= p(g(y) < z) \\ 
&= p(y < g^{-1}(z)) \\
&= P_{y}(g^{-1}(z))
\end{aligned}
$$
- Nếu $g$ là hàm nghịch biến:
$$
\begin{aligned}
P_{x}(z) &= p(x < z) \\
&= p(g(y) < z) \\ 
&= p(y > g^{-1}(z)) \\
&= 1 - p(y < g^{-1}(z)) \\
&= 1 - P_{y}(g^{-1}(z))
\end{aligned}
$$
Lấy đạo hàm $P_x(z)$ ta được:
- Nếu $g$ là hàm đồng biến:
$$
P'_{x}(z) = P'_{y}(g^{-1}(z)) \frac{d}{dz}g^{-1}(z)
$$
- Nếu $g$ là hàm nghịch biến:
$$
P'_{x}(z) = -P'_{y}(g^{-1}(z)) \frac{d}{dz}g^{-1}(z)
$$
- Kết hợp cả 2, ta được trường hợp tổng quát nếu $g$ là hàm đơn điệu (ngặt):
$$
P'_{x}(z) = P'_{y}(g^{-1}(z)) \left| \frac{d}{dz}g^{-1}(z) \right|
$$
Thay biến $z$ thành $x$, ta được:
$$
\begin{aligned}
P'_{x}(x) &= P'_{y}(g^{-1}(x)) \left| \frac{d}{dx}g^{-1}(x) \right| \\
&= P'_{y}(y) \left| \frac{dy}{dx} \right| \\
\Leftrightarrow P'_{y}(y) &= P'_{x}(x) \left| \frac{dx}{dy} \right| \\
&= P'_{x}(g(y)) \left| \frac{dg(y)}{dy} \right| \\
\implies p_{y}(y) &= p_{x}(g(y)) | g'(y) |
\end{aligned}
$$
Ta gọi $|g'(y)|$ là **jacobian factor**. Hàm mật độ xác suất $p_x(x)$ sau khi chuyển từ biến $x$ sang biến $y$ bằng hàm không tuyến tính $g$ với $x = g(y)$ biến đổi khác đi, từ một hàm đơn giản khác sang một hàm mới (có thể phức tạp hơn), điều này là do jacobian factor.

Nếu ta có nhiều biến ngẫu nhiên $x_1, \dots, x_D$, được định nghĩa chung bằng vector $\mathbf{x} = (x_1, \dots, x_D)$, khi đó ta định nghĩa hàm **mật độ xác suất đồng thời** $p(\mathbf{x}) = p(x_1, \dots, x_D)$ sao cho xác suất $\mathbf{x}$ thuộc một phần thể tích vô cùng nhỏ (infinitesimal volume) $\delta \mathbf{x}$ (có chứa $\mathbf{x}$) được xác định bởi $p(\mathbf{x})\delta \mathbf{x}$.

>[!note]+
>Khi ở nhiều chiều hơn, một "khoảng" của ta sẽ trở nên khác. Ví dụ ở 1 chiều $\mathbf{x} = (x)$ thì khoảng ở đây sẽ là một khoảng trên đường thẳng từ $(a, b)$ nào đó, nếu ở 2 chiều $\mathbf{x} = (x_1, x_2)$ thì "khoảng" ở đây là một hình chữ nhật, ở 3 chiều là một hình hộp chữ nhật, ở 4 chiều thì chịu 🥲, đùa đấy, ở chiều cao hơn thì sẽ được gọi là **hyper-rectangle**. Ngoài ra chữ *infinitesimal* (vô cùng nhỏ) có nghĩa là một số $x$ nào đó rất gần $0$ và không có số nào gần hơn nó.

Tương tự như mật độ xác suất 1 biến, ta cũng có:
- Xác suất không âm:
$$
p(\mathbf{x}) \geq 0
$$
- Phần tổng diện tích luôn là $1$:
$$
\int p(\mathbf{x}) d\mathbf{x} = 1
$$
>[!note]+
>Kí hiệu $\int$ có nghĩa là tích phân toàn bộ không gian của $\mathbf{x}$, giả sử trong không gian 2 chiều, ta có:
>$$
\int p(\mathbf{x}) d\mathbf{x} = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} p(x_{1}, x_{2}) dx_{1} dx_{2} = 1
>$$
>Tương tự lên $3$ chiều hay $n$ chiều. Nếu xét trong 2 chiều, ta có xác suất để $\mathbf{x}$ nằm trong hình chữ nhật được tạo bởi 4 đường thẳng $x = a, x = b, y = c, y = d$ là:
>$$
p(a < x < b, c < y < d) = \int_{c}^{d} \int_{a}^{b} p(x, y) dx dy
>$$
>Nếu ta viết (chỉ xét trong không gian 2 chiều):
>$$
\begin{aligned}
p(a < x < b) = p(a < x < b, y) &= \int_{-\infty}^{\infty} \int_{a}^{b} p(x, y) dx dy \\
&= \int_{a}^{b} \left[ \int_{-\infty}^{\infty} p(x, y)dy \right] dx
\end{aligned}
>$$
>thì đây chính là xác suất biên (tổng cũng tương tự tích phân, ta lấy tổng các biến ngẫu nhiên còn lại như đã định nghĩa ở phần trước). Ta có thể thấy $\int_{-\infty}^{\infty} p(x, y)dy$ đóng vai trò như $p_x(x)$.

Nếu $x$ là biến ngẫu nhiên rời rạc, ta gọi $p(x)$ là **hàm khối xác suất** (probability mass function). Phân biệt một tí với hàm mật độ xác suất, hàm khối xác suất cũng thể được xem là xác suất của biến ngẫu nhiên rời rạc.

Tương tự như biến ngẫu nhiên rời rạc, sum rule, product rule và định lý Bayes vẫn có thể áp dụng với biến ngẫu nhiên liên tục. Đặt $x$ và $y$ là hai biến ngẫu nhiên liên tục, ta có:
$$
\begin{aligned}
p(x) &= \int p(x, y) dy \\
p(x, y) &= p(y \mid x) p(x)
\end{aligned}
$$
>[!bug]+
>Việc chứng minh hai công thức này thì mình chịu, vượt quá sức của mình rồi 🥲

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
- [calculus - How is the derivative of the CDF of a random variable $X$ its PDF? - Mathematics Stack Exchange](https://math.stackexchange.com/questions/248269/how-is-the-derivative-of-the-cdf-of-a-random-variable-x-its-pdf)
- [distributions - Derivation of change of variables of a probability density function? - Cross Validated (stackexchange.com)](https://stats.stackexchange.com/questions/239588/derivation-of-change-of-variables-of-a-probability-density-function)
- [ch3withfigs.pdf (uchicago.edu)](https://www.stat.uchicago.edu/~stigler/Stat244/ch3withfigs.pdf)