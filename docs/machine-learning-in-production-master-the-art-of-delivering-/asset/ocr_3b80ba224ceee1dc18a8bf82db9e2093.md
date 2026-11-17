```
19. else:
20.     pred = 'Rejected'
21.
22.     return {'status':pred}
23.
24.
25. if __name__ == '__main__':
26.     pass
```

The file for FastAPI is completed.

# requirements.txt

Now, create the requirements.txt file, as follows. In this file, you can define the model requirements, test requirements, and FastAPI requirements separately for better understanding and ease of management.

```
1. # Model building requirements
2. joblib==0.16.0
3. numpy==1.19.0
4. pandas==1.0.5
5. scikit-learn==0.23.1
6. scipy==1.5.1
7. sklearn==0.0
8.
9. # testing requirements
10. pytest<5.0.0,>=4.6.6
11. requests
12.
13. # packaging
14. setuptools==40.6.3
15. wheel==0.32.3
16.
17. # FastAPI app requirements
18. fastapi>=0.68.0,<0.69.0
```