 核心组件

- **DispatcherServlet：**前端控制器，是整个**流程控制的核心**，控制其他组件的执行，统一调度，降低组件之间的耦合性，相当于总指挥。
- **Handler：**处理器，完成具体业务逻辑，相当于 Servlet 或 Action。
- **HandlerMapping：**DispatcherServlet 接收到请求之后，通过 HandlerMapping 将不同的请求分发到不同的 Handler。
- **HandlerInterceptor：**处理器拦截器，是一个接口，如果我们需要做一些拦截处理，可以来实现这个接口。
- **HandlerExecutionChain：**处理器执行链，包括两部分内容，Handler 和 HandlerInterceptor（系统会有一个默认的 HandlerInterceptor，如果需要额外拦截处理，可以添加拦截器设置）。
- **HandlerAdapter：**处理器适配器，Handler 执行业务方法之前，需要进行一系列的操作，包括表单数据的验证、数据类型的转换，将表单数据封装到 JavaBean 等这一系列的操作，都是由 HandlerAdapter 来完成，DispatcherServlet 通过 HandlerAdapter 执行不同的 Handler。
- **ModelAndView：**装载了模型数据和视图信息，作为 Handler 的处理结果，返回给 DispatcherServlet。
- **ViewResolver：**视图解析器，DispatcherServlet 通过它将逻辑视图解析成物理视图，最终将渲染结果响应给客户端。

请求调用流程

- 客户端请求被 DispatcherServlet（前端控制器）接收。

- 根据 HandlerMapping 映射到 Handler。
- 生成 Handler 和 HandlerInterceptor（如果有则生成）。
- Handler 和 HandlerInterceptor 以 HandlerExecutionChain 的形式一并返回给 DispatcherServlet。
- DispatcherServlet 通过 HandlerAdapter 调用 Handler 的方法做业务逻辑处理。
- 返回一个 ModelAndView 对象给 DispatcherServlet。
- DispatcherServlet 将获取的 ModelAndView 对象传给 ViewResolver 视图解析器，将逻辑视图解析成物理视图 View。
- ViewResolver 返回一个 View 给 DispatcherServlet。
- DispatcherServlet 根据 View 进行视图渲染（将模型数据填充到视图中）。
- DispatcherServlet 将渲染后的视图响应给客户端。

![enter image description here](https://ws1.sinaimg.cn/large/bd9c8deely1fx23ct75g4j21gj0noamb.jpg)



【?】疑问拦截器实现的设计模式，以及多个拦截器的调用的先后关系