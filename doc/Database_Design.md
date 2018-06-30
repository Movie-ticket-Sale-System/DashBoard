## 1. ER模型

![](https://github.com/Movie-ticket-Sale-System/DashBoard/raw/master/image/系统ER模型.jpg) 

## 2. 关系模型

- 用户: 电影票 = 1 : N

  用户 ( **用户ID**, 用户NAME )

  电影票 ( **电影票ID**, 电影票价格, 电影票信息, 支付状态, 备注 )

  订票 ( **用户ID**, 电影票ID, 时间, 影院)

  - **主键**: 用户ID
  - **外键**: 电影票ID

- 电影院 : 电影 = 1 : N

  电影院 ( **电影院ID**, 电影院NAME )

  电影 ( **电影ID**, 电影信息,, 备注 )

  管理 ( **电影院ID**, **电影ID**)

  - **主键**: **电影院ID**
  - **外键**: **电影ID**

  

## 3.数据库物理模型

### 1. register表

|    字段    |    类型     |  空  |       默认        |    注释    |
| :--------: | :---------: | :--: | :---------------: | :--------: |
| **reg_id** | bigint(20)  |  No  |                   |   注册id   |
|   phone    | varchar(64) |  No  |                   |  注册号码  |
|    code    |  char(32)   |  No  |                   | 注册验证码 |
| create_at  |  datetime   | Yes  | CURRENT_TIMESTAMP |  注册时间  |

### 2. user表

|    字段     |     类型     |  空  |       默认        |      注释      |
| :---------: | :----------: | :--: | :---------------: | :------------: |
| **user_id** |  bigint(20)  |  No  |                   |     用户id     |
|    phone    | varchar(64)  |  No  |                   |    电话号码    |
|  password   |   char(32)   |  No  |                   | 密码，加密保存 |
|    name     | varchar(128) | Yes  |       NULL        |     用户名     |
|   pay_num   | varchar(64)  | Yes  |       NULL        |    支付账号    |
|  create_at  |   datetime   | Yes  | CURRENT_TIMESTAMP |    注册时间    |

### 3. movie表

|    字段     |     类型     |  空  | 默认 |   注释    |
| :---------: | :----------: | :--: | :--: | :-------: |
| **mov_id**  |  bigint(20)  |  No  |      |  电影id   |
|    name     | varchar(128) |  No  |      |  电影名   |
|    grade    |    float     | Yes  |  0   |   评分    |
|  starttime  |   datetime   |  No  |      | 上映时间  |
|    type     |     text     | Yes  | NULL | 影片类型  |
|   region    |     text     | Yes  | NULL | 国家/地区 |
|  language   |   char(32)   |  No  |      |   语言    |
|   length    |  tinyint(3)  |  No  |      |   片长    |
|   imgUrl    |     text     | Yes  | NULL |  海报url  |
|  prevueUrl  |     text     | Yes  | NULL | 预告片url |
| description |     text     | Yes  | NULL | 电影简介  |

### 4. mov_peo表（电影与主演/编剧/导演关系表）

|      字段      |    类型    |  空  | 默认 |                 注释                 |
| :------------: | :--------: | :--: | :--: | :----------------------------------: |
| **mov_peo_id** | bigint(20) |  No  |      |             电影-主演id              |
|     mov_id     | bigint(20) |  No  |      |                电影id                |
|     peo_id     | bigint(20) |  No  |      |                主演id                |
|      flag      | tinyint(1) | Yes  |  0   | 0是未定义，1是演员，2是编剧, 3是导演 |

### 5. people表(用于存放演员/导演/编剧信息)

|    字段     |     类型     |  空  | 默认 |       注释        |
| :---------: | :----------: | :--: | :--: | :---------------: |
| **peo_id**  |  bigint(20)  |  No  |      |                   |
|    name     | varchar(128) |  No  |      |       名字        |
|   gender    |  tinyint(1)  |  No  |      | 性别,0为女，1为男 |
|     job     |   tinytext   | Yes  | NULL |       工作        |
|  birthday   |   datetime   | Yes  | NULL |     出生日期      |
| description |     text     | Yes  | NULL |       简介        |

### 6. cinema表

|    字段     |     类型     |  空  |     默认      |   注释   |
| :---------: | :----------: | :--: | :-----------: | :------: |
| **cin_id**  |  bigint(20)  |  No  |               |  影院id  |
|    name     | varchar(128) |  No  |               |  影院名  |
|   address   |     text     |  No  |               | 影院地址 |
| description |     text     | Yes  |               | 影院介绍 |
|    phone    | varchar(64)  | Yes  |     NULL      | 影院电话 |
|   jobtime   |     text     | Yes  | "09:00-23:30" | 上班时间 |

### 7. video_hell表

|    字段     |     类型     |  空  | 默认 |   注释   |
| :---------: | :----------: | :--: | :--: | :------: |
|  **vh_id**  |  bigint(20)  |  No  |      | 放映厅id |
|   cin_id    |  bigint(20)  |  No  |      |  影院id  |
|    name     | varchar(128) | Yes  | NULL |  影厅名  |
|   number    |   char(32)   |  No  |      | 影厅编号 |
| screen_size |   char(32)   |  No  |      | 屏幕尺寸 |

### 8. video_movie表

|     字段      |       类型       |  空  | 默认 |     注释      |
| :-----------: | :--------------: | :--: | :--: | :-----------: |
| **vh_mov_id** |    bigint(20)    |  No  |      | 放映厅-电影id |
|     vh_id     |    bigint(20)    |  No  |      |   放映厅id    |
|    mov_id     |    bigint(20)    |  No  |      |    电影id     |
|     type      | enum("3D", "2D") | Yes  | "2D" |   影片效果    |
|   starttime   |     datetime     |  No  |      |   播放时间    |
|    endtime    |     datetime     |  No  |      |   结束时间    |
|     price     |    bigint(20)    |  No  |      |     票价      |

### 9. seat表

|    字段     |    类型    |  空  | 默认 |                 注释                 |
| :---------: | :--------: | :--: | :--: | :----------------------------------: |
| **seat_id** | bigint(20) |  No  |      |                座位id                |
|    vh_id    | bigint(20) |  No  |      |               放映厅id               |
|   status    |  Boolean   | Yes  |  0   | 座位状态，0-有效，1-待支付，2-已预定 |
|   row_col   |   String   |  No  |      |         表示该座位是几排几座         |
|   user_id   | bigint(20) | Yes  | NULL |       座位预定者（无时为null）       |

### 10. ticket表

|    字段    |    类型    |  空  |       默认        |             注释             |
| :--------: | :--------: | :--: | :---------------: | :--------------------------: |
| **tkt_id** | bigint(20) |  No  |                   |            订票id            |
|  user_id   | bigint(20) |  No  |                   |            用户id            |
| vh_mov_id  | bigint(20) |  No  |                   |    放映厅-电影-播放时间id    |
|  seat_id   | bigint(20) |  No  |                   |            座位id            |
|   status   |  Boolean   | Yes  |         0         | 0——订单未支付，1——订单已支付 |
| create_at  |  datetime  | Yes  | CURRENT_TIMESTAMP |         订单创建时间         |

### 11. cinema_comment表（影院评论表）

|    字段     |    类型    |  空  |       默认        |   注释   |
| :---------: | :--------: | :--: | :---------------: | :------: |
| **com_id**  | bigint(20) |  No  |                   |  评论id  |
|   cin_id    | bigint(20) |  No  |                   |  影院id  |
|   user_id   | bigint(20) |  No  |                   | 评论者id |
| description |    text    |  No  |                   | 评论内容 |
|  create_at  |  datetime  | Yes  | CURRENT_TIMESTAMP | 创建时间 |