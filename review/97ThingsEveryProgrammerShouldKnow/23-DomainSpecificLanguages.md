# 领域专用语言

[Domain-Specific Languages](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_23/)

不论何时你听到任何领域内的专家在讨论，可以是国际象棋选手，幼儿教师，或者保险代理人，你都能发现他们的词汇与日常用语有很大的不同。这是领域专用语言(DSLs)的一部分：一个特定领域内的特殊词汇，用来描述领域内特定的某件事情。

在软件世界里，DLSs是领域专用语言的可执行表达式，具备有限的词汇和句法，可读、可理解，并希望领域专家可以编写。针对开发者和科学家的软件专用语言已经存在很长时间了。例如，Unix的“小语种”可以从配置文件中找到，而通过LISP宏创建的语言就是一些更古老的例子了。

领域专用语言通常根据内部或外部来分类：
- **内部领域专用语言**通过通用的编程语言编写，使其看起来更倾向于自然语言。相比于其他不用这种方式的语言(如Java)，这可以更方便给语言提供更多语法糖和格式化可能性(例如Ruby和Scalar)。很多内部领域专用语言包括令人兴奋的API、库、或者业务代码以及提供一个封装来减少对某些功能的诡异访问。只需要运行(run)它们就可以直接执行(excutable)。根据实现和领域，它们被用于构建数据结构，定义依赖，运行处理或任务，和其他系统通信，或者校验用户输入。内部领域专用语言受限于本地语言。有很多模式——例如，表达式构建器、方法链、以及注解——能够帮你把本地语言转换到内部领域专用语言。如果本地语言不具备重新编译，内部领域专用语言可以很快和领域专家肩并肩开发。