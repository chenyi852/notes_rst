mcp_servers
^^^^^^^^^^^^^^^^^^^

什么是MCP
============

**MCP**(Model Context Protocol, 模型上下文协议)是由Anthropic提出并于2024年11月开源
的一种通信协议，旨在解决大型语言模型(LLM)与外部数据源及工具之间无缝集成的需求。

它通过标准花AI系统与数据源的交互方式，帮助模型获取更丰富的上下文的信息，从而生成更
准确、更相关的响应。

**主要功能**

#. **上下文共享**: 应用程序可以通过MCP向模型提供所需的上下文信息(如文件内容、数据库
   记录等）， 增强模型的理解能力。

#. **工具暴露**: MCP允许应用程序将功能(如文件读写、API调用)暴露给模型，模型可以调用
   这些工具完成复杂任务。

#. **可组合的工作流**: 开发者可以利用MCP集成多个服务和组件，构建灵活、可扩展的AI
   工作流。

#. **安全性**: 通过本地服务器运行，MCP避免将敏感数据上传至第三方平台，确保数据隐私。

MCP架构
=============

MCP采用客户端-服务器架构:

#. **MCP客户端(client)**: 通常是AI应用程序(如Clande Desktop或其他LLM工具),负责发起
   请求并与服务器通信。

#. **MCP服务器(server)**: 轻量级程序，负责暴露特定的数据源或工具功能，并通过标准化
   协议。

**通信格式**: 基于JSON-RPC 2.0, 支持请求、响应和通知三种消息类型，确保通信的标准化
和移植性。

MCP Servers主要功能
----------------------

MCP Servers作为一个轻量级的本地服务，旨在为客户端提供数据访问和功能执行的接口。

#. 资源暴露(Resource Exposure)

   资源是服务器提供给客户端的数据实体，可以是文件、数据库记录、内存中的对象等。

   例如：

   #. 文件资源: file///home/user/report.txt

   #. 内存资源: memo://recent-insights

   #. 工具提供(Tool Provisoning)

   工具是服务器暴露的可执行功能，客户端可以通过这些工具完成特定任务。

   例如：

   #. 查询数据库: query_database(参数: SQL语句， 返回: 查询结果)

   #. 文件写入: write_file(参数: 文件路径、内容)

#. 动态通知(Dynamic NOtification)

   当资源发生变化时，服务器可以通过通知机制(如 notificatoin消息)主动推送更新到客户端。

#. 会话管理(Session Management)

   处理客户端的连接初始化、能力协商和会话关闭。

MCP Client
---------------

MCP Client一般选用AI应用程序(如 Clande Desktop、cline或其他LLM工具), 负责发起请求
并与服务器通信。
