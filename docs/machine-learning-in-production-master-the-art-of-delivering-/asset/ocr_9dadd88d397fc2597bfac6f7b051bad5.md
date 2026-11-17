```
30. run: |
31. tox
32.
33. - name: Login via Azure CLI
34. uses: azure/login@v1
35. with:
36. creds: ${{{ secrets.AZURE_CREDENTIALS }}}
37.
38. - name: Login to Azure Container Registry
39. uses: azure/docker-login@v1
40. with:
41. login-server: mlappcd.azurecr.io
42. username: ${{{ secrets.REGISTRY_USERNAME }}}
43. password: ${{{ secrets.REGISTRY_PASSWORD }}}
44.
45. - name: Build and push container image to the registry
46. run: |
47. docker build . -t mlappcd.azurecr.io/mlapp-cd:${{{ github.sha }}}
48. docker push mlappcd.azurecr.io/mlapp-cd:${{{ github.sha }}}
49.
50. - name: Deploy to App Service
51. uses: azure/webapps-deploy@v2
52. with:
53. app-name: 'mlapp-cd'
54. images: 'mlappcd.azurecr.io/mlapp-cd:${{{ github.sha }}}'
55.
56. - name: Azure logout
57. run: |
58. az logout
```

Next, create the repository on GitHub for this (if not created already) and push the codebase into that repo.