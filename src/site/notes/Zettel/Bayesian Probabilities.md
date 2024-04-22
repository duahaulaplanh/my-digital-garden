---
{"dg-publish":true,"permalink":"/zettel/bayesian-probabilities/","noteIcon":"📝","created":"2024-04-22T12:19:56.445+07:00","updated":"2024-04-22T19:14:51.539+07:00"}
---

Định lý Bayes cũng có thể áp dụng trong Machine Leanring như sau. Giả sử rằng ta có tập dữ liệu $\mathcal{D}$ và một model có bộ tham số là $\mathbf{w}$. Mục đích của ta là với tập dữ liệu $\mathcal{D}$ như này, bộ tham số $\mathbf{w}$ của ta như nào mới là tốt, tức là tìm xác suất $p(\mathbf{w} \mid \mathcal{D})$.

Giả sử ta đã chọn được một mô hình với bộ tham số $\mathbf{w}$. Trước khi có tập dữ liệu $\mathcal{D}$, ta ngầm giả định rằng $\mathbf{w}$ có phân phối là $p(\mathbf{w})$. Sử dụng định lý Bayes, ta có:
$$
p(\mathbf{w} \mid \mathcal{D}) = \frac{p(\mathcal{D} \mid \mathbf{w})p(\mathbf{w})}{p(\mathcal{D})}
$$
Phân phối $p(\mathcal{D} \mid \mathbf{w})$ ở bên phải của định lý Bayes là một hàm phụ thuộc vào $\mathcal{D}$, thế nhưng nếu ta xem phân phối ấy là một hàm phụ thuộc vào $\mathbf{w}$, thì khi đó ta gọi $p(\mathcal{D} \mid \mathbf{w})$ là **hàm likelihood** (likelihood function).

>[!note]+
>Thay vì viết $p(\mathcal{D} \mid \mathbf{w})$ để dễ bị nhầm lẫn giữa phân phối xác suất và hàm likelihood, ta sẽ kí hiệu:
>$$
\mathcal{L}(\mathbf{w} \mid \mathcal{D}) = p(\mathcal{D} \mid \mathbf{w})
>$$
>trong đó $\mathcal{L}(\mathbf{w} \mid \mathcal{D})$ là hàm likelihood có biến là $\mathbf{w}$ còn $p(\mathcal{D} \mid \mathbf{w})$ là phân phối có biến là $\mathcal{D}$.

Dựa vào định nghĩa của likelihood, ta có thể viết lại định lý Bayes như sau:
$$
\text{posterior} \propto \text{likelihood} \times \text{prior}
$$
>[!note]+
>Kí hiệu $\propto$ nghĩa là tỉ lệ. Ví dụ, chiều cao ($h$) $= 1.2 \times$ cân nặng ($w$), lúc này ta nói chiều cao tỉ lệ với cân nặng hay $h \propto w$. Ở định lý Bayes, nếu ta xem $1 / p(\mathcal{D})$ là một hằng số (mà nó là một hằng số thật, bởi vì $\mathcal{D}$ không đổi rồi) thì $p(\mathbf{w} \mid \mathcal{D}) \propto \mathcal{L}(\mathbf{w} \mid \mathcal{D})p(\mathbf{w})$.

trong đó $\text{likelihood}, \text{posterior}$ và $\text{prior}$ đều là các hàm phụ thuộc vào $\mathbf{w}$. Còn giá trị $p(\mathcal{D})$ dưới mẫu là một hằng số, dùng để đảm bảo rằng phân phối hậu nghiệm ở bên phải định lý Bayes đúng là một phân phối (mật độ xác suất).

>[!note]+
>Áp dụng sum rule và product rule ([[Zettel/Probability Densities\|Probability Densities]]) cho biến tục, ta có:
>$$
>p(\mathcal{D}) = \int p(\mathcal{D} \mid \mathbf{w}) p(\mathbf{w}) d\mathbf{w}
>$$
>Vậy:
>$$
\begin{aligned}
\int_{-\infty}^{\infty} p(\mathbf{w} \mid \mathcal{D}) d\mathbf{w} &= \int_{-\infty}^{\infty} \frac{p(\mathcal{D} \mid \mathbf{w})p(\mathbf{w})}{p(\mathcal{D})} d\mathbf{w} \\
&= \frac{\int p(\mathcal{D}\mid \mathbf{w})p(\mathbf{w}) d\mathbf{w}}{\int p(\mathcal{D}\mid \mathbf{w})p(\mathbf{w}) d\mathbf{w}} = 1
\end{aligned}
>$$
>Còn việc $p(\mathbf{w} \mid \mathcal{D}) \geq 0$ mình nghĩ khá là dễ thấy rồi.

---

Phần trước: [[Zettel/Expectations and covariances\|Expectations and covariances]]
Phần sau: [[Zettel/Gaussian Distribution\|Gaussian Distribution]]

---
# References

- [Bishop] Pattern Recognition and Machine Learning - Bishop (chapter 1.2)