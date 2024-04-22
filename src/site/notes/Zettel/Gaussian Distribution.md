---
{"dg-publish":true,"permalink":"/zettel/gaussian-distribution/","noteIcon":"📝","created":"2024-04-22T12:17:03.261+07:00","updated":"2024-04-22T15:26:57.850+07:00"}
---

**Phân phối chuẩn** (Gaussian Distribution hoặc Normal Distribution), kí hiệu là $\mathcal{N}(x \mid \mu, \sigma^2)$, sẽ được định nghĩa như sau:
$$
\mathcal{N}(x \mid \mu, \sigma^2) = \frac{1}{(2\pi \sigma^2)^{1/2}} \exp \left\{ - \frac{1}{2\sigma^2} (x - \mu)^2 \right\}
$$
Với $x$ là số thực và $\mathcal{N}(x \mid \mu, \sigma^2)$ có nghĩa là phân phối gồm 2 tham số là $\mu$ và $\sigma^2$, trong đó $\mu$ là **trung bình** (mean) của phân phối, $\sigma^2$ là **phương sai** (variance) của phân phối.

Ngoài ra, nếu lấy căn của phương sai, ta được $\sigma$ và ta gọi giá trị đó là **độ lệch chuẩn** (standard derivation) của phân phối. Còn nếu lấy nghịch đảo của phương sai và đặt giá trị đó là $\beta$, tức là $\beta = 1/(\sigma^2)$, ta gọi $\beta$ là **độ chính xác** (precision) của phối.

>[!note]+
>Khi ta nói một biến ngẫu nhiên liên tục $X$ nào đó có phân phối $f$ với các tham số $\theta_{i}$, ta kí hiệu $X \sim f(\theta_{1}, \theta_{2}, \dots)$. Ví dụ, $X$ có phân phối chuẩn với trung bình là $\mu$ và phương sai là $\sigma^2$ thì ta viết $X \sim \mathcal{N}(\mu, \sigma^2)$. Ngoài ra khi viết $X$ có phân phối, ta ngầm hiểu phân phối đó là mật độ xác suất (pdf) của $X$.

>[!danger]+  Mình làm màu là chủ yếu
>Để chứng minh phân phối chuẩn $\mathcal{N}(x \mid \mu, \sigma^2)$ là một hàm mật độ xác suất thì ta cần chứng minh hai tính chất:
>$$
\begin{aligned}
\mathcal{N}(x \mid \mu, \sigma^2) &\geq 0 \\
\int_{-\infty}^{\infty} \mathcal{N}(x \mid \mu, \sigma^2) dx &= 1
\end{aligned}
>$$
>Tính chất đầu tiên thì ta dễ thấy rồi, để chứng minh được tính chất thứ 2, ta phải tìm hiểu thêm một dạng nữa của phân phối chuẩn, được gọi là **phân phối chuẩn tắc** (standard normal distribution), kí hiệu $\varphi(z)$. Phân phối chuẩn tắc được định nghĩa như sau:
>$$
\varphi(z) = \frac{1}{(2\pi)^{1/2}} \exp \left\{ -\frac{1}{2}z^2 \right\}
>$$
>Ngoài ra, phân phối chuẩn tắc có trung bình là $0$ và phương sai là $1$. Nếu đặt $z = (x - \mu) / sigma$ thì ta có thể đưa phân phối chuẩn tắc về phân phối chuẩn như sau:
>$$
\mathcal{N}(x \mid \mu, \sigma^2) = \frac{1}{\sigma} \varphi\left( \frac{x-\mu}{\sigma} \right)
>$$
>Giờ xét tích phân của phân phối chuẩn, ta có:
>$$
\begin{aligned}
&\int_{-\infty}^{\infty} \frac{1}{(2\pi \sigma^2)^{1/2}} \exp \left\{ - \frac{1}{2\sigma^2} (x - \mu)^2 \right\} dx \\
= \frac{1}{(2\pi \sigma^2)^{1/2}} &\int_{-\infty}^{\infty} \exp \left\{ - \frac{1}{2\sigma^2} (x - \mu)^2 \right\} dx \\
\end{aligned}
>$$
>Đặt $z = (x - \mu) / \sigma$ (mục đích đưa tích phân trên về tích phân của phân phối chuẩn tắc), ta có $x = z \sigma + \mu \implies dx = \sigma dz$. Đổi biến tích phân trên từ $x$ sang $z$ ta được:
>$$
\begin{aligned}
&\frac{1}{(2\pi \sigma^2)^{1/2}} \int_{-\infty}^{\infty} \exp \left\{ - \frac{1}{2} z^2 \right\} \sigma dz \\
= &\frac{1}{(2\pi)^{1/2}} \int_{-\infty}^{\infty} \exp \left\{ - \frac{1}{2} z^2 \right\} dz \\
\end{aligned}
>$$
>Lưu ý, tích phân sau:
>$$
\int_{-\infty}^{\infty} \exp\{-y^2\}dy = \sqrt{ \pi }
>$$
>còn được gọi là **tích phân Gauss** ([Gaussian integral - Wikipedia](https://en.wikipedia.org/wiki/Gaussian_integral)) mình sẽ không chứng minh mà dùng luôn (chứng minh không nổi 🥲). Nếu tiếp tục đặt $y^2 = z^2 / 2 \implies \sqrt{ 2 } y = z$ thì ta có $\sqrt{ 2 }dy = dz$, ta được:
>$$
\begin{aligned}
&\frac{1}{(2\pi)^{1/2}} \int_{-\infty}^{\infty} \exp \left\{ - y^2 \right\} \sqrt{ 2 } dy \\
&= \frac{1}{(2\pi)^{1/2}} \sqrt{ 2 } \sqrt{ \pi } \\
&= 1
\end{aligned}
>$$

Ta có kì vọng của một biến ngẫu nhiên $X \sim \mathcal{N}(\mu, \sigma^2)$ là:
$$
\mathbb{E}[X] = \int_{-\infty}^{\infty} \mathcal{N}(x \mid \mu, \sigma^2)x dx = \mu
$$
Vậy kì vọng của $X$ chính là giá trị trung bình của phân phối. Ngoài ra, ta có:
$$
\mathbb{E}[X^2] = \int_{-\infty}^{\infty} \mathcal{N}(x \mid \mu, \sigma^2)x^2 dx = \mu^2 + \sigma^2
$$
ta gọi giá trị $\mathbb{E}[X^2]$ là **moment bậc 2** (second order moment) của $X$. Tương tự moment bậc $k$ của $X$ sẽ là $\mathbb{E}[X^k]$. Từ hai phương trình trên, ta có phương sai của $X$ là:
$$
\text{var}[X] = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = \sigma^2
$$
Giá trị lớn nhất của một phân phối còn được gọi là **mode** và phân phối chuẩn có $mode = \mu$, tức là:
$$
\max \mathcal{N}(x \mid \mu, \sigma^2) = \mu
$$
>[!note]+
>Do tác giả đưa chứng minh này vào phần bài tập nên mình cũng sẽ cố gắng chứng minh trong phần bài tập luôn. Phần bài tập nằm ở [[Exercises Part I\|Exercises Part I]].

Xét một vector $D$ chiều gồm các số thực $\mathbf{x} =(x_{1}, \dots, x_{D})^T$. Ta định nghĩa phân phối chuẩn trên vector $\mathbf{x}$ là:
$$
\mathcal{N}(\mathbf{x} \mid \pmb{\mu}, \pmb{\Sigma}) = \frac{1}{(2\pi)^{D/2}} \frac{1}{|\pmb{\Sigma}|^{1/2}} \exp \left\{ -\frac{1}{2} (\mathbf{x} - \pmb{\mu})^T \pmb{\Sigma}^{-1} (\mathbf{x} - \pmb{\mu}) \right\}
$$
trong đó $\pmb{\mu}$ là vector trung bình của phân phối có $D$ chiều, $\pmb{\Sigma}$ là ma trận hiệp phương sai có kích thước $D \times D$ và $|\pmb{\Sigma}|$ là định thức của ma trận hiệp phương sai $\pmb{\Sigma}$. Một tên gọi khác cho phân phối chuẩn nhiều chiều là **multivariate normal (hoặc gaussian) distribution**.

---

Phần trước: [[Zettel/Bayesian Probabilities\|Bayesian Probabilities]]
Phần sau: [[Curve Fitting Revisited\|Curve Fitting Revisited]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.2)
- [Proof: Integral of PDF of Normal Distribution is Equal to 1 (in English) (youtube.com)](https://www.youtube.com/watch?v=8Ey7v8IoZjA)