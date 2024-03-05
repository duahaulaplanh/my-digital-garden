---
{"dg-publish":true,"permalink":"/zettel/lam-quen-voi-du-lieu-p2/","created":"2024-03-05T12:54:21.953+07:00","updated":"2024-03-05T16:25:42.379+07:00"}
---

# III. Phép đo độ tương đồng và khác biệt của dữ liệu (TT)

## 7. Jaccard Similarity

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
## 8. Cosine Similarity

- 

---
# References

- [book3.dvi (stanford.edu)](http://infolab.stanford.edu/~ullman/mmds/ch3.pdf)
- 