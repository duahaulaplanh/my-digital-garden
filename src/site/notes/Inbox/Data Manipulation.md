---
{"dg-publish":true,"permalink":"/inbox/data-manipulation/","created":"2024-02-26T09:09:02.907+07:00","updated":"2024-02-26T09:49:47.865+07:00"}
---

# Content

>[!note]
>Nhớ dùng
>```python 
>torch.set_default_device("cuda")
>```
>(hoặc GPU khác) để mặc định dùng GPU, nếu không, pytorch sẽ default dùng CPU.

- Một tensor có thể được hiểu là một array nhiều chiều (n-dimensional array).
- Ta gọi tensor 0 chiều là **scalar**, 1 chiều là **vector**, 2 chiều là **matrix**, lớn hơn nữa gọi là **tensor bậc-k** (k-order tensor).
```python
# Ví dụ:
T = 0 # là 1 tensor (0 chiều)
T = [1, 2, 3] # là 1 tensor (1 chiều)
T = [[1, 2, 3], [4, 5, 6]] # (2 chiều)
T = [[[1, 2, 3],
	  [4, 5, 6]]
	  [[7, 8, 9],
	  [10, 11, 12]]] # (3 chiều)
``` 
- **Pytorch** có các hàm ```arange, reshape``` và attribute ```shape``` tương tự như **numpy**.
```python
X = torch.arange(start=0,
				 end=10,
				 step=1,
				 dtype=torch.int64)
# X = tensor([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

X.shape
# X.shape = torch.Size([10])

X.reshape(2, 5) # hàm này không inplace
# X = tensor([[0, 1],
#             [2, 3],
#             [4, 5],
#             [6, 7],
#             [8, 9]])
```
---

# References

- [2.1. Data Manipulation — Dive into Deep Learning 1.0.3 documentation (d2l.ai)](https://d2l.ai/chapter_preliminaries/ndarray.html)