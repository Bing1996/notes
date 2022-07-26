MySQL
===============

关于MySQL8.0的一些新特性
-----------------------------------

查找数据库重复
-------------------------

关于查找重复行数，使用delete和inner join语句的组合对MySQL进行去重，使用这个组合式，表需要至少有一个唯一的的列，例如主键：primary key with into automent;

下列代码为数据库H8卫星数据的处理，例如把2022年7月25日全天数据进行检索，找出由于debug所产生的重复行数，并且保证形同通道、扫描区域、扫描时间的记录有且只有一条，且满足第一范式原则。

.. code-block::
    
   DELETE t1 from H8_record t1
        INNER JOIN H8_record t2
    WHERE
        t1.H8_time BETWEEN '2022-07-25 00:00:00' AND '2022-07-25 23:50:00'
    AND t1.id < t2.id
    AND t1.H8_time = t2.H8_time and t1.channel_id = t2.channel_id and t1.scan_id = t2.scan_id;
