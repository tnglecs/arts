# 辨别来自技术中的业务异常

[Distinguish Business Exceptions from Technical](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_21/)

导致运行时出错的事情根本上来说有两种原因：阻止我们使用程序的技术问题，以及组织我们滥用程序的业务逻辑。很多现代语言，如LISP、Java、Smalltalk和C#，运用异常来标记这两种情况。然而，这两种情况完全不同，要严格区分开。用相同级别的异常来描述他们会混淆潜在的来源，不要继承相同的异常类。

但有一个程序错误时，可能是一个无法解决的技术问题导致的。例如，如果你尝试去访问长度为17的数组中的第83个元素，程序明显会跑飞，得到一些异常结果。有些小版本调用一些参数不当的代码库，导致内部库出现相同的情况。

试图解决你自己造成的情况可能会是个错误。我们会把这个异常上升到顶层架构级别，并采用一些异常处理机制让其确保系统处于一个安全状态，比如回滚、日志和通知管理员，以及反馈(客气的)给用户。

当你处在“库情况”中，调用者还违反你方法的调用规则，是这些情况的一个变种，例如，传入一个奇怪的参数或者没有正确设置依赖的对象。这就等同于从17个(长度数组)里面访问第83个：调用者应检查；否则就成了客户端开发程序员的错误了。正确的响应是抛出一个技术异常。

有个不同的，但也属于技术范畴的情况，当一个程序由于运行环境问题导致无法继续，例如数据库无响应。在这种情况下，你必须假设基础设施能够解决这些问题——修复连接以及合理的重连几次——最后失败。即便原因不同，对于调用者而言这些情况是类似的：能做的很少。所以，我们把这个情况当作异常信号抛出交给一般异常处理机制。

与此相反，我们遇到的情况是你无法完成领域逻辑调用的原因。因此我们将其视作异常情况。即不常见且让人不爽的，但并非怪异或者编程错误。例如，我尝试从一个余额不足的储蓄账户中取钱。换而言之，这种情况是约定的一部分，抛出一个异常仅用来*取代返回路径*，它是模型的一部分，客户能够意识到并着手应对。对于这些情况，适合创建一个特定异常或者异常此层结构，以便客户能根据自己的项目处理这些情况。

把技术异常和业务异常混淆成相同的层次结构，含糊的差异，让调用者困惑于这些方法的约定是什么，什么是调用前必须的前提条件，它应该处理什么情况。分清这些情况，可能增加技术异常被一些程序框架处理掉的几率，而业务领域的异常实际上是由客户端代码考虑并处理的事情。
