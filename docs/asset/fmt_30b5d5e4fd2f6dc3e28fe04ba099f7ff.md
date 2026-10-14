
`memory = ConversationBufferMemory()`

# 创建对话链

`conversation = ConversationChain(llm=llm, memory=memory)`

# 与记忆进行聊天

```
response = conversation.run("告诉我关于 Python 编程的内容。")

print(response)

response = conversation.run("关于 Django 呢？")

print(response)  # 聊天机器人会记住上下文！
```

## 设计用户友好的流程

### 对话式用户体验最佳实践

- 使用清晰提示 → 通过建议操作引导用户。
- 提供兜底选项 → 优雅处理模糊输入。
- 允许更正 → 让用户修改其输入。
- 保持响应简洁 → 避免冗长、混淆的回复。

### 示例：处理兜底的聊天机器人

```python
def chatbot_response(user_input):
    # 检查输入是否匹配已知意图
    if "balance" in user_input.lower():
        return "您的账户余额是 5,000 美元。"
    elif "transfer" in user_input.lower():
        return "您想转账多少？"
    else:
        return "抱歉，我未理解您的话。您能重新表述吗？"

print(chatbot_response("我账户里有多少钱？"))  # 识别到意图
print(chatbot_response("讲个笑话"))  # 兜底回复
```

## 测量聊天机器人性能

### 评估关键指标

- 意图识别准确率 – 衡量聊天机器人理解用户查询的能力。
- 响应延迟 – 确保快速、实时的交互。
- 用户满意度 – 追踪用户参与度和反馈评分。

#### Python 代码：测量延迟

```python
import time

start_time = time.time()

response = chatbot_response("告诉我关于 AI 伦理的内容。")

end_time = time.time()

print("响应时间：", end_time - start_time, "秒")
```

### 8.2 将 DeepSeek AI 集成到聊天框架（Python、LangChain）

在本节中，我们探讨如何将 DeepSeek AI 与流行的聊天框架（如 LangChain）集成，以构建智能、对话式人工智能代理。目标是提供实用的指导，配有实践代码示例，涵盖意图检测、响应生成和对话管理。

### 了解聊天框架

聊天框架提供构建 AI 驱动对话系统的工具、库和工作流。

为什么使用框架？

- 预建 NLP 工具 → 节省时间，提供即插即用的组件。
- 上下文跟踪 → 保持对话历史以实现更好的响应。
- 可扩展性 → 可轻松集成到 API、数据库和外部工具中。

#### 热门聊天框架

- `Rasa` → 开源对话式人工智能。
- `Google Dialogflow` → 基于 NLP 的聊天机器人平台。
- `LangChain` → 为 LLM 驱动的应用（DeepSeek AI、OpenAI 等）构建的框架。

### 设置开发环境

构建基于 DeepSeek AI 的聊天机器人，需要安装所需依赖：

```bash
pip install langchain openai deepseek-ai
```
