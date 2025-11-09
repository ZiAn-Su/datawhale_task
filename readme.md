# HelloAgent学习之路
## 简介
参与datawhale 11月的学习课程，记录学习hello agent过程中的笔记和代码。
## 参考资料
https://datawhalechina.github.io/hello-agents/#/

## 第一章
- 智能体是能够感知环境并在环境中做出行动的实体。
- 参考资料：https://api.pageplace.de/preview/DT0400.9781292401171_A41586057/preview-9781292401171_A41586057.pdf
  
- 实践
```
用户输入: 你好，请帮我查询一下今天北京的天气，然后根据天气推荐一个合适的旅游景点。
========================================
--- 循环 1 ---

正在调用大语言模型...
大语言模型响应成功。
模型输出:
Thought: 用户请求查询北京的天气，然后根据天气推荐一个合适的旅游景点。因此，我需要先使用 get_weather 工具获取北京的实时天气信息，因为景点推荐依赖于天气条件。一旦获得天气，我将使用 get_attraction 工具来搜索推荐的景点。
Action: get_weather(city="北京")

Observation: 北京当前天气:Clear，气温5摄氏度
========================================
--- 循环 2 ---

正在调用大语言模型...
大语言模型响应成功。
模型输出:
Thought: 现在已获取北京的天气为晴朗（Clear），气温5摄氏度。接下来需要使用 get_attraction 工具，根据北京的晴朗天气来推荐合适的旅游景点。
Action: get_attraction(city="北京", weather="Clear")

Observation: In clear weather, the Forbidden City, Great Wall, and the Summer Palace are top Beijing attractions. These sites offer stunning views and rich history.
========================================
--- 循环 3 ---

正在调用大语言模型...
大语言模型响应成功。
模型输出:
Thought: 根据工具返回的信息，在晴朗天气下北京推荐的景点包括故宫、长城和颐和园。这些景点在晴天能提供最佳游览体验。现在可以给用户完整的答复了。
Action: finish(answer="北京当前天气晴朗，气温5摄氏度。推荐您游览故宫、长城或颐和园，这些景点在晴朗天气下视野开阔，能更好地欣赏历史建筑和自然风光。")

任务完成，最终答案: 北京当前天气晴朗，气温5摄氏度。推荐您游览故宫、长城或颐和园，这些景点在晴朗天气下视野开阔，能更好地欣赏历史建筑和自然风光。
```