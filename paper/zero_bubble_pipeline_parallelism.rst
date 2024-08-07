zero bubble pipeline parallelism
=====================================

流水线并行是大规模分布式训练的核心技术，但其效率常受流水线气泡的严重影响，这一挑战难以忽视。
在这项工作中，我们介绍了一种调度策略，据我们所知，这是首次在同步训练语义下成功实现零流水线
气泡的策略。这项改进背后的关键思想是将反向计算拆分为两部分，一部分计算输入的梯度，另一部分
计算参数的梯度。基于这一思想，我们手工设计了新颖的流水线调度方案，在性能上显著优于基准方法。
我们还开发了一种算法，该算法可以根据特定的模型配置和内存限制自动找到最优调度方案。此外，为了
真正实现零气泡，我们引入了一种新技术来绕过优化器步骤中的同步操作。

论文总结参加微信: `zero_bubble_pipeline_parallelism`_

.. _zero_bubble_pipeline_parallelism: https://mp.weixin.qq.com/s?__biz=MzA5MTQxMTM0Nw==&mid=2247484690&idx=1&sn=209e6657f0d7bc82e81155400106e0db&chksm=91d081bb2ff97f291275d91d8d93b8ae7b5ee9013a9522aa8a16b54bd69fae1e595b12efeb6d&xtrack=1&scene=90&subscene=93&sessionid=1720747606&flutter_pos=0&clicktime=1720747689&enterid=1720747689&finder_biz_enter_id=4&ranksessionid=1720747239&ascene=56&fasttmpl_type=0&fasttmpl_fullversion=7289491-zh_CN-zip&fasttmpl_flag=0&realreporttime=1720747689878&devicetype=android-31&version=2800315a&nettype=cmnet&abtest_cookie=AAACAA%3D%3D&lang=zh_CN&session_us=gh_89fa82b0efb8&countrycode=CN&exportkey=n_ChQIAhIQOa2stcCH%2BPxl%2FXSYJHVYkBLxAQIE97dBBAEAAAAAAIIQNCwO40oAAAAOpnltbLcz9gKNyK89dVj0WvafaqY4i0TBIf2%2FGaIhRSzNJkcSQk%2BsrF2VFi5f%2FY2Nua1IFp8ee27SbOucXva8Yx%2Bp%2BBac%2FSHWlYY1AEwKC%2FfJAcBchHfz%2BLlvyhh0TrZGWYLy4YLXL6KVv3Rfc6kS9qhW5cKW69oejKdq2chRJs6JJaAVCUL7XObnL%2FJnsvGsmrgkiHIaINcQ5LHjTRqf0JJwEQb7%2FJOAOPVN%2FkpRsjKwZLSiaqeWxUO2vtOBu8xBtAio5FWk2eGQXhOyxiqYVvrbOVJcucCi%2BX4%3D&pass_ticket=NX0m7Y9N5jvSUwWXVdHPszgOpYcJHZ%2BxNf7U%2By2TshSBlbONlHTbW%2B2JQ7fDR41s&wx_header=3
