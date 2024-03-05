---
{"dg-publish":true,"permalink":"/zettel/lam-quen-voi-du-lieu-p2/","created":"2024-03-05T12:54:21.953+07:00","updated":"2024-03-05T17:55:40.605+07:00"}
---

# III. Phép đo độ tương đồng và khác biệt của dữ liệu (TT)

## 8. Jaccard Similarity

- **Độ tương đồng Jaccard** (jaccard similarity) hay **hệ số Jaccard** (jaccard index) được dùng để đo sự tương đồng giữa các *tập hợp* với nhau.
- Xét hai tập hợp $A$ và $B$, khi đó độ tương đồng Jaccard là:
$$
\text{JSim}(A, B) = \dfrac{|A \cap B|}{|A \cup B|} = \dfrac{|A \cap B|}{|A| + |B| - |A \cap B|}
$$
- Có thể thấy:
	- $\text{JSim}(A, B) = 0$ nếu $|A \cap B| = 0$, nghĩa là $A$ với $B$ không có phần tử chung.
	- $\text{JSim}(A, B) = 1$ nếu $|A \cap B| = |A \cup B|$, nghĩa là $A$ với $B$ giống nhau.
	- Hiểu một nghĩa khác, độ tương đồng Jaccard chính là xác suất chọn được một phần tử mà nằm trong cả $A$ và $B$.
	- Giả sử $A = B = \emptyset$ thì $|A \cup B| = 0$, điều này không thể xảy ra được 🥲, thế nhưng theo định nghĩa tương đồng thì rõ ràng $A$ với $B$ giống nhau (đều là $\emptyset$) nên người ta quy ước rằng $\text{JSim}(\emptyset, \emptyset) = 1$.
- Ngoài ra ta có **khoảng cách Jaccard** là:
$$
\text{JDist}(A, B) = 1 - \text{JSim}(A, B) = \dfrac{|A \cup B| - |A \cap B|}{|A \cup B|}
$$
>[!note]
>[[Zettel/Chứng minh Jaccard Distance là một metric\|Chứng minh Jaccard Distance là một metric]]

Giả sử ta có 2 đối tượng dữ liệu có thuộc tính binary $A$ và $B$, nếu xem $A$ và $B$ như các tập hợp, ta sẽ có các trường hợp:
- $A \cap B$, nghĩa là thuộc tính tại $A = 0$ và $B = 0$ (gọi là $q$) hoặc tại $A = 1$ và tại $B = 1$ (gọi là $t$). Do đó $|A \cap B| = q + t$.
- Còn lại bao gồm $A = 1$ và $B = 0$ (gọi là $r$) hoặc $A = 0$ và $B = 1$ (gọi là $s$).
- Do đó $|A \cup B| = r + s + q + t$.
- Khi đó độ tương đồng Jaccard giống với độ đo proximity ở [[Zettel/Làm quen với dữ liệu (P1)#III. Phép đo độ tương đồng và khác biệt của dữ liệu\|Làm quen với dữ liệu (P1)#III. Phép đo độ tương đồng và khác biệt của dữ liệu#3. Độ đo proximity cho thuộc tính binary]]:
$$
\begin{aligned}
\text{JSim}(A, B) &= \dfrac{|A \cap B|}{|A \cup B|} = \dfrac{q + t}{q + r + s + t} \\
\Rightarrow \hspace{5pt} \text{JDist}(A, B) &= 1 - \text{JSim}(A, B) = \dfrac{r + s}{q + r + s + t} = d(A, B)
\end{aligned}
$$
## 9. Cosine Similarity

- Cho 2 đối tượng dữ liệu $X = (x_1, x_2, ..., x_p)$ và $Y = (y_1, y_2, ..., y_p)$ gồm $p$ thuộc tính. Khi đó **độ tương đồng cosine** giữa $X$ và $Y$ là:
$$
\text{sim}(X, Y) = \dfrac{X \cdot Y}{||X|| \hspace{3pt} ||Y||}
$$
- Trong đó:
	- $X \cdot Y$ là tích vô hướng của $X$ và $Y$.
	- $||X||$ là độ dài của $X$ hay là $L_2$-norm của $X$. Tương tự với $||Y||$.
- Nếu ta áp dụng lên *văn bản* thì $X$ và $Y$ là các *term-frequency* vector của hai văn bản mà ta muốn so sánh.
- Ngoài ra, ta có **khoảng cách cosine** là:
$$
d(X, Y) = 1 - \text{sim}(X, Y) 
$$
- Thế nhưng *khoảng cách cosine không phải là 1 metric*, xét ví dụ đơn giản sau đây: Giả sử ta có 2 vector $a = (1, 2)$ và $b = (2, 4)$ khi đó $\text{sim}(a, b) = 1$ nên $d(a, b) = 0$ nhưng khoảng cách giữa hai đối tượng khác nhau phải luôn $> 0$.

## 10. Correlation Coefficient

### a. Pearson correlation coefficient 

- Cho hai đối tượng dữ liệu gồm $p$ thuộc tính $X = (x_1, x_2, ..., x_p)$ và $Y = (y_1, y_2, ..., y_p)$ khi đó **hệ số tương quan pearson** giữa $X$ và $Y$ là:
$$
\text{Corr}(X, Y) = \dfrac{\sum_{i=1}^p(x_i - \overline{X})(y_i - \overline{Y})}{\sqrt{\sum_{i=1}^p(x_i - \overline{X})}\sqrt{\sum_{i=1}^p(y_i - \overline{Y})}} 
$$
- Trong đó:
	- $\overline{X}$ là mean của $X$, tương tự với $\overline{Y}$.
	- $\sigma_X = \sqrt{\sum_{i=1}^p(x_i - \overline{X})}$ là phương sai của $X$, tương tự với $Y$.
- Thông thường, ta gọi vector $X'$ là vector **chuẩn hoá** của $X$ nếu $X' = X - \overline{X} = (x_1 - \overline{X}, ..., x_p - \overline{X})$. Thế nên ở công thức trên, $\text{Corr}(X, Y)$ chính là độ tương đồng cosine giữa các vector chuẩn hoá. 

---
# References

- [book3.dvi (stanford.edu)](http://infolab.stanford.edu/~ullman/mmds/ch3.pdf)
- [Data Mining. Concepts and Techniques, 3rd Edition (The Morgan Kaufmann Series in Data Management Systems) (sabanciuniv.edu)](https://myweb.sabanciuniv.edu/rdehkharghani/files/2016/02/The-Morgan-Kaufmann-Series-in-Data-Management-Systems-Jiawei-Han-Micheline-Kamber-Jian-Pei-Data-Mining.-Concepts-and-Techniques-3rd-Edition-Morgan-Kaufmann-2011.pdf) (chương 2)