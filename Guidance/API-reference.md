# API 参考

本文档指明了试用期 web 日历应用在前后端对接时的 API 规范。后端成员需按照本规范实现接口，前端成员需参考本文档来调用接口。

## 总述

后端程序需将所有接口设计为 `<host>/<name>/<api_url>` 开头的url，以便服务器从 80 端口进行转发。举例：运行在 TB 服务器上的黄永晋设计的后端程序的 "/calendar" 接口的 URL 应设计为:

`https://www.tea-break.cn/hyj/calendar`

接口建议尽可能采用 RESTful 的接口设计。

有关时间的 JSON 字段，例如 `start_time`，无论接口做什么具体要求，都要给出完整的年月日时间，即需要包含以下示例中的全部字段：

```
{
    "start_time":{
        "year":2021,
        "month":1,
        "day_of_month":1,
        "hour":10,
        "minute":30,
    }
}
```

## API 索引

### 1.  `/event`

日历相关接口

#### 1.1 `GET /event?eid=x`

带参请求，根据 `event_id` 获取特定事件的详情。返回内容为 JSON 格式：
```
{
    "event_id":27,
    "event_name":"TB Week Meeting"
    "event_description":"",
    "organizer":[
        {
            "user_name":"TeaBreak",
            "user_id":"xxxxx",
        }
    ]
    "start_time":{
        "year":2021,
        "month":1,
        "day_of_month":1,
        "hour":10,
        "minute":30,
    },
    "end_time":{
        "year":2021,
        "month":1,
        "day_of_month":1,
        "hour":13,
        "minute":0,
    },
    "location":{
        "latitude":22.687320,
        "latitude":114.210455,
        "location_title":"TeaBreak",
        "location_id":null,
    },
    "capacity":21,
    "ap_num":10,
    "reg_time":{
        "start_time":{
            "year":2020,
            "month":12,
            "day_of_month":15,
            "hour":17,
            "minute":0,
        },
        "end_time":{
            "year":2021,
            "month":1,
            "day_of_month":1,
            "hour":10,
            "minute":0,
        }
    }
}
```
ap_mun: applicant number
reg_time: registration time

未知的字段使用 null。

#### 1.2 `GET /event?year=y&month=m`

获取某月的活动事件列表。使用 **查询字串** (query string) 进行带参请求。返回的数据为 JSON 格式

```
{
    "year":2021,
    "month":2,
    "events":[
        {
            "event_id":27,
            "day_of_month":1,
            "event_name":"TB Week Meeting"
            "event_description":"",
            "organizer":[
                {
                    "user_name":"TeaBreak",
                    "user_id":"xxxxx",
                }
            ]
            "start_time":{
                "year":2020,
                "month":12,
                "day_of_month":1,
                "hour":10,
                "minute":30,
            },
            "end_time":{
                "year":2020,
                "month":12,
                "day_of_month":1,
                "hour":13,
                "minute":0,
            },
            "capacity":21,
            "applicant_num":10,
        },
        {
            "event_id":27,
            "day_of_month":null,
            "event_name":"delicious tea break"
            "event_description":"",
            "organizer":[
                {
                    "user_name":"TeaBreak",
                    "user_id":"xxxxx",
                }
            ]
            "start_time":{
                "day_of_month":2,
                "hour":13,
                "minute":30,
            },
            "end_time":{
                "day_of_month":3,
                "hour":15,
                "minute":30,
            }
            "capacity":100,
            "applicant_num":99,
        }
    ]
}
```
其中 `year` 不提供则默认为当年，`month` 不提供则默认为当月。举例：

`GET /event` 获取当月的活动事件列表。

对于跨日跨月跨年事件，只要在本月有事件发生（正在发生、开始、结束、报名开始、报名结束、正在报名）就加入到列表中。如果跨日，则要将该事件的 `day_of_month` 设置为 `null`。前端将根据 `start_time` 和 `end_time` 中的日期信息来确定事件发生的日期。

本结果中不给出报名时间信息。

本结果中默认不给出地点信息。

本结果中不给出每个事件的发生年份和月份。


#### 1.3 `GET /event?year=y&month=m&week=w`

获取某月的活动事件列表。使用 **查询字串** (query string) 进行带参请求。

* year
* month: (1 ~ 12)
* week: week of month (1 ~ 6)

返回的数据为 JSON 格式

```
{
    "year":2021,
    "month":2,
    "week_of_month":1,
    "events":[
        {
            "event_id":27,
            "day_of_month":1,
            "event_name":"TB Week Meeting"
            "event_description":"",
            "organizer":[
                {
                    "user_name":"TeaBreak",
                    "user_id":"xxxxx",
                }
            ]
            "start_time":{
                "year":2020,
                "month":12,
                "day_of_month":1,
                "hour":10,
                "minute":30,
            },
            "end_time":{
                "year":2020,
                "month":12,
                "day_of_month":1,
                "hour":13,
                "minute":0,
            }
            "capacity":21,
            "applicant_num":10,
        },
        {
            "event_id":27,
            "day_of_month":null,
            "event_name":"delicious tea break"
            "event_description":"",
            "organizer":[
                {
                    "user_name":"TeaBreak",
                    "user_id":"xxxxx",
                }
            ],
            "start_time":{
                "year":2020,
                "month":12,
                "day_of_month":2,
                "hour":13,
                "minute":30,
            },
            "end_time":{
                "year":2020,
                "month":12,
                "day_of_month":3,
                "hour":15,
                "minute":30,
            },
            "capacity":100,
            "applicant_num":99,
        }
    ]
}
```
其中 `year` 不提供则默认为当年，`month` 不提供则默认为当月。`week_of_month` 不提供默认为当日所在的一周。

`GET /event` 获取当月的活动事件列表。

对于跨日跨月跨年事件，只要在本月有事件发生（正在发生、开始、结束、报名开始、报名结束、正在报名）就加入到列表中。如果跨日，则要将该事件的 `day_of_month` 设置为 `null`。前端将根据 `start_time` 和 `end_time` 中的日期信息来确定事件发生的日期。

本结果中不给出报名时间信息。

本结果中默认不给出地点信息。

本结果中不给出每个事件的发生年份和月份。


#### 1.4 `GET /event?year=y&month=m&day=w`

获取某月的活动事件列表。使用 **查询字串** (query string) 进行带参请求。

* year
* month
* day: day of month

返回的数据为 JSON 格式

```
{
    "year":2021,
    "month":2,
    "day_of_month":1,
    "events":[
        {
            "event_id":27,
            "event_name":"TB Week Meeting"
            "event_description":"",
            "organizer":[
                {
                    "user_name":"TeaBreak",
                    "user_id":"xxxxx",
                }
            ],
            "start_time":{
                "year":2020,
                "month":12,
                "day_of_month":1,
                "hour":10,
                "minute":30,
            },
            "end_time":{
                "year":2020,
                "month":12,
                "day_of_month":1,
                "hour":13,
                "minute":0,
            },
            "capacity":21,
            "applicant_num":10,
        },
        {
            "event_id":27,
            "event_name":"delicious tea break"
            "event_description":"",
            "organizer":[
                {
                    "user_name":"TeaBreak",
                    "user_id":"xxxxx",
                }
            ],
            "start_time":{
                "year":2020,
                "month":12,
                "day_of_month":2,
                "hour":13,
                "minute":30,
            },
            "end_time":{
                "year":2020,
                "month":12,
                "day_of_month":3,
                "hour":15,
                "minute":30,
            },
            "capacity":100,
            "applicant_num":99,
        }
    ]
}
```
其中 `year` 不提供则默认为当年，`month` 不提供则默认为当月。`week_of_month` 不提供默认为当日所在的一周。

`GET /event` 获取当月的活动事件列表。

对于跨日跨月跨年事件，只要在本日有事件发生（正在发生、开始、结束、报名开始、报名结束、正在报名）就加入到列表中。如果跨日，则要将该事件的 `day_of_month` 设置为 `null`。前端将根据 `start_time` 和 `end_time` 中的日期信息来确定事件发生的日期。

本结果中不给出报名时间信息。

本结果中默认不给出地点信息。

本结果中不给出每个事件的发生年份、月份、具体日期。
