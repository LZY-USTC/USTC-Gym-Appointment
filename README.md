# USTC-Gym-Appointment
中科大中区体育中心小程序预约脚本

支持通过统一身份认证登录进行中区体育馆场地预约（由于游泳预约平台已经迁移，目前该脚本只支持预约羽毛球场）

本项目仅供学习使用

# 环境

python=3.6+

见requirements.txt

# 使用方法

首先在config.yml中填写需要的字段（注意冒号与值之间需要有空格），例如：

```yaml
username: SA66668888
password: 12345678
time_ids: [3, 4, 5, 6]
people_number: 2
```
其中，time_ids为一个list，包含你想预约的全部时间段的id，对应关系如下：

|时间段|id|
|---|---|
|08:00-09:30|3|
|09:30-11:00|4|
|11:00-12:30|5|
|12:30-14:00|6|
|14:00-15:30|7|
|15:30-17:00|8|
|17:00-18:30|9|
|18:30-20:00|10|
|20:00-21:30|11|

例如，若你想预约14:00-21:30之间任意场次，就填: [7, 8, 9, 10, 11]

然后直接按下面方法调用脚本：

```python
from ustc_gym_appointment import USTCGymAppointment

bot = USTCGymAppointment()
bot.appointment()
```

取消预约方法：
```python
# 通过bot.cancel方法取消预约,参数reserve_id在预约成功后的返回结果中获取
bot.cancel(reserve_id)
```
