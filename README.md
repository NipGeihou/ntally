## 简介

　　市面上存在的记账app，其主要功能就是对每一笔账记录、管理，而对我来讲，实在没那么多时间细抠每一笔账，只是想每隔一段时间（比如：发工资）统计下这段时间的花费情况，因此编写这个系统，用`浏览器`+`图表`的形式，更直观的看到自己的财务情况，从而调整接下来一段时间的开支，并且集成对信用消费（信用卡、花呗、白条）出账日、最后还款日的图形化显示。



## 技术栈

PHP+ThinkPHP5+ZUI+JQuery



## 数据库设计

### n_account 账户表

- id
- title 名称
- type 类型 (bank 银行卡,e-wallet 电子钱包....)
- is_credit 是否是信用支付
- money 金额
- create_time 创建时间
- update_time 更新时间
- status 状态(1正常，0禁用，-1删除)

### tally 账单表

- id
- payment_id 支付方式ID
- type 收支类型（in、out）
- money 金额
- remark 备注说明
- create_time 创建时间
- update_time 更新时间
- status 状态(1正常，0禁用，-1删除)

### n_loan 借贷表（分期）

- id
- type（in贷款、out借出）
- money 金额
- title 名称
- is_immediately 是否马上还
- remark 备注说明
- create_time 创建时间
- update_time 更新时间
- status 状态(1正常，0禁用，-1删除)



## n_summary 汇总表

- id
- total_assets 总资产
- recent_disposable 近期可支配资产
- create_time 创建时间
- update_time 更新时间
- status 状态(1正常，0禁用，-1删除)

## n_summary_batch 汇总批次表

- id 
- summary_id 汇总ID
- create_time 创建时间
- update_time 更新时间
- status 状态(1正常，0禁用，-1删除)