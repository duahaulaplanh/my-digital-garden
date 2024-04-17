---
{"dg-publish":true,"permalink":"/zettel/about-chapter-1/","created":"2024-04-15T16:40:01.637+07:00","updated":"2024-04-17T14:36:30.038+07:00"}
---

## Phân phối nhị thức (binomial distribution)

Một đồng xu không đồng chất (tức là xác suất ra mặt ngửa và mặt xấp không đều nhau) có xác suất ra mặt ngửa là $f$. Đặt biến ngẫu nhiên $X$ là số mặt ngửa khi tung đồng xu $N$ lần, khi đó, phân phối xác suất của $X$ sẽ là:
$$
P(X = r \mid f, N) = P(r \mid f, N) = {N \choose r} f^r (1-f)^{N- r} 
$$
>[!note]+ Giải thích
>Giả sử rằng mỗi lần tung đồng xu là độc lập với nhau, đặt biến cố lần tung đầu tiên là $A_1$, tương tự, tung lần thứ $i$ là $A_i$ và tung sau $N$ là $A$ vậy:
>$$
>P(A) = P(A_{1} \cap \dots \cap A_{n}) = P(A_{1})\dots P(A_{n})
>$$
>Vậy nếu tung $N$ lần, trong đó $r$ lần là mặt ngửa, tức là tại lần $i$ nào đó, ta tung được mặt ngửa, tức là $P(A_i) = f$, có $r$ lần như vậy. Ngoài ra khi tung $N$ lần mà $r$ lần mặt ngửa nên $N-r$ lần còn lại là mặt xấp với xác suất $1-f$. 
>$$
>(A) = f^r (1-f)^{N-r}
>$$
>Nếu ta xem mỗi lần tung thứ $i$ là một "ô" thứ $i$ trong $N$ ô, thì số cách mà tung $N$ lần có $r$ mặt ngửa ta xem như số cách để chọn $r$ ô trong $N$ ô, vậy số cách sẽ là:
>$$
>N \choose r
>$$
>Do $P(A)$ chỉ là xác suất của 1 cách trong $N \choose r$ cách, vì vậy, xác suất để mặt ngửa xuất hiện $r$ lần trong $N$ lần tung là:
>$$
>{N \choose r} f^r (1-f)^{N-r}
>$$

Trung bình của phân phối trên (được gọi là **phân phối nhị thức**), kí hiệu là $\mathcal{E}[X]$, được định nghĩa như sau:
$$
\mathcal{E}[X] \equiv \sum_{r=0}^N P(X = r \mid f, N) r
$$
>[!note]+
>Với $n$ biến ngẫu nhiên $X_1, X_2, ..., X_n$, trung bình có tính chất sau:
>$$
>\mathcal{E}\left[ \sum_{i=1}^n X_i \right] = \sum_{i=1}^n \mathcal{E}[X_{i}]
>$$
>Ngoài ra, với $\alpha \in \mathbb{R}$, ta có:
>$$
\mathcal{E}[\alpha X_i] = \alpha \mathcal{E}[X_i]
>$$
>Tính chất cuối cùng của trung bình (được gọi là [LOTUS](https://en.wikipedia.org/wiki/Law_of_the_unconscious_statistician)):
>$$
\mathcal{E}[g(X)] = \sum_{x} P(X = x)g(X)
>$$
>trong đó $P(x)$ là phân phối xác suất của $X$ và $\sum_{x}$ nghĩa là tổng trên toàn bộ giá trị mà $X$ có.

Nếu ta xem $X_i$ là số mặt ngửa ở lần tung thứ $i$ (tức là tại lần tung thứ $i$, ta được mặt ngửa hay mặt sấp, chỉ tung 1 lần). Vậy:
$$
X = X_1 + X_2 + \dots + X_N
$$
Ta biết rằng, với mỗi lần tung thứ $i$ thì trung bình của lần tung đó là $\mathcal{E}[X_i]=\sum_{r=0}^1 P(X=r \mid f, 1)r = f\cdot 1 + (1-f) \cdot 0 = f$ . Khi đó, trung bình của phân phối nhị thức sẽ là:
$$
\mathcal{E}[X] = \mathcal{E}[X_1 + X_2 + \dots + X_N] = \sum_{i=1}^N \mathcal{E}[X_i] = Nf
$$
Ta định nghĩa **phương sai** của phân phối nhị thức, kí hiệu $\text{var}[X]$ là:
$$
\text{var}[X] \equiv \mathcal{E}[(X - \mathcal{E}[X])^2] = \mathcal{E}[X^2] - (\mathcal{E}[X])^2
$$
>[!note]+
>Tương tự với trung bình, phương sai cũng có tính chất:
>$$
>\text{var}\left[ \sum_{i=1}^n X_n \right] = \sum_{i=1}^n \text{var}[X_i]
>$$

Nếu đặt $X_i$ tương tự như trung bình, ta có phương sai của $X_i$ là 
$$
\begin{aligned}
\text{var}[X_i] &= \mathcal{E}[X_i^2] + (\mathcal{E}[X_i])^2 \\ 
&= \sum_{r=0}^1 P(X = r \mid f, 1)r^2 + (\mathcal{E}[X_i])^2 \\ 
&= f - f^2 = f(1-f)
\end{aligned}
$$
Vậy, phương sai của phân phối nhị thức sẽ là:
$$
\text{var}[X] = \text{var}[X_1 + \dots + X_N] = Nf(1-f)
$$
## Xấp xỉ $x!$ và $N \choose r$

Xét phân phối $X$ như dưới đây:
$$
P(X = r \mid \lambda) = e^{-\lambda} \dfrac{\lambda^r}{r!} \hspace{5pt} \text{với $r \in \{0, 1, 2, \dots\}$}.
$$
ta gọi phân phối trên là **phân phối Poisson**.

>[!note]+
>Phân phối chuẩn hay còn gọi là phân phối gaussian có công thức như sau:
>$$
>P(X = x \mid \mu, \sigma) = \dfrac{1}{\sigma\sqrt{2 \pi}} e^{\dfrac{-(x - \mu)^2}{2\sigma^2}}.
>$$
>trong đó $\mu$ là trung bình của $X$, $\sigma^2$ là phương sai của $X$ và $\sigma$ là độ lệch chuẩn của $X$.

Khi $\lambda$ đủ lớn (thông thường là $\lambda > 1000$), ta có thể xấp xỉ phân phối Poisson với phân phối chuẩn có $\mu = \lambda$ và $\sigma^2 = \lambda \implies \sigma = \sqrt{\lambda}$ (tìm hiểu thêm ở [đây](https://stats.stackexchange.com/questions/83283/normal-approximation-to-the-poisson-distribution?rq=1)), vậy:
$$
e^{-\lambda} \dfrac{\lambda^r}{r!} \simeq\dfrac{1}{\sqrt{2\pi \lambda}} e^{\dfrac{-(r - \lambda)^2}{2\lambda}}.
$$
Xét phương trình xấp xỉ phía trên, nếu thay $r = \lambda$, ta được:
$$
\begin{aligned}
e^{-\lambda} \dfrac{\lambda^\lambda}{\lambda!} &\simeq \dfrac{1}{\sqrt{2\pi \lambda}} e^{\dfrac{-(\lambda - \lambda)^2}{2\lambda}} \\
\Leftrightarrow e^{-\lambda} \dfrac{\lambda^\lambda}{\lambda!} &\simeq \dfrac{1}{\sqrt{2\pi \lambda}} \\
\Leftrightarrow \lambda! &\simeq \lambda^{\lambda} e^{-\lambda} \sqrt{2\pi\lambda}.
\end{aligned}
$$
Ở phương trình xấp xỉ trên, ta có thể thấy giai thừa của một số được xấp xỉ bằng một công thức khác, ta gọi công thức đó là **xấp xỉ Stirling** ([Stirling's approximation](https://en.wikipedia.org/wiki/Stirling%27s_approximation)). Nếu ta lấy $\ln$ của xấp xỉ stirling, ta được:
$$
\begin{aligned}
\ln x! &\simeq \ln x^xe^{-x}\sqrt{2\pi x} \\
&\simeq \ln x^x  + \ln e^{-x} + \ln \sqrt{ 2\pi x } \\
&\simeq x\ln x - x + \frac{1}{2}\ln 2 \pi x.
\end{aligned}
$$
>[!note]+
>Ngoài cách viết như trên, người ta cũng thường viết như sau:
>$$
>x\ln x - x + O(\ln x).
>$$

Giá trị nằm phía cuối $\frac{1}{2} \ln 2\pi x$ được gọi là *next-order correction term* (mình cũng không rõ đoạn này), ta hoàn toàn có thể bỏ nó và sử dụng:
$$
x! \simeq x\ln x - x.
$$
Ta biết rằng:
$$
{N \choose r} = \frac{N!}{(N - r)! r!}.
$$
Do đó, ta hoàn toàn có thể xấp xỉ $N \choose r$ bằng cách dùng xấp xỉ Stirling:
$$
\begin{aligned}
\ln \frac{N!}{(N - r)! r!} &= \ln N! - \ln (N-r)! - \ln r \\
&\simeq N\ln N - N - (N-r)\ln(N-r) + (N-r) - r\ln r + r \\
&= N\ln N - (N-r)\ln(N-r) - r\ln r \\
&= (N-r)\ln N - (N-r)\ln(N-r) + r\ln N - r\ln r\\
&= (N-r)\ln \frac{N}{N-r} + r\ln \frac{N}{r}.
\end{aligned}
$$
Ta biết rằng:
$$
\log_{2}x = \frac{\log_{e}x}{\log_{e}2} = \frac{\ln x}{\ln 2}.
$$
tức là giữa $\ln x$ và $\log_{2} x$ (nếu chỉ viết $\log$ thì ta hiểu đây là $\log_{2}$) chỉ khác nhau một hằng số, do đó việc xấp xỉ $\ln x!$ có thể thay thế thành $\log x!$ mà không cần thay đổi công thức, chỉ thêm hằng số vào, do đó có thể bỏ luôn hằng số đó trong khi xấp xỉ.
$$
\log{N\choose r} \simeq (N-r)\log \frac{N}{N-r} + r\log \frac{N}{r}.
$$
Định nghĩa hàm $H_2(x)$ như sau:
$$
H_{2}(x) \equiv x\log \frac{1}{x} + (1-x) \log \frac{1}{(1-x)}.
$$ta gọi $H_2(x)$ là **hàm entropy nhị phân** (binary entropy function).

Dựa vào hàm $H_2(x)$, ta có thể xấp xỉ $\log{N \choose r}$ thành:
$$
\log{N \choose r} \simeq N H_{2}(r / N).
$$
hay
$$
{N \choose r} = 2^{NH_{2}(r / N)}.
$$

>[!danger]+ Tại sao mình lại học Information Theory
>He

---

Phần sau: [[Zettel/Introduction to Information Theory\|Introduction to Information Theory]]

---
# References

- [Deriving the Binomial PMF (dcgerard.github.io)](https://dcgerard.github.io/stat234/14_binomial_distribution.pdf)
- [MacKay] Information Theory, Inference and Learning Algorithms - MacKay (chapter 1)