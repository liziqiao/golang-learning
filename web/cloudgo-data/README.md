## cloudgo-data


这里使用的是windows环境
--------------------------------
这里使用的是老师推荐使用的entity - dao - service层次结构编程模型。

entity层是实体类 ，充当一个对象的作用，也称为模型 ，这里定义相应的结构体以及相应的构造函数
dao层是使用了Hibernate连接数据库、操作数据库，错误处理也会放在这里。
service层：引用对应的Dao数据库操作，在这里编写业务逻辑。

ORM框架

对象-关系映射（Object/Relation Mapping，简称ORM），是随着面向对象的软件开发方法发展而产生的。面向对象的开发方法是当今企业级应用开发环境中的主流开发方法，关系数据库是企业级应用环境中永久存放数据的主流数据存储系统。

ORM方法论基于三个核心原则：

简单性：以最基本的形式建模数据。
传达性：数据库结构被任何人都能理解的语言文档化。
精确性：基于数据模型创建正确标准化了的结构。


数据库的创建，然后使用命令行创建两个表

![这里写图片描述](http://img.blog.csdn.net/20171202004139881?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3lzdWx6cQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

![这里写图片描述](http://img.blog.csdn.net/20171202004208817?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3lzdWx6cQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


使用cloudgo-data代码测试：


![这里写图片描述](http://img.blog.csdn.net/20171202004414210?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3lzdWx6cQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

![这里写图片描述](http://img.blog.csdn.net/20171202004433528?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3lzdWx6cQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


使用cloudgo-data-template测试，这使用了orm，测试结果如下：

![这里写图片描述](http://img.blog.csdn.net/20171202004455500?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3lzdWx6cQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

![这里写图片描述](http://img.blog.csdn.net/20171202004508116?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvc3lzdWx6cQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

使用ab测试可以看到,使用orm牺牲了一定的性能，总结优缺点如下：

优点：

程序员不再关注数据库细节，专心在业务逻辑，程序员可以不懂数据库就可以开发系统。
让数据库迁移变的非常方便，如果系统需要更改使用的数据库，直接改配制，不再管不同数据库之间的语法差异。
省时，可快速开发，因为不需要自己写复杂的SQL语句，不需要封装复杂的数据底层，这样可以节省很多时间。

缺点：

ORM不能帮你生成所有的业务语句，有些复杂的生成不了，还是需要写SQL，例如复杂的报表。
配制过于繁琐，出错后不好定位问题点在哪。
性能低，内部使用了大量反射以及数据库检测，造成性能必然低下。
需要额外的学习成本，虽然不需要学习数据库，但是需要学习ORM语句。
容易引起不规范开发，因为ORM可以在任何地方写ORM语句然后调用开发，给维护带来了很大的难度。

