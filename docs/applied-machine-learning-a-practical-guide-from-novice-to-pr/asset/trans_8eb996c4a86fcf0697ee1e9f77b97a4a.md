
我们选择使用 Pythonanywhere（[Pythonanywhere](https://www.google.com/url?q=https://www.pythonanywhere.com/&sa=D&source=editors&ust=1720099682040546&usg=AOvVaw1SAR9Jd7pT-ohjVTBx6gpe)）作为本应用的托管平台，因为其稳健性和灵活性，使其非常适合我们的测试部署。Aiven 提供可靠的应用部署环境，并支持 Python 以及必要库的安装。然而，您可以自由选择任何支持 Python 并能够安装所需库或提供管理依赖关系的环境的部署平台。这种灵活性使您能够根据项目需求和运营偏好选择最合适的平台。

## Step 1: Access PythonAnywhere

在浏览器中访问 [Pythonanywhere](https://www.google.com/url?q=https://www.pythonanywhere.com/&sa=D&source=editors&ust=1720099682041114&usg=AOvVaw0StOAWzfUfgmSVhQZUG3eO) 以访问该平台。图 5-7 展示了 PythonAnywhere 的登陆页面。点击 **plans & pricing** 并点击“Create a Beginner account”按钮，如图 5-8 所示。  

![](OEBPS/image_rsrc57Y.jpg)Figure 5-7.

## Step 2: Start the onboarding process

点击图 5-8 中所示的按钮，启动入职流程。完成入职后，继续登录。  

![](OEBPS/image_rsrc57Z.jpg)Figure 5-8.

## Step 3: Login form

图 5-9 展示了登录表单，您需要在此输入登录信息以进入仪表盘。  

![](OEBPS/image_rsrc580.jpg)Figure 5-9.

## Step 4: Navigate to Files

从仪表盘点击 **Files** 链接，如图 5-10 所示。  

![](OEBPS/image_rsrc581.jpg)Figure 5-10.

## Step 5: Create a directory

为您的应用文件命名目录，点击 **New directory** 按钮创建它，如图 5-11 所示。  

![](OEBPS/image_rsrc582.jpg)Figure 5-11.

## Step 6: Upload files

进入您创建的 **mysite** 目录。点击 **Upload a file** 按钮，选择 `app.py` 并提交。重复此过程上传 `model.pkl`。上传的文件将如图 5-12 所示。  

![](OEBPS/image_rsrc583.jpg)Figure 5-12.

## Step 7: Access Web setup

点击 **Web** 链接，如图 5-13 所示。这将引导您进入 API 或应用的设置区域。  

![](OEBPS/image_rsrc584.jpg)Figure 5-13.

## Step 8: Add a new web app

点击“Add a new web app”按钮，然后选择默认域名的单选按钮，如图 5-14 所示。请注意，显示的名称会根据您的个人入职信息而变化，可能与示例不同。  

![](OEBPS/image_rsrc585.jpg)Figure 5-14.

## Step 9: Choose a web framework

选择与开发 API 所用的 Python Web 框架相匹配的框架，例如 Flask，如图 5-15 所示。  

![](OEBPS/image_rsrc586.jpg)Figure 5-15.

## Step 10: Choose Python version

选择您的解决方案所基于的 Python 版本。例如，如果您的 API 使用 Python 3.9 开发，请选择该版本，如图 5-16 所示。  

![](OEBPS/image_rsrc587.jpg)Figure 5-16.

## Step 11: Set the WSGI configuration file

图 5-17 显示了应用启动时执行的应用文件路径。保持默认设置并点击 **Next**。我们稍后会将路径从 `flask_app.py` 更改为 `app.py`（实际的应用文件名）。目前，点击“Next”按钮进入图 5-18 所示的界面。  

![](OEBPS/image_rsrc588.jpg)Figure 5-17.

Web 仪表盘显示我们的应用设置成功，如图 5-18 中的浅绿色指示信息所示。  

![](OEBPS/image_rsrc589.jpg)Figure 5-18.

## Step 12: Edit WSGI configuration

向下滚动至图 5-19 所示区域。点击“WSGI configuration file”链接以编辑文件，并将其更新为启动 API 时应指向的文件。当前指向 PythonAnywhere 主机默认创建的文件，如图 5-20 所示。将图中高亮项更改为图 5-21 中的内容。  

![](OEBPS/image_rsrc58A.jpg)Figure 5-19.  

![](OEBPS/image_rsrc58B.jpg)Figure 5-20.  

![](OEBPS/image_rsrc58C.jpg)Figure 5-21.

## Step 13: Reload the application

向上滚动并点击“Reload anyasorchigozie.pythonanywhere.com”按钮，以刷新应用配置，如图 5-22 所示。  

![](OEBPS/image_rsrc58D.jpg)Figure 5-22.

## Step 14: Access the API

我们的 API 现在可在以下 URL 访问：[http://anyasorchigozie.pythonanywhere.com/api/custype](https://www.google.com/url?q=http://anyasorchigozie.pythonanywhere.com/api/custype&sa=D&source=editors&ust=1720099682046404&usg=AOvVaw3x0oFS1EKDQMIENm_UZnSC)，如图 5-23 所示。  

![](OEBPS/image_rsrc58E.jpg)Figure 5-23. 这与本地测试时的输出相同，表明我们的 API 与模型已成功部署，并可供应用调用以解决业务问题。

# Conclusion

在第 5 章中，我们探讨了如何将机器学习模型转换为 pickle 文件，并无缝地将其集成到应用作为 API。这一过程使我们能够在真实场景中运营机器学习模型。在支持 Python 应用的平台上托管这些 API 对于最大化机器学习在组织中的实用性至关重要。它使企业能够在全企业范围内充分挖掘机器学习投资的价值。

该方法不仅适用于单一行业；一旦模型训练完成，将其转换为 API 并部署，便可实现跨行业的广泛应用。这种做法确保了机器学习的益处 —  — 从改进决策到自动化 —  — 能在各种行业和场景中得到实现。

随着我们机器学习之旅的结束，我鼓励您继续练习并探索 AI 所提供的自动化和创新机遇。手握创作的力量，充满热情地投身于编码实践。祝编码愉快！

# References

Katrina, W. (n.d). *A guide to the types of machine learning algorithms and their applications*. sas.com. https://www.sas.com/en_gb/insights/articles/analytics/Machine-learning-algorithms.html

Namitha, V. (2022). *How Machine Learning Improves Retail Demand Forecasting*. Algonomy. https://algonomy.com/blogs/retail/how-machine-learning-improves-retail-demand-forecasting/

Volodymyr, A. (2024). *Machine Learning Predictive Maintenance: How to Implement It?* Lemberg Solutions. https://lembergsolutions.com/blog/machine-learning-predictive-maintenance-how-implement-it

![](OEBPS/image_rsrc58F.jpg)
