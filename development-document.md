# Neighborhood Chef开发文档

## 数据库设计

表名：users  
说明：这张表由meteor维护，用于记录用户的信息。除去_id，username和password这三个字段是meteor自带的字段之外，
其他的都是我们添加的字段

| 字段名 | 类型 | 说明 |
|-------|-----|------|
| _id | string | meteor自动生成 |
| username | string | 用户名，同样是用户的唯一标识 |
| password | number | 用户注册时的密码 |
| address | string | 用户的地址 |
| phone | string | 用户的联系电话 |
| payment | string | 用户的账户信息 |
| profile_pic | picture | 用户的头像 |
| gender | string | 用户的性别 |


表名：orders  
说明：这张表用于记录订单信息

| 字段名 | 类型 | 说明 |
|-------|-----|------|
| _id | string | 订单的id， meteor自动生成 |
| create_time | date | 订单创建的时间 |
| end_time | date | 订单结束的时间 |
| status | number | 订单当前的状态 |
| customer_id | string | 下订单用户的id, 和Users表中的id一致 |
| cook_ id | string | 创建订单用户的id, 和Users表中的id一致 |
| recipe_id | string | 订单配料表的id |
| count | number | 订单的数量 |
| price | number | 订单的价格 |
| ready_time | date | 订单可取时间 |


表名：recipes  
说明：这张表用于记录菜谱的信息

| 字段名 | 类型 | 说明 |
|-------|-----|------|
| _id | string | 备料表的id, 和Order表中的recipe_id一致 |
| cook_id | string | 创建订单用户的id, 和users表中的id一致 |
| content | string | order 配料的具体内容 |
| nutrition | string | 每份配料的营养成分，调用API |
| price | string | 订单的价格， 和orders表中的价格一致 |
| available_time | date | 订单有效的时间范围 |

表名：recipe_comments
说明：这张表用于记录评价信息，可以考虑合并到order表内

| 字段名 | 类型 | 说明 |
|-------|-----|------|
| _id | string | 评价食物id |
| content | string | 评价的具体内容 |
| time | date | 评价的时间 |
| rating | number | 对食物的评分 |
| order_id | string | 订单的id, 和orders 表中的id 一致 |
| recipe_id | string | 备料表的id, 和 recipes 表中的id一致 |