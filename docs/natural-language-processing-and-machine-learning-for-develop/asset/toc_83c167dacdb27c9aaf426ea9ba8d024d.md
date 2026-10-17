
# 第 5 章 算法和工具包（I）
## 前言
## 这本书的核心价值是什么？
## 目标受众
## 为什么本书包含如此多的主题？
## 这本书是如何组织的，我将学到什么？
## 为什么这本书对深度学习的覆盖极少？
## 为什么代码示例主要使用 Python？
## 这本书需要多少 Keras 知识？
## 是否需要学习本书的理论部分？
## 代码示例是如何创建的？
## 如何从本书中获得最大收益？
## 这本书需要哪些先决知识？
## 伴随光盘是否消除了本书的必要性？
## 这本书是否包含生产级代码示例？
## 这本书的非技术先决条件是什么？
## 如何设置命令行？
## 伴随文件
## 作者其他书籍
## 完成本书后的“下一步”是什么？

# CHAPTER 1
# INTRODUCTION TO NUMPY
## 什么是 NumPy？
### 实用的 NumPy 特性
## 什么是 NumPy 数组？
## 使用循环
# -1 => "all *except* the last element in . . ." (row or col)
## Other Useful NumPy Methods
## Arrays and Vector Operations
## NumPy and Dot Products (1)
## NumPy and Dot Products (2)
## NumPy and the “Norm” of Vectors
## NumPy and Other Operations
## **NumPy 和 reshape() 方法**
## **计算均值和标准差**
### **修剪均值和加权均值**
### **包含均值和标准差的代码示例**
# 生成数据样本
# 计算四分位数、最小值和最大值
# 打印摘要信息
## # 在平面上工作（可选）
## # 使用 NumPy 和 Matplotlib 绘制直线
## # 使用 NumPy 和 Matplotlib 绘制二次函数
## # 什么是线性回归？
### # 什么是多元分析？
### # 非线性数据怎么办？
## **The MSE Formula**
### **Other Error Types**
### **Nonlinear Least Squares**
## **Calculating the MSE Manually**
## **Find the Best-Fitting Line with NumPy**
## 计算 MSE 的逐步逼近（1）
## **Google Colaboratory**
### **在 Google Colaboratory 中上传 CSV 文件**
## **Summary**

# CHAPTER 2
# INTRODUCTION TO PANDAS
## **What is Pandas?**
### **Pandas Options and Settings**
### **Pandas Data Frames**
### **数据框和数据清洗任务**
### **Pandas 的替代方案**
## **带有 NumPy 的 Pandas 数据框示例**
### `Transposing` a `Pandas` Data Frame
### `Pandas` Data Frames and Random Numbers
### 读取 CSV 文件
### `loc()` 与 `iloc()` 方法
### 将分类数据转为数值数据
## **Merging and Splitting Columns in Pandas**
# separate column for first name and for last name:
# concatenate year and month with a "#" symbol:
# concatenate year and month with a "-" symbol:
## 数据操作与 Pandas 数据框 (1)
## 数据操作与 Pandas 数据框 (2)
## 数据操作与 Pandas 数据框 (3)
## Pandas 数据框与 CSV 文件
## **Managing Columns in Data Frames**
### **Switching Columns**
### **Appending Columns**
### **Deleting Columns**
### **Inserting Columns**
### **Scaling Numeric Columns**
## 管理 Pandas 中的行
### 在 Pandas 中选择行范围
## **Handling Missing Data in Pandas**
### **Multiple Types of Missing Values**
### **Test for Numeric Values in a Column**
### **Replacing NaN Values in Pandas**
## **Sorting Data Frames in Pandas**
## **Working with groupby() in Pandas**
# colors and weights of balls: data = { 'color':\['red','blue','blue','red','blue'\],         'weight':\[40,50,20,30,90\]} df1 = pd.DataFrame(data)
## **Working with apply() and mapapply() in Pandas**
# df1 = df.apply(lambda x: x * x * x)
## **Save Data Frames as CSV Files and Zip Files**
# save data frame to CSV file:
# save data frame as CSV file in a zip file:
## **Pandas Data Frames and Excel Spreadsheets**
# optionally specify the sheet name:
# df1.to_excel("people.xlsx", sheet_name='Sheet_name_1')
## **Working with JSON-based Data**
### **Python Dictionary and JSON**
# convert JSON string to Python dictionary:
### **Python, Pandas, and JSON**
## `Pandas` and `Regular Expressions` (Optional)
# create a Pandas data frame:
# convert to lowercase:
# character count for each string in df['dow_of_week']:
# the number of tokens for each string in df['dow_of_week']
# the number of occurrences of digits:
# display all occurrences of digits:
# create new columns from hour:minute value:
# pattern splits email address into three components:
## **Useful One-Line Commands in Pandas**
## **What is Method Chaining?**
### **Pandas and Method Chaining**
## **Pandas Profiling**
## **What is Texthero?**
## **Summary**
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的起源**
### **语言流利度**
### **主要语言族群**
### **某些语言的高峰使用时期**
### **语言与地区口音**
### **语言与俚语**
### **语言和方言**
### **自然语言的复杂性**
### **句子中的词序**
### `What about Verbs?`
### `Auxiliary Verbs`
### `What are Case Endings?`
### **Languages and Gender**
### **Singular and Plural Forms of Nouns**
### **Changes in Spelling of Words**
## **Japanese Grammar**
### **Japanese Postpositions (Particles)**
### **Ambiguity in Japanese Sentences**
### **Japanese Nominalization**
### **Google Translate and Japanese**
### **Japanese and Korean**
### **Vowel-Optional Languages and Word Direction**
### **Mutating Consonant Spelling**
### **Expressing Negative Opinions**
## **Phonetic Languages**
### 音素和词根
### 英语中希腊语和拉丁语词源的单词
### 多种方式发音的辅音字母
### 字母 “j” 在各种语言中的发音
### “硬” 与 “软” 辅音发音
### “Ess”、“zee” 与 “sh” 音
### 三个连续的辅音
## 什么是 NLP？
### NLP 的演变
### NLP 的宽阔视角
#### NLP 应用和用例
### NLU 和 NLG
### 什么是文本分类？
### 信息提取与检索
### 词义消歧
## NLP 技术在机器学习中
### 训练模型的 NLP 步骤
## 文本归一化与分词
### 日语词汇分词
### `Text Tokenization with Unix Commands`
## `Handling Stop Words`
## `What is Stemming?`
### `Singular versus Plural Word Endings`
### `Common Stemmers`
### `Stemmers and Word Prefixes`
### `Over Stemming and Under Stemming`
## `What is Lemmatization?`
### `Stemming/Lemmatization` Caveats
### 词干和词根化的局限性
## `Working with Text: POS`
### `POS Tagging`
### `POS Tagging Techniques`
## `Working with Text: NER`
### 缩写和首字母缩写
### `NER Techniques`
## 什么是主题建模？
## 关键词提取、情感分析和文本摘要
## 总结
## **语言的