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

datefiled字段处理
-----------------------

需要从excel中读取日期存入sqlite3数据库中，然后django从数据库中读出。遇到的问题是django
无法识破格式，报错"none type"。AI指出这是因为excel的日期类型是datetime.datetime,而django
的格式是datetime.datetime.date()。转换为date后，django能读出数据。



表单
===========

form的实例用{{form.as_p}}输出。

HTML模板语法
===================

for语法
--------------

::HTML

    {%for item in 列表%} 
	    // 循环逻辑 
	    {{forloop.counter}}表示当前是第几次循环，从1开始 
	    {%empty%} 列表为空或不存在时执行此逻辑 
    {%endfor%}

if语法
---------------

::HTML

    {%if ...%}
	    逻辑1
    {%elif ...%}
	    逻辑2
    {%else%}
	    逻辑3
    {%endif%}


第三方插件
=================

第三方插件如下 `django_package`_

.. _django: https://djangopackages.org/


网页
=============

分页机制
------------

下面是一段将表格分页显示的代码，post_list为paginator.page()返回。
.. code-block:: html

        <div class="pagination">
                <span class="step-links">
                        {% if post_list.has_previous %}
                        <a href="?page=1">&laquo; 第一页</a>
                        <a href="?page={{ post_list.previous_page_number }}">上一页</a>
                        {% endif %}

                        <span class="current-page">
                                第 {{ post_list.number }} 页，共 {{ post_list.paginator.num_pages }} 页。
                        </span>

                        {% if post_list.has_next %}
                        <a href="?page={{ post_list.next_page_number }}">下一页</a>
                        <a href="?page={{ post_list.paginator.num_pages }}">最后一页 &raquo;</a>
                        {% endif %}
                </span>
        </div>