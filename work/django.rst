django总结
^^^^^^^^^^^^^^^^^^^^

数据库models
=================

数据库的表为app_method小写。

迁移是非常强大的功能，它能让你在开发过程中持续的改变数据库结构而不需要重新删除和创建表。
它专注于使数据库平滑升级而不会丢失数据。我们会在后面的教程中更加深入的学习这部分内容，
现在，你只需要记住，改变模型需要这三步：
- 编辑 `models.py` 文件，改变模型。
- python manage.py makemigrations polls（表名为polls）
- python manage.py migrate