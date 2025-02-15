# RAG
# 项目环境搭建
# 下载开源模型到本地
    - embeddings models 文本向量化
    - 文本生成模型
        - Qwen2.5
            - 国内用的最多的版本 7b
        - InteInLM
    - 下载
        - hugging face
        - modelscope
    
    - 如果文档语料库既有中文也有英文（跨语言）
        - text-emmbedding-ada-002 (openai)
            - 购买 key
            - 按token付费

# RAG 问答系统
    1、LangChain
    2、LLM GPT4o
    3、Embeddeds 模型
    4、向量数据库 Vector store
    5、文档处理
        加载、切割、向量化、存储

# RAG原理
    一、Indexing索引       
        - 加载文件
        - 读取文本
        - 文本分割（原因：目前大模型输入长度受限）
        - 文本向量化（便于相似度匹配）

    二、Retrieval检索  
        - 问句向量化
        - 文本向量中匹配出与问句向量最相似的top k个
        - 匹配出的文本作为上下文和问题一起添加到prompt中

    三、Generation生成
        - 提交给LLM生成回答

# RAG中的Prompt模板

```
"""
已知信息：{context}
根据上述已知信息，简洁和专业的来回答用户的问题。如果无法从中得到答案，请说“根据已知信息无法回答该问题”或“没有提供足够的相关信息”，不允许在答案中添加编造成分，答案请使用中文。
问题是：{question}
"""

其中{context}是检索出来的文档
```

# 检索架构
    先检索（重点）
    后推理（交给LLM）

    检索要求
        1、提高召回率
        2、减少无关信息（减少噪声） 准确率要高
        3、检索速度

    检索逻辑
        关键词keyword
