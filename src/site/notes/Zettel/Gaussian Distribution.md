---
{"dg-publish":true,"permalink":"/zettel/gaussian-distribution/","noteIcon":"📝","created":"2024-04-22T12:17:03.261+07:00","updated":"2024-04-23T07:59:24.106+07:00"}
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
>Do tác giả đưa chứng minh này vào phần bài tập nên mình cũng sẽ cố gắng chứng minh trong phần bài tập luôn. Phần bài tập nằm ở [[Zettel/Exercises Part I\|Exercises Part I]].

Xét một vector $D$ chiều gồm các số thực $\mathbf{x} =(x_{1}, \dots, x_{D})^T$. Ta định nghĩa phân phối chuẩn trên vector $\mathbf{x}$ là:
$$
\mathcal{N}(\mathbf{x} \mid \pmb{\mu}, \pmb{\Sigma}) = \frac{1}{(2\pi)^{D/2}} \frac{1}{|\pmb{\Sigma}|^{1/2}} \exp \left\{ -\frac{1}{2} (\mathbf{x} - \pmb{\mu})^T \pmb{\Sigma}^{-1} (\mathbf{x} - \pmb{\mu}) \right\}
$$
trong đó $\pmb{\mu}$ là vector trung bình của phân phối có $D$ chiều, $\pmb{\Sigma}$ là ma trận hiệp phương sai có kích thước $D \times D$ và $|\pmb{\Sigma}|$ là định thức của ma trận hiệp phương sai $\pmb{\Sigma}$. Một tên gọi khác cho phân phối chuẩn nhiều chiều là **multivariate normal (hoặc gaussian) distribution**.

>[!danger]+
>Mình không thể gõ được chữ $x$ như trong sách 😭. Nên mình dùng kí hiệu là $\mathcal{D}$ vậy.

Giả sử ta có một tập dữ liệu $\mathcal{D} = (y_1, \dots, y_N)^T$. Tập dữ liệu bao gồm $N$ quan sát, mỗi quan sát (observation) là một đại lượng vô hướng (scalar) $y_{i}$.

>[!note]+
>Ta gọi một giá trị $x$ là scalar nếu nó không phải là vector (ez huh). Đúng hơn, scalar (hay đại lượng vô hướng) để chỉ phần tử của một trường (field) ([Scalar (mathematics) - Wikipedia](https://en.wikipedia.org/wiki/Scalar_(mathematics))). Tập số thực ($\mathbb{R}$) là một trường, do đó ta có thể nói các số thực $x \in \mathbb{R}$ là một đại lượng vô hướng. Ngoài ra, tập số phức $\mathbb{C}$ cũng là một trường nên $x$ cũng có thể là số phức nếu ta chỉ nói $x$ là đại lượng vô hướng mà không nói gì thêm.

Giả sử các quan sát trong tập dữ liệu $\mathcal{D}$ của ta được lấy ra một cách độc lập (drawn independently) từ một phân phối chuẩn có trung bình là $\mu$ và phương sai là $\sigma^2$ (đây là hai đại lượng mà ta chưa biết và mục đích của chúng ta là tìm ra được hai tham số này từ tập dữ liệu mà ta có), nghĩa là $y_i = \mathcal{N}(x_i \mid \mu, \sigma^2)$.

>[!note]+
>Ở câu "lấy ra một cách độc lập", ta có thể hiểu như sau:
>- "Lấy ra" (drawn): tức là các giá trị này được chọn một cách ngẫu nhiên trên phân phối.
>- "Độc lập" (independently): khi ta lấy một giá trị mới, các giá trị trước đó (kể cả sau đó) không làm ảnh hưởng đến quyết định ta lấy giá trị mới nào.

Các điểm dữ liệu mà:
- Được lấy ra từ cùng một phân phối (identically distributed).
- Độc lập với nhau (independent).
thì được nói là **độc lập và có phân phối đồng nhất** (independent and identically distributed) và thuòng viết tắt là i.i.d.

>[!note]+
>Xét tập dữ liệu $\mathcal{D}$, nếu ta viết $\mathcal{D} \overset{i.i.d}{\sim} \mathcal{N}(\mu, \sigma^2)$ tức là tập dữ liệu $\mathcal{D}$ là độc lập và có phân phối đồng nhất, ngoài ra $\mathcal{D}$ được lấy ra từ phân phối chuẩn.

Xét hàm likelihood $\mathcal{L}(\mu, \sigma^2 \mid \mathcal{D})$, bởi vì $\mathcal{D}$ là i.i.d nên ta có:
$$
\mathcal{L}(\mu, \sigma^2 \mid \mathcal{D}) = p(\mathcal{D} \mid \mu, \sigma^2) = p(y_{1}, \dots, y_{N} \mid \mu, \sigma^2) = \prod_{n=1}^N p(y_{n} \mid \mu, \sigma^2)
$$
>[!note]+
>Như ta đã nói ở phần trước ([[Zettel/Introduction (Prob)\|Introduction (Prob)]]), khi $X$ và $Y$ độc lập với nhau thì:
>$$
p(X, Y) = p(X)p(Y)
>$$

Ta có một tập dữ liệu $\mathcal{D}$, ta đã giả sử các điểm dữ liệu được lấy ra từ một phân phối chuẩn $\mathcal{N}(\mu, \sigma^2)$ với $\mu$ và $\sigma^2$ chưa biết. Nếu dự đoán được $\mu$ và $\sigma^2$, gọi giá trị đự doán là $\hat{\mu}$ và $\hat{\sigma}^2$, thì ta đã tìm được cách để dự đoán $\hat{y}$ từ một mẫu $x$ nào đó, bằng $\hat{y} = \mathcal{N}(x \mid \hat{\mu}, \hat{\sigma}^2)$.

Một trong những cách thường dùng để tìm các tham số cho phân phối bằng cách sử dụng tập dữ liệu quan sát được là tìm các tham số mà **làm cực đại** hàm likelihood (hay còn gọi là **maximum likelihood**). Hay nói cách khác:
$$
\hat{\mu}, \hat{\sigma}^2 = \text{arg}\max_{\mu, \sigma^2} \mathcal{L}(\mu, \sigma^2 \mid \mathcal{D})
$$
>[!note]+
>Kí hiệu $\displaystyle \text{arg}\max_{x} f(x)$ có nghĩa là giá trị $x$ sao cho $f(x)$ là lớn nhất (cực đại).

Đễ dễ dàng hơn, thay vì tìm các tham số làm cực đại hàm likelihood, ta tìm các tham số làm cực đại hàm log (log ở đây sẽ được hiểu là $\ln$) của hàm likelihood, nghĩa là:
$$
\hat{\mu}, \hat{\sigma}^2 = \text{arg}\max_{\mu, \sigma} \ln \mathcal{L}(\mu, \sigma^2 \mid \mathcal{D})
$$
Sử dụng cách thức cực đại hàm log likehood, ta có thể viết hàm likelihood lại như sau:
$$
\begin{aligned}
\ln \mathcal{L}(\mu, \sigma^2 \mid \mathcal{D}) &= \ln \prod_{n=1}^N p(y_{n} \mid \mu, \sigma^2) \\
&= \left[-\frac{1}{2\sigma^2} \sum_{n=1}^N (y_{n} - \mu)^2 \right] - \frac{N}{2} \ln 2\pi - \frac{N}{2}\ln \sigma^2
\end{aligned}
$$
>[!note]+
>Ta có:
>$$
\begin{aligned}
\ln \mathcal{L}(\mu, \sigma^2 \mid \mathcal{D}) &= \ln \prod_{i=1}^N p(y_{i} \mid \mu, \sigma^2) \\
&= \sum_{i=1}^N \ln p(y_{i} \mid \mu, \sigma^2) \\
&= \sum_{=1}^N \ln \frac{1}{(2\pi\sigma^2)^{1/2}} \exp \left\{ -\frac{1}{2\sigma^2} (y_{i} - \mu)^2 \right\} \\
&= \sum_{i=1}^N \ln (2\pi\sigma^2)^{-1/2} -\frac{1}{2\sigma^2} (y_{i} - \mu)^2 \\
&= \sum_{i=1}^N - \frac{1}{2}\ln 2\pi -\frac{1}{2}\ln \sigma^2 - \frac{1}{2\sigma^2} (y_{i} - \mu)^2 \\
&= \left[-\frac{1}{2\sigma^2} \sum_{i=1}^N (y_{i} - \mu)^2 \right] - \frac{N}{2} \ln 2\pi - \frac{N}{2}\ln \sigma^2
\end{aligned}
>$$

Cực đại hàm log likelihood phía trên bằng cách dùng $\mu$, ta có:
$$
\mu_{ML} = \frac{1}{N} \sum_{n=1}^N y_{n}
$$
trong đó $\mu_{ML}$ được gọi là **trung bình mẫu** (sample mean) tức là trung bình của các quan sát $\{y_n\}$ mà ta quan sát được. Còn nếu ta cực đại bằng cách dùng $\sigma^2$, ta có:
$$
\sigma^2_{ML} = \frac{1}{N} \sum_{n=1}^N (y_{n} - \mu_{ML})^2
$$
ta gọi $\sigma^2_{ML}$ là **phương sai mẫu** (sample variance), ngoài ra ta thấy $\sigma^2_{ML}$ cũng phụ thuộc vào $\mu_{ML}$. Về lý thuyết là ta cần tính cả hai cùng lúc (tìm bộ tham số làm cực đại, mà bộ tham số gồm $n$ biến thì tìm cùng lúc $n$ biến) thế nhưng trong trường hợp này, $\mu_{ML}$ không phụ thuộc vào $\sigma^2_{ML}$ do đó ta có thể tìm $\mu_{ML}$ trước sau đó tìm $\sigma^2_{ML}$.

>[!note]+
>Thông thường giá trị trung bình $\mu$ được gọi trung bình tổng thể (population mean) tương tự với $\sigma^2$ là phương sai tổng thể (variance mean), đây là giá trị mà ta không biết, thế nhưng bằng cách dùng một phần của tổng thể (gọi là mẫu), ta sẽ cố gắng ước lượng được giá trị $\mu$ với $\sigma^2$ tốt nhất. Như đã chứng minh phía trên, giá trị ước lượng tốt nhất chính là $\mu_{ML}$ (trung bình của mẫu) và $\sigma^2_{ML}$ (phương sai của mẫu).

>[!note]+
>Để tìm giá trị cực đại của một hàm, ta đạo hàm sau đó lấy bằng $0$. Ta biết rằng $\ln$ là một hàm đồng biến trên $\mathbb{R}$ do đó giá trị tại dạo hàm bằng $0$ cũng chính là cực đại. Ta sẽ viết gọn $\ln \mathcal{L}(\mu, \sigma^2 \mid \mathcal{D})$ thành $\mathcal{L}$.
>
>Xét cực đại bằng $\mu$, ta có:
>$$
\frac{\partial\mathcal{L}}{\partial\mu} = -\frac{1}{2\sigma^2} \sum_{n=1}^N -2y_{n} + 2\mu 
>$$
>Khi đó, giá trị cần tìm là:
>$$
\begin{aligned}
-\frac{1}{2\sigma^2} \sum_{n=1}^N -2y_{n} + 2\mu &= 0 \\
\implies \sum_{n=1}^N -2y_{n} + 2\mu &= 0 \\
\Leftrightarrow 2\sum_{n=1}^N -y_{n} + 2N\mu &= 0 \\
\Leftrightarrow \mu = \frac{1}{N} \sum_{n=1}^N y_{n}
\end{aligned}
>$$
>
>Xét cực đại bằng $\sigma^2$, ta có:
>$$
\frac{\partial \mathcal{L}}{\partial \sigma^2} = \frac{1}{2\sigma^4} \sum_{n=1}^N (y_{n} - \mu)^2 - \frac{N}{2} \frac{1}{\sigma^2}
>$$
>Khi đó, giá trị cần tìm là:
>$$
\begin{aligned}
\frac{1}{2\sigma^4} \sum_{n=1}^N (y_{n} - \mu)^2 - \frac{N}{2} \frac{1}{\sigma^2} = 0 \\
\implies \frac{1}{\sigma^2} \sum_{n=1}^N (y_{n} - \mu)^2 - N = 0 \\
\Leftrightarrow \sigma^2 = \frac{1}{N} \sum_{n=1}^N (y_{n} - \mu)^2
\end{aligned}
>$$

Xét giá trị kì vọng của trung bình mẫu $\mu_{ML}$, ta có:
$$
\begin{aligned}
\mathbb{E}[\mu_{ML}] &= \mathbb{E}\left[ \frac{1}{N} \sum_{n=1}^N y_{n} \right] \\
&= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[y_{n}] \\
&= \frac{1}{N} \sum_{n=1}^N \mu \\
&= \mu
\end{aligned}
$$
có thể thấy, kì vọng của trung bình mẫu $\mu_{ML}$ chính là trung bình của phân phối $\mu$, đúng như ta dự đoán, giá trị $\mu_{ML}$ có thể được dùng ước lượng rất tốt $\mu$. Thế nhưng, nếu xét giá trị kì vọng của phương sai mẫu $\sigma^2_{ML}$, ta có:
$$
\mathbb{E}[\sigma^2_{ML}] = \frac{(N-1)}{N} \sigma^2
$$
Mặc dù ước lượng tốt với $\mu_{ML}$ thế nhưng $\sigma^2_{ML}$ thì không. Dùng $\sigma^2_{ML}$ để ước lượng cho $\sigma^2$ thì cho ra giá trị thấp hơn, ta gọi cách ước lượng này là **đánh giá thấp** (underestimate) (hay còn gọi là bias). Để tránh việc bias như này, ta chỉ cần chia cho $N-1$ thay vì $N$ ở phương sai mẫu:
$$
\begin{aligned}
\sigma^2_{ML} &= \frac{1}{N-1} \sum_{n=1}^N (y_{n} - \mu_{ML})^2 \\
\implies \mathbb{E}[\sigma^2_{ML}] &= \sigma^2
\end{aligned}
$$
và đây là lý do mà người ta thường chia cho $N-1$ thay vì $N$ ở phương sai mẫu.

>[!danger]+ Phần chứng minh này hơi dài 🥲
>Ta có:
>$$
\begin{aligned}
\mathbb{E}[\sigma^2_{ML}] &= \mathbb{E}\left[ \frac{1}{N} \sum_{n=1}^N (y_{n} - \mu_{{ML}})^2 \right] \\
&= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[(y_{n} - \mu_{ML})^2] \\
&= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[y_{n}^2 -2y_{n}\mu_{ML} + \mu_{ML}^2] \\
&= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[y_{n}^2] -2\mathbb{E}[y_{n}\mu_{ML}] + \mathbb{E}[\mu_{ML}^2] \\
\end{aligned}
>$$
>Như ta đã biết ở phần trên, moment bậc 2 của $y_n$ hay $\mathbb{E}[y_n^2]$ sẽ là:
>$$
\mathbb{E}[y_{n}^2] = \sigma^2 + \mu^2
>$$
>Còn giá trị $\mathbb{E}[y_n\mu_{ML}]$ sẽ được tính như sau (nhớ là các quan sát độc lập với nhau, do đó với hai quan sát $y_i$ và $y_j$ bất kì, ta có $\mathbb{E}[y_iy_j] = \mathbb{E}[y_i]\mathbb{E}[y_j]$):
>$$
\begin{aligned}
\mathbb{E}[y_{n}\mu_{ML}] &= \mathbb{E}\left[ y_{n} \frac{1}{N} \sum_{i=1}^N y_{i} \right] \\
&= \frac{1}{N} \left[ \sum_{j \neq n} \mathbb{E}[y_{n}y_{j}] + \mathbb{E}[y_{n}^2] \right] \\
&= \frac{1}{N} \left[ (N-1)\mu^2 + \mu^2 + \sigma^2 \right] \\
&= \mu^2 + \frac{\sigma^2}{N}
\end{aligned}
>$$
>Ta chỉ cần tính giá trị còn lại là $\mathbb{E}[\mu_{ML}^2]$. Trước tiên ta cần biết công thức sau:
>$$
\left( \sum_{n=1}^N x_{n} \right)^2 = \sum_{n=1}^N a_{n}^2 + 2\sum_{j=1}^N\sum_{i=1}^j a_{i}a_{j}
>$$
>Chứng minh này công thức này mình thua (các bạn có thể xem thêm ở [algebra precalculus - What is the square of summation? - Mathematics Stack Exchange](https://math.stackexchange.com/questions/329344/what-is-the-square-of-summation)). Sau khi có công thức rồi thì tính thôi nào:
>$$
\begin{aligned}
\mathbb{E}[\mu_{ML}^2] &= \mathbb{E}\left[ \frac{1}{N^2} \left( \sum_{n=1}^N y_{n} \right)^2 \right] \\
&= \frac{1}{N^2} \mathbb{E}\left[ \sum_{n=1}^N y_{n}^2 + \sum_{j=1}^N\sum_{i=1}^{j-1} y_{i}y_{j} \right] \\
&= \frac{1}{N^2} \left[ \sum_{n=1}^N \mathbb{E}[y_{n}^2] + \sum_{j=1}^N\sum_{i=1}^{j-1} \mathbb{E}[y_{i}y_{j}] \right] \\
&= \frac{1}{N^2} \left( N(\mu^2 + \sigma^2) + 2\sum_{j=1}^N\sum_{i=1}^{j-1} \mu^2 \right)
\end{aligned}
>$$
>Ở đoạn cuối, ta thấy như sau:
>$$
\begin{aligned}
\sum_{j=1}^N\sum_{i=1}^{j-1} \mu^2 &= \mu^2 + 2\mu^2 + \dots + (N-1)\mu^2 \\
&= \frac{N(N-1)}{2} \mu^2 \\
\end{aligned}
>$$
>Thay ngược vào phương trình của $\mathbb{E}[\mu_{ML}^2]$ ta được:
>$$
\begin{aligned}
\mathbb{E}[\mu_{ML}^2] &= \frac{1}{N^2} \left( N(\mu^2 + \sigma^2) + N(N-1)\mu^2 \right) \\
&= \mu^2 + \frac{\sigma^2}{N} = \mathbb{E}[y_{n}\mu_{ML}]
\end{aligned}
>$$
>Sau khi đã có cả 3, ta chứng minh được, mình đi ngủ đây, dài vãi 💀.
>$$
\begin{aligned}
\mathbb{E}[\sigma^2_{ML}] &= \frac{1}{N} \sum_{n=1}^N \mathbb{E}[y_{n}^2] -\mathbb{E}[y_{n}\mu_{ML}] \\
&= \mu^2 + \sigma^2 - \mu^2 - \frac{1}{N}\sigma^2 \\
&= \frac{(N-1)}{N} \sigma^2
\end{aligned}
>$$
>
>My honest reaction:
><center><img width=300 height=300 src="https://preview.redd.it/man-im-dead-v0-ymr5u3c0bjsa1.jpg?auto=webp&s=364c87d710ec0cda25a8e23fcbf1dbd692d0a597"> </center>

Thế nhưng khi $N$ trở lên lớn dần, việc bias của nghiệm của maximum likelihood ($\sigma^2_{ML}$) không còn quá quan trọng nữa (ví dụ bạn có $N = 100001$ thì $N - 1 = 100000$ sẽ cho ra kết quả không quá chênh lệch). Khi mà $N \to \infty$ thì phương sai mẫu $\sigma^2_{ML}$ sẽ tiến dần về phương sai thực sự $\sigma$ của phân phối. Trong thực tế, nếu $N$ không nhỏ thì bias không phải là một vấn đề quan trọng lắm.

>[!note]+
>Việc phương sai mẫu $\sigma^2_{ML}$ tiến dần về phương sai thực sự $\sigma$ của phân phối khi mà $N \to \infty$ được chứng minh cụ thể ở **luật số lớn** (Law of Large Number).
>[Law of large numbers - Wikipedia](https://en.wikipedia.org/wiki/Law_of_large_numbers)
>[probability theory - Sample variance converge almost surely - Mathematics Stack Exchange](https://math.stackexchange.com/questions/243348/sample-variance-converge-almost-surely)

Tuy nhiên với các mô hình ML phức tạp có nhiều tham số thì vấn đề bias này lại trở nên nghiêm trọng. Ở các phần sau, tác giả sẽ cho thấy vấn đề bias của maximum likelihood là một trong những nguyên nhân gây ra over-fitting.

---

Phần trước: [[Zettel/Bayesian Probabilities\|Bayesian Probabilities]]
Phần sau: [[Zettel/Curve Fitting Revisited\|Curve Fitting Revisited]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.2)
- [Proof: Integral of PDF of Normal Distribution is Equal to 1 (in English) (youtube.com)](https://www.youtube.com/watch?v=8Ey7v8IoZjA)
- [probability - Expectation of sample variance - Mathematics Stack Exchange](https://math.stackexchange.com/questions/4017763/expectation-of-sample-variance)