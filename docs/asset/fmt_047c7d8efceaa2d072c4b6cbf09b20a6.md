
# 2x2

```python
f1=np.array([[2,2],[2,2]])

f2=np.array([[-1,-1],[-1,-1]])

f3=np.array([[-1,-1],[-1,-1]])

img=np.zeros((8,8,3))

for i in range(7):
    for j in range(7):
        img[i,j]=np.sum(img[i:i+2,j:j+2]*f1) # 示例代码逻辑

plt.imshow(red_index, cmap='gray')

max_index=np.argmax(red_index)

max_position=np.unravel(max_index, (8,8))

print(max_position)
```
