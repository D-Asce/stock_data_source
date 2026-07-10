# A股历史，实时数据稳定数据源接口
**提供A股历史数据，实时数据稳定接口｜量化回测专用**

---
## 🚀 接口详细说明
http://120.26.45.202

如需正式使用，可联系我：

- **QQ：2727517694**
- **微信：onestock188/pandastock888**（请备注：数据API）

# PandaStock API 接口文档

> 共 9 个分类，147 个接口

---

## Levle2和大单

### 订阅Level2实时数据通道

- **函数**: `subscribe_ch_l2_data_real`
- **说明**: 订阅全量个股Level2数据通道，从竞价开始实时推送。数据包含竞价金额、成交量涨速、委托总量、撤单量、成交/委托笔数、主力资金流向等高级指标。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `action_amount` | number | 当日竞价成交金额（万元） |
| `pre_action_amount` | number | 昨日竞价成交金额（万元） |
| `l2_vol_rise_speed` | number | 成交量涨速 |
| `l2_total_buy_vol` | number | 买入委托总量 |
| `l2_total_sell_vol` | number | 卖出委托总量 |
| `l2_buy_cancel` | number | 撤销的买入委托总量 |
| `l2_sell_cancel` | number | 撤销的卖出委托总量 |
| `l2_deal_tick_num` | integer | 成交笔数 |
| `l2_order_tick_num` | integer | 委托笔数 |
| `inst_aggressive_buy_amount` | number | 主力主动净买额（万元） |
| `inst_net_amount` | number | 主力净流入金额（万元） |

- **示例数据**:

```json
{ '603135': {'action_amount': 112.1, 'pre_action_amount': 88.44, 'l2_vol_rise_speed': 0.41, 'l2_total_buy_vol': 6889.0, 'l2_total_sell_vol': 16656.0, 'l2_buy_cancel': 76161.0, 'l2_sell_cancel': 55761.0, 'l2_deal_tick_num': 19560, 'l2_order_tick_num': 29793, 'inst_aggressive_buy_amount': 2862.63, 'inst_net_amount': 696.07}}
```

### 获取Level2实时数据

- **函数**: `get_ch_l2_data_cur_real`
- **说明**: 随时获取全量个股Level2高级行情数据，包括竞价金额、成交量涨速、委托/撤单/成交统计、主力资金流向等指标。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `action_amount` | number | 当日竞价成交金额（万元） |
| `pre_action_amount` | number | 昨日竞价成交金额（万元） |
| `l2_vol_rise_speed` | number | 成交量涨速 |
| `l2_total_buy_vol` | number | 买入委托总量 |
| `l2_total_sell_vol` | number | 卖出委托总量 |
| `l2_buy_cancel` | number | 撤销的买入委托总量 |
| `l2_sell_cancel` | number | 撤销的卖出委托总量 |
| `l2_deal_tick_num` | integer | 成交笔数 |
| `l2_order_tick_num` | integer | 委托笔数 |
| `inst_aggressive_buy_amount` | number | 主力主动净买额（万元） |
| `inst_net_amount` | number | 主力净流入金额（万元） |

- **示例数据**:

```json
{ '603135': {'action_amount': 112.1, 'pre_action_amount': 88.44, 'l2_vol_rise_speed': 0.41, 'l2_total_buy_vol': 6889.0, 'l2_total_sell_vol': 16656.0, 'l2_buy_cancel': 76161.0, 'l2_sell_cancel': 55761.0, 'l2_deal_tick_num': 19560, 'l2_order_tick_num': 29793, 'inst_aggressive_buy_amount': 2862.63, 'inst_net_amount': 696.07}}
```

### 订阅大单数据(DDE)通道

- **函数**: `subscribe_ch_ddx_data_real`
- **说明**: 订阅全量个股DDE大单数据通道，交易日9:31左右开始实时推送。包含DDX、DDY、DDZ三大指标及大单/中单/小单/超大单资金流向比例等高级数据。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `ddx` | number | 当日DDX（大单动向） |
| `ddy` | number | 当日DDY（涨跌动因） |
| `ddz` | number | 当日DDZ（大单差分） |
| `ddx_positive_in_five` | number | 5日内DDX为正的天数 |
| `ddx_positive_in_ten` | number | 10日内DDX为正的天数 |
| `ddx_inc_days` | number | DDX连续递增天数 |
| `ddx_positive_continue_days` | number | DDX连续为正的天数 |
| `bbd_amount` | number | 大单净额（万元） |
| `sell_odd` | integer | 卖出单数 |
| `buy_odd` | integer | 买入单数 |
| `odd_ratio` | number | 单数比（卖出单数/买入单数） |
| `big_odd_ratio` | number | 大单单差（大单买入占比 - 大单卖出占比） |
| `big_odd_buy_ratio` | number | 大单买入金额占总成交额比例 |
| `big_odd_sell_ratio` | number | 大单卖出金额占总成交额比例 |
| `medium_odd_ratio` | number | 中单单差（中单买入占比 - 中单卖出占比） |
| `small_odd_ratio` | number | 小单单差（小单买入占比 - 小单卖出占比） |
| `small_odd_buy_ratio` | number | 小单买入金额占总成交额比例 |
| `small_odd_sell_ratio` | number | 小单卖出金额占总成交额比例 |
| `xl_odd_ratio` | number | 超大单单差（超大单买入占比 - 超大单卖出占比） |
| `xl_odd_buy_ratio` | number | 超大单买入金额占总成交额比例 |
| `xl_odd_sell_ratio` | number | 超大单卖出金额占总成交额比例 |

- **示例数据**:

```json
{ '603188': {'ddx': -0.001, 'ddy': -0.031, 'ddz': -0.41, 'ddx_positive_in_five': 3.0, 'ddx
_positive_in_ten': 8.0, 'bbd_amount': -3.12, 'sell_odd': 4268, 'buy_odd': 4394, 'odd_ratio': 0.971, 'big_odd_ratio': -0.1, 'big_odd_buy_ratio': 10.6, 'big_odd_sell_ratio': 10.7, 'medium_odd_ratio': -7.1, 'small_odd_ratio': 7.2, 'small_odd_buy_r
atio': 60.4, 'small_odd_sell_ratio': 53.2, 'ddx_positive_continue_days': 0.0, 'ddx_inc_days': 0.0, 'xl_odd_ratio': 0.0, 'xl_odd_buy_ratio': 0.0, 'xl_odd_sell_ratio': 0.0}}
```

### 获取大单数据(DDE)

- **函数**: `get_ch_ddx_data_cur_real`
- **说明**: 实时获取全量个股DDE大单数据，包含DDX/DDY/DDZ三大核心指标、各类资金（超大单/大单/中单/小单）的买卖比例和净流向。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `ddx` | number | 当日DDX（大单动向） |
| `ddy` | number | 当日DDY（涨跌动因） |
| `ddz` | number | 当日DDZ（大单差分） |
| `ddx_positive_in_five` | number | 5日内DDX为正的天数 |
| `ddx_positive_in_ten` | number | 10日内DDX为正的天数 |
| `ddx_inc_days` | number | DDX连续递增天数 |
| `ddx_positive_continue_days` | number | DDX连续为正的天数 |
| `bbd_amount` | number | 大单净额（万元） |
| `sell_odd` | integer | 卖出单数 |
| `buy_odd` | integer | 买入单数 |
| `odd_ratio` | number | 单数比（卖出单数/买入单数） |
| `big_odd_ratio` | number | 大单单差（大单买入占比 - 大单卖出占比） |
| `big_odd_buy_ratio` | number | 大单买入金额占总成交额比例 |
| `big_odd_sell_ratio` | number | 大单卖出金额占总成交额比例 |
| `medium_odd_ratio` | number | 中单单差（中单买入占比 - 中单卖出占比） |
| `small_odd_ratio` | number | 小单单差（小单买入占比 - 小单卖出占比） |
| `small_odd_buy_ratio` | number | 小单买入金额占总成交额比例 |
| `small_odd_sell_ratio` | number | 小单卖出金额占总成交额比例 |
| `xl_odd_ratio` | number | 超大单单差（超大单买入占比 - 超大单卖出占比） |
| `xl_odd_buy_ratio` | number | 超大单买入金额占总成交额比例 |
| `xl_odd_sell_ratio` | number | 超大单卖出金额占总成交额比例 |

- **示例数据**:

```json
{ '603188': {'ddx': -0.001, 'ddy': -0.031, 'ddz': -0.41, 'ddx_positive_in_five': 3.0, 'ddx
_positive_in_ten': 8.0, 'bbd_amount': -3.12, 'sell_odd': 4268, 'buy_odd': 4394, 'odd_ratio': 0.971, 'big_odd_ratio': -0.1, 'big_odd_buy_ratio': 10.6, 'big_odd_sell_ratio': 10.7, 'medium_odd_ratio': -7.1, 'small_odd_ratio': 7.2, 'small_odd_buy_r
atio': 60.4, 'small_odd_sell_ratio': 53.2, 'ddx_positive_continue_days': 0.0, 'ddx_inc_days': 0.0, 'xl_odd_ratio': 0.0, 'xl_odd_buy_ratio': 0.0, 'xl_odd_sell_ratio': 0.0}}
```

### 获取个股历史大单历史数据

- **函数**: `get_ch_stock_ddx_history`
- **说明**: 获取个股DDE历史数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `ddx` | number | 当天ddx |
| `ddy` | number | 当天ddy |
| `ddz` | number | 当天ddz |
| `ddx_positive_in_five` | number | 5日内 DDX 为正的天数 |
| `ddx_positive_in_ten` | number | 10日内 DDX 为正的天数 |
| `ddx_positive_continue_days` | number | ddx 连续为正的天数 |
| `ddx_inc_days` | number | ddx 连续递增天数 |
| `bbd_amount` | number | 大单净额(万元) |
| `sell_odd` | integer | 卖出单数 |
| `buy_odd` | integer | 买入单数 |
| `odd_ratio` | number | 单数比  卖出单数/买入单数 |
| `xl_odd_ratio` | number | 超大单单差   超大单买入占比 - 超大单卖出占比 |
| `xl_odd_buy_ratio` | number | 超大单买入金额占总成交额比例 |
| `xl_odd_sell_ratio` | number | 超大单卖出金额占总成交额比例 |
| `big_odd_ratio` | number | 大单单差   大单买入占比 - 大单卖出占比 |
| `big_odd_buy_ratio` | number | 大单买入金额占总成交额比例 |
| `big_odd_sell_ratio` | number | 大单卖出金额占总成交额比例 |
| `medium_odd_ratio` | number | 中单单差   中单买入占比 - 中单卖出占比 |
| `small_odd_ratio` | number | 小单单差   小单买入占比 - 小单卖出占比 |
| `small_odd_buy_ratio` | number | 小单买入金额占总成交额比例 |
| `small_odd_sell_ratio` | number | 小单卖出金额占总成交额比例 |

- **示例数据**:

```json
{
  "2026-01-08": {
    "ddx": -0.011,
    "ddy": 0.043,
    "ddz": 8.001,
    "ddx_positive_in_five": 3,
    "ddx_positive_in_ten": 6,
    "bbd_amount": -2537.29,
    "sell_odd": 36475,
    "buy_odd": 30520,
    "odd_ratio": 1.195,
    "xl_odd_ratio": 5.1,
    "xl_odd_buy_ratio": 35,
    "xl_odd_sell_ratio": 29.9,
    "big_odd_ratio": -7.1,
    "big_odd_buy_ratio": 19.9,
    "big_odd_sell_ratio": 27,
    "medium_odd_ratio": 2.8,
    "small_odd_ratio": -0.8,
    "small_odd_buy_ratio": 19.9,
    "small_odd_sell_ratio": 20.7,
    "ddx_positive_continue_days": 0,
    "ddx_inc_days": 0
  }
}
```

### 个股千档数据

- **函数**: `get_ch_stock_thousand_level_order`
- **说明**: 获取指定个股的千档盘口数据，包含每档详细挂单数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码。如:000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `buy` | dict | 买方数据 |
| `sell` | dict | 卖方数据 |
| `buy.total_vol` | number | 买方总挂单量 |
| `buy.total_amt` | number | 买方总挂单金额 |
| `buy.avg_price` | number | 买方平均挂单价格 |
| `buy.levels` | list | 买方各档位详细信息 |
| `buy.levels.level` | number | 档位 |
| `buy.levels.type` | string | 档位名称 |
| `buy.levels.price` | number | 该档位挂单价格 |
| `buy.levels.orders` | number | 该档委托笔数 |
| `buy.levels.details` | number | 每笔详细委托信息 |
| `sell.total_vol` | number | 卖方总挂单量 |
| `sell.total_amt` | number | 卖方总挂单金额 |
| `sell.avg_price` | number | 卖方平均挂单价格 |
| `sell.levels` | list | 卖方各档位详细信息 |
| `sell.levels.level` | number | 档位 |
| `sell.levels.type` | string | 档位名称 |
| `sell.levels.price` | number | 该档位挂单价格 |
| `sell.levels.orders` | number | 该档委托笔数 |
| `sell.levels.details` | list | 每笔详细委托信息 |

- **示例数据**:

```json
{
  "buy": {
    "total_vol": 225976.69,
    "total_amt": 248743993.9,
    "avg_price": 11.01,
    "levels": [
      {
        "level": 1,
        "type": "买1",
        "price": 11.23,
        "volume": 6023,
        "orders": 20,
        "details": [
          5000,
          31,
          10,
          2,
          7,
          418,
          40,
          8,
          10,
          10,
          11,
          50,
          20,
          2,
          5,
          220,
          4,
          11,
          19,
          145
        ]
      },
      {
        "level": 2,
        "type": "买2",
        "price": 11.22,
        "volume": 841,
        "orders": 10,
        "details": [
          10,
          8,
          3,
          3,
          21,
          17,
          37,
          149,
          77,
          339
        ]
      },
      {
        "level": 3,
        "type": "买3",
        "price": 11.21,
        "volume": 1171,
        "orders": 29,
        "details": [
          21,
          12,
          16,
          10,
          14,
          11,
          43,
          443,
          1,
          42,
          2,
          12,
          1,
          24,
          8,
          18,
          6,
          24,
          7,
          34,
          45,
          26,
          3,
          7,
          1,
          1,
          29,
          1,
          8
        ]
      },
      {
        "level": 4,
        "type": "买4",
        "price": 11.2,
        "volume": 1994,
        "orders": 45,
        "details": [
          3,
          10,
          2,
          2,
          5,
          1,
          7,
          17,
          52,
          3,
          2,
          6,
          7,
          2,
          19,
          7,
          5,
          12,
          27,
          5,
          28,
          7,
          7,
          1,
          3,
          13,
          7,
          1,
          3,
          2,
          1,
          1,
          2,
          77,
          1,
          50,
          1,
          1,
          1,
          1,
          1,
          1,
          98,
          26,
          2
        ]
      },
      {
        "level": 5,
        "type": "买5",
        "price": 11.19,
        "volume": 465,
        "orders": 22,
        "details": [
          2,
          11,
          2,
          50,
          3,
          49,
          13,
          9,
          50,
          4,
          2,
          270
        ]
      },
      {
        "level": 6,
        "type": "买6",
        "price": 11.18,
        "volume": 1188,
        "orders": 34,
        "details": [
          1,
          2,
          4,
          10,
          5,
          1,
          17,
          2,
          5,
          1,
          1,
          1,
          1,
          26,
          3,
          2,
          7,
          3,
          5,
          3,
          1,
          3,
          3,
          5,
          9,
          4,
          6,
          9,
          6,
          19,
          6,
          18,
          5,
          5
        ]
      },
      {
        "level": 7,
        "type": "买7",
        "price": 11.17,
        "volume": 1798,
        "orders": 24,
        "details": [
          5,
          5,
          12,
          1,
          1,
          28,
          2,
          1,
          3,
          9,
          4,
          4,
          7,
          20,
          13,
          28,
          27,
          10,
          12,
          22,
          74,
          11,
          41,
          2
        ]
      },
      {
        "level": 8,
        "type": "买8",
        "price": 11.16,
        "volume": 2090,
        "orders": 21,
        "details": [
          14,
          42,
          341,
          7,
          20,
          19,
          12,
          25,
          45,
          82,
          9,
          4,
          9,
          59,
          48,
          44,
          6,
          22,
          47,
          52,
          8
        ]
      },
      {
        "level": 9,
        "type": "买9",
        "price": 11.15,
        "volume": 623,
        "orders": 34,
        "details": [
          7,
          3,
          1,
          1,
          1,
          8,
          19,
          1,
          2,
          1,
          5,
          9,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          9,
          13,
          1,
          1,
          15,
          1,
          7,
          2,
          1,
          1,
          14,
          4,
          1,
          33,
          29
        ]
      },
      {
        "level": 10,
        "type": "买10",
        "price": 11.14,
        "volume": 1378,
        "orders": 18,
        "details": [
          274,
          1000,
          39,
          21,
          20,
          1,
          3,
          20
        ]
      },
      {
        "level": 11,
        "type": "买11",
        "price": 11.13,
        "volume": 507,
        "orders": 23,
        "details": [
          3,
          1,
          11,
          3,
          21,
          2,
          5,
          25,
          10,
          20,
          50,
          10,
          10,
          5,
          3,
          5,
          100,
          10,
          20,
          20,
          13,
          1,
          159
        ]
      },
      {
        "level": 12,
        "type": "买12",
        "price": 11.12,
        "volume": 21040,
        "orders": 1042,
        "details": [
          128,
          9,
          19,
          150,
          96,
          2,
          3,
          1,
          3,
          1,
          2,
          1,
          3,
          1,
          2,
          1,
          2,
          409,
          1,
          1,
          30,
          14,
          39,
          15,
          87,
          10,
          46,
          41,
          23,
          14,
          1,
          1,
          1,
          2,
          2,
          1,
          18,
          3,
          2,
          2,
          1,
          1,
          1,
          1,
          3,
          2,
          1,
          1,
          1,
          2
        ]
      },
      {
        "level": 13,
        "type": "买13",
        "price": 11.11,
        "volume": 8201,
        "orders": 226,
        "details": [
          9,
          7,
          4,
          6,
          100,
          12,
          22,
          21,
          2,
          25,
          5,
          19,
          23,
          56,
          21,
          4,
          47,
          14,
          14,
          10,
          8,
          21,
          17,
          9,
          27,
          65,
          21,
          20,
          13,
          13,
          11,
          10,
          12,
          17,
          20,
          22,
          15,
          48,
          50,
          32,
          57,
          54,
          28,
          2,
          1,
          1,
          2,
          1,
          1,
          13
        ]
      },
      {
        "level": 14,
        "type": "买14",
        "price": 11.1,
        "volume": 17211,
        "orders": 163,
        "details": [
          280,
          1,
          9990,
          99,
          150,
          157,
          1,
          1,
          43,
          84,
          52,
          46,
          32,
          26,
          55,
          32,
          41,
          117,
          135,
          48,
          34,
          51,
          67,
          16,
          4,
          7,
          75,
          13.03,
          10.03,
          131.03,
          155.03,
          16.03,
          30.03,
          59.03,
          86.03,
          19.83,
          30.83,
          19.83,
          1,
          19,
          5,
          20,
          65,
          52,
          1,
          9,
          27,
          6,
          13,
          16
        ]
      },
      {
        "level": 15,
        "type": "买15",
        "price": 11.09,
        "volume": 7145,
        "orders": 356,
        "details": [
          1,
          5,
          1,
          1,
          1,
          1,
          1,
          2,
          61,
          1,
          10,
          1,
          3,
          4,
          1,
          12,
          10,
          4,
          20,
          8,
          6,
          30,
          6,
          17,
          6,
          8,
          16,
          21,
          14,
          20,
          24,
          6,
          16,
          5,
          44,
          11,
          11,
          10,
          5,
          7,
          2,
          13,
          3,
          6,
          14,
          34,
          8,
          14,
          25,
          11
        ]
      },
      {
        "level": 16,
        "type": "买16",
        "price": 11.08,
        "volume": 5141,
        "orders": 171,
        "details": [
          2,
          1,
          26,
          9,
          14.4,
          7.4,
          4,
          21,
          20,
          42,
          25,
          2,
          2,
          3,
          1,
          2,
          1,
          1,
          1,
          1,
          1,
          1,
          43,
          2,
          39,
          1,
          1,
          2,
          49,
          1,
          1,
          271,
          1,
          3,
          1,
          2,
          3,
          3,
          1,
          1,
          1,
          1,
          1,
          1,
          9,
          28,
          1,
          10,
          1,
          1
        ]
      },
      {
        "level": 17,
        "type": "买17",
        "price": 11.07,
        "volume": 16186,
        "orders": 516,
        "details": [
          6,
          1,
          49,
          2,
          1,
          1,
          1,
          1,
          1,
          1,
          2,
          1,
          1,
          44,
          2,
          14.71,
          101,
          11,
          43,
          51,
          48,
          15,
          11,
          9,
          65,
          20,
          22,
          10,
          17,
          2,
          14,
          57,
          1,
          43,
          4,
          4,
          1,
          7,
          1,
          4,
          1,
          3,
          1,
          1,
          2,
          1,
          2,
          5,
          2,
          2
        ]
      },
      {
        "level": 18,
        "type": "买18",
        "price": 11.06,
        "volume": 36085,
        "orders": 578,
        "details": [
          2,
          2,
          7,
          13,
          18,
          186,
          9,
          1,
          1,
          10,
          7,
          5,
          19,
          56,
          158,
          2,
          1,
          1,
          10,
          5,
          3,
          2,
          2,
          1,
          1,
          1,
          3,
          1,
          5,
          1,
          5,
          3,
          3,
          1,
          1,
          2,
          3,
          1,
          3,
          2,
          1,
          5,
          3,
          5,
          3,
          1,
          3,
          4,
          1,
          1
        ]
      },
      {
        "level": 19,
        "type": "买19",
        "price": 11.05,
        "volume": 7222,
        "orders": 230,
        "details": [
          3,
          9,
          5,
          7,
          5,
          5,
          13,
          2,
          7,
          5,
          25,
          25,
          2,
          16,
          3,
          1,
          2,
          12,
          1,
          1,
          1,
          12,
          300,
          4,
          57,
          4,
          2,
          1,
          2,
          71,
          75,
          96,
          32,
          29,
          25,
          90,
          4,
          11,
          1,
          1,
          81,
          10,
          4,
          2,
          1,
          1,
          2,
          6,
          2,
          3
        ]
      },
      {
        "level": 20,
        "type": "买20",
        "price": 11.04,
        "volume": 3395,
        "orders": 247,
        "details": [
          2,
          5,
          2,
          3,
          2,
          8,
          1,
          1,
          2,
          1,
          1,
          2,
          3,
          3,
          2,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          3,
          1,
          2,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          2,
          1,
          1,
          3,
          2,
          1,
          2,
          2,
          1,
          1,
          9,
          1,
          1,
          1,
          2,
          1,
          3,
          2
        ]
      },
      {
        "level": 21,
        "type": "买21",
        "price": 11.03,
        "volume": 13900,
        "orders": 135,
        "details": [
          1,
          1,
          3,
          3000,
          2950,
          921,
          70,
          62,
          54,
          72,
          64,
          12,
          3,
          55,
          25,
          28,
          21,
          10,
          27,
          34,
          13,
          34,
          28,
          17,
          97,
          19,
          108,
          41,
          32,
          18,
          28,
          8,
          6,
          2,
          1,
          1,
          3,
          2,
          1,
          38,
          2,
          2,
          1,
          2,
          13,
          2,
          2,
          1,
          1,
          1
        ]
      },
      {
        "level": 22,
        "type": "买22",
        "price": 11.02,
        "volume": 1247,
        "orders": 88,
        "details": [
          1,
          6,
          2,
          7,
          46,
          33,
          7,
          8,
          36,
          1,
          6,
          43,
          18,
          4,
          2,
          2,
          2,
          1,
          4,
          1,
          5,
          2,
          2,
          3,
          3,
          1,
          3,
          3,
          1,
          1,
          1,
          1,
          1,
          1,
          4,
          5,
          10,
          141,
          2,
          2,
          2,
          26,
          8,
          2,
          1,
          1,
          3,
          1,
          10,
          3
        ]
      },
      {
        "level": 23,
        "type": "买23",
        "price": 11.01,
        "volume": 14588,
        "orders": 234,
        "details": [
          21,
          1,
          1,
          2,
          27,
          58,
          1,
          4,
          4,
          4,
          5,
          1,
          5,
          3,
          5,
          2,
          1,
          13,
          2,
          52,
          2,
          19,
          11,
          16,
          3,
          2,
          4,
          2,
          3,
          3,
          3,
          1,
          1,
          1,
          2,
          19,
          3,
          1,
          2,
          4,
          2,
          4,
          2,
          2,
          2,
          588,
          3,
          3000,
          59,
          140
        ]
      },
      {
        "level": 24,
        "type": "买24",
        "price": 11,
        "volume": 8344,
        "orders": 499,
        "details": [
          1,
          7,
          1,
          1,
          2,
          1,
          1,
          1,
          3,
          3,
          1,
          2,
          1,
          1,
          1,
          66,
          1,
          1,
          1,
          3,
          1,
          2,
          1,
          1,
          2,
          2,
          1,
          1,
          1,
          2,
          1,
          1,
          3,
          1,
          2,
          1,
          1,
          1,
          1,
          4,
          1,
          2,
          3,
          1,
          2,
          1,
          6,
          2,
          1,
          2
        ]
      },
      {
        "level": 25,
        "type": "买25",
        "price": 10.99,
        "volume": 3677,
        "orders": 258,
        "details": [
          8,
          102,
          169,
          6,
          185,
          88,
          9,
          12,
          70,
          7,
          17,
          2,
          10,
          1,
          8,
          6,
          168,
          1,
          24,
          1,
          5,
          8,
          39,
          20,
          4,
          8,
          7,
          5,
          11,
          22,
          7,
          2,
          7,
          1,
          2,
          2,
          6,
          3,
          3,
          1,
          1,
          3,
          20,
          8,
          4,
          1,
          3,
          1,
          1,
          1
        ]
      },
      {
        "level": 26,
        "type": "买26",
        "price": 10.98,
        "volume": 3879,
        "orders": 138,
        "details": [
          8,
          3,
          1,
          67,
          1,
          4,
          29,
          1,
          85,
          23,
          9,
          82,
          5,
          75,
          88,
          1,
          26,
          4,
          1,
          3,
          9,
          2,
          9,
          3,
          50,
          10,
          5,
          7,
          4,
          2,
          1,
          2,
          110,
          7,
          5,
          7,
          5,
          8,
          2,
          12,
          10,
          630,
          2,
          2,
          15,
          1,
          6,
          16,
          20,
          1
        ]
      },
      {
        "level": 27,
        "type": "买27",
        "price": 10.97,
        "volume": 2599,
        "orders": 45,
        "details": [
          3,
          154,
          9,
          16,
          2,
          8,
          36,
          2,
          11,
          6,
          7,
          7,
          10,
          8,
          5,
          7,
          1,
          630,
          2,
          1,
          1,
          1,
          20,
          2,
          10,
          7,
          550,
          10,
          2,
          3,
          5,
          1,
          9,
          7,
          30,
          1,
          46,
          33,
          5,
          896,
          10,
          9,
          5,
          1,
          10
        ]
      },
      {
        "level": 28,
        "type": "买28",
        "price": 10.96,
        "volume": 674,
        "orders": 48,
        "details": [
          36,
          36,
          1,
          3,
          1,
          1,
          1,
          12,
          2,
          164,
          5,
          8,
          1,
          1,
          10,
          28,
          3,
          7,
          2,
          5,
          5,
          45,
          33,
          20,
          3,
          19,
          5,
          10,
          16,
          7,
          4,
          9,
          1,
          16,
          8,
          20,
          12,
          22,
          10,
          5,
          10,
          5,
          30,
          1,
          20,
          1,
          5,
          5
        ]
      },
      {
        "level": 29,
        "type": "买29",
        "price": 10.95,
        "volume": 1935,
        "orders": 102,
        "details": [
          56,
          4,
          17,
          1,
          23,
          10,
          10,
          4,
          9,
          20,
          5,
          37,
          20,
          1,
          49,
          3,
          7,
          4,
          8,
          5,
          1,
          9,
          21,
          26,
          100,
          2,
          12,
          5,
          2,
          9,
          30,
          17,
          6,
          2,
          3,
          16,
          200,
          31,
          48,
          17,
          3,
          15,
          12,
          1,
          112,
          32,
          78,
          52,
          14,
          25
        ]
      },
      {
        "level": 30,
        "type": "买30",
        "price": 10.94,
        "volume": 981,
        "orders": 40,
        "details": [
          227,
          1,
          1,
          35,
          6,
          56,
          25,
          57,
          6,
          3,
          2,
          21,
          22,
          5,
          1,
          5,
          5,
          30,
          10,
          20,
          16,
          7,
          1,
          13,
          5,
          10,
          1,
          20,
          6,
          200,
          5,
          1,
          5,
          1,
          1,
          16,
          99,
          10,
          2,
          24
        ]
      },
      {
        "level": 31,
        "type": "买31",
        "price": 10.93,
        "volume": 1263,
        "orders": 42,
        "details": [
          20,
          49,
          8,
          27,
          50,
          1,
          14,
          1,
          1,
          1,
          1,
          58,
          2,
          18,
          22,
          11,
          6,
          9,
          13,
          16,
          4,
          15,
          3,
          2,
          9,
          2,
          1,
          6,
          1,
          2,
          5,
          20,
          1,
          50,
          6,
          1,
          1,
          3,
          2,
          1,
          795,
          5
        ]
      },
      {
        "level": 32,
        "type": "买32",
        "price": 10.92,
        "volume": 796,
        "orders": 44,
        "details": [
          10,
          23,
          67,
          16,
          1,
          1,
          11,
          1,
          7,
          4,
          70,
          10,
          50,
          1,
          10,
          10,
          132,
          3,
          10,
          10,
          25,
          20,
          5,
          30,
          5,
          8,
          5,
          10,
          12,
          40,
          20,
          2,
          5,
          5,
          10,
          4,
          10,
          5,
          5,
          10,
          10,
          31,
          70,
          2
        ]
      },
      {
        "level": 33,
        "type": "买33",
        "price": 10.91,
        "volume": 3326,
        "orders": 91,
        "details": [
          3,
          18,
          62,
          112,
          29,
          22,
          53,
          2,
          1,
          5,
          1,
          5,
          1,
          2,
          2,
          1,
          1,
          12,
          5,
          30,
          6,
          3,
          10,
          11,
          1,
          1,
          12,
          5,
          640,
          2,
          1,
          29,
          2,
          4,
          8,
          15,
          50,
          58,
          2,
          23,
          3,
          170,
          177,
          10,
          6,
          41,
          877,
          20,
          10,
          3
        ]
      },
      {
        "level": 34,
        "type": "买34",
        "price": 10.9,
        "volume": 5187,
        "orders": 205,
        "details": [
          10,
          4,
          16,
          1,
          6,
          8,
          6,
          2,
          3,
          10,
          10,
          17,
          23,
          1,
          20,
          1,
          5,
          10,
          2,
          2,
          3,
          10,
          30,
          2,
          16,
          6,
          3,
          95,
          1,
          3,
          3,
          10,
          2,
          6,
          10,
          7,
          5,
          10,
          3,
          4,
          5,
          1,
          26,
          5,
          82,
          1,
          1,
          63,
          10,
          80
        ]
      },
      {
        "level": 35,
        "type": "买35",
        "price": 10.89,
        "volume": 1557,
        "orders": 59,
        "details": [
          9,
          32,
          68,
          79,
          54,
          139,
          20,
          3,
          7,
          94,
          10,
          100,
          10,
          47,
          93,
          26,
          10,
          10,
          10,
          10,
          88,
          12,
          21,
          50,
          9,
          30,
          5,
          28,
          10,
          7,
          25,
          2,
          8,
          30,
          20,
          5,
          10,
          20,
          10,
          50,
          1,
          1,
          6,
          1,
          2,
          82,
          3,
          24,
          3,
          10
        ]
      },
      {
        "level": 36,
        "type": "买36",
        "price": 10.88,
        "volume": 4969,
        "orders": 178,
        "details": [
          13,
          2,
          10,
          10,
          10,
          2,
          1,
          11,
          5,
          10,
          10,
          10,
          5,
          8,
          62,
          200,
          10,
          1,
          4,
          10,
          13,
          46,
          275,
          164,
          45,
          500,
          13,
          284,
          91,
          205,
          30,
          5,
          19,
          4,
          2,
          2,
          3,
          13,
          31,
          1,
          6,
          1,
          1,
          1,
          9,
          10,
          1,
          27,
          10,
          4
        ]
      },
      {
        "level": 37,
        "type": "买37",
        "price": 10.87,
        "volume": 801,
        "orders": 14,
        "details": [
          3,
          4,
          50,
          3,
          1,
          3,
          30,
          50,
          8,
          500,
          3,
          20,
          70,
          56
        ]
      },
      {
        "level": 38,
        "type": "买38",
        "price": 10.86,
        "volume": 601,
        "orders": 25,
        "details": [
          20,
          8,
          1,
          10,
          2,
          3,
          10,
          13,
          100,
          3,
          40,
          5,
          1,
          10,
          1,
          5,
          200,
          40,
          5,
          10,
          1,
          81,
          1,
          20,
          11
        ]
      },
      {
        "level": 39,
        "type": "买39",
        "price": 10.85,
        "volume": 683,
        "orders": 35,
        "details": [
          1,
          5,
          10,
          9,
          3,
          10,
          10,
          10,
          2,
          22,
          10,
          6,
          1,
          10,
          2,
          358,
          10,
          6,
          4,
          8,
          9,
          3,
          23,
          4,
          10,
          3,
          1,
          20,
          10,
          20,
          5,
          31,
          4,
          3,
          40
        ]
      },
      {
        "level": 40,
        "type": "买40",
        "price": 10.84,
        "volume": 449,
        "orders": 13,
        "details": [
          200,
          1,
          2,
          10,
          2,
          5,
          210,
          2,
          3,
          5,
          5,
          2,
          2
        ]
      },
      {
        "level": 41,
        "type": "买41",
        "price": 10.83,
        "volume": 593,
        "orders": 12,
        "details": [
          260,
          10,
          100,
          60,
          1,
          10,
          70,
          10,
          20,
          7,
          3,
          42
        ]
      },
      {
        "level": 42,
        "type": "买42",
        "price": 10.82,
        "volume": 314,
        "orders": 10,
        "details": [
          10,
          1,
          1,
          20,
          90,
          2,
          100,
          20,
          20,
          50
        ]
      },
      {
        "level": 43,
        "type": "买43",
        "price": 10.81,
        "volume": 184,
        "orders": 14,
        "details": [
          3,
          1,
          2,
          6,
          1,
          10,
          50,
          3,
          4,
          30,
          30,
          40,
          3,
          1
        ]
      },
      {
        "level": 44,
        "type": "买44",
        "price": 10.8,
        "volume": 1640,
        "orders": 54,
        "details": [
          30,
          2,
          50,
          5,
          100,
          1,
          3,
          10,
          2,
          5,
          3,
          200,
          5,
          10,
          6,
          2,
          3,
          2,
          1,
          5,
          3,
          27,
          100,
          11,
          5,
          300,
          5,
          20,
          10,
          50,
          10,
          10,
          5,
          10,
          9,
          20,
          100,
          10,
          30,
          3,
          30,
          1,
          20,
          4,
          2,
          6,
          5,
          98,
          50,
          94
        ]
      },
      {
        "level": 45,
        "type": "买45",
        "price": 10.79,
        "volume": 310,
        "orders": 4,
        "details": [
          20,
          200,
          80,
          10
        ]
      },
      {
        "level": 46,
        "type": "买46",
        "price": 10.78,
        "volume": 122,
        "orders": 11,
        "details": [
          5,
          5,
          10,
          1,
          10,
          10,
          10,
          2,
          50,
          9,
          10
        ]
      },
      {
        "level": 47,
        "type": "买47",
        "price": 10.77,
        "volume": 11,
        "orders": 2,
        "details": [
          10,
          1
        ]
      },
      {
        "level": 48,
        "type": "买48",
        "price": 10.76,
        "volume": 26,
        "orders": 4,
        "details": [
          1,
          3,
          1,
          21
        ]
      },
      {
        "level": 49,
        "type": "买49",
        "price": 10.75,
        "volume": 610,
        "orders": 10,
        "details": [
          3,
          50,
          10,
          2,
          6,
          326,
          100,
          50,
          3,
          60
        ]
      },
      {
        "level": 50,
        "type": "买50",
        "price": 10.74,
        "volume": 24,
        "orders": 2,
        "details": [
          4,
          20
        ]
      },
      {
        "level": 51,
        "type": "买51",
        "price": 10.73,
        "volume": 28,
        "orders": 4,
        "details": [
          1,
          20,
          2,
          5
        ]
      },
      {
        "level": 52,
        "type": "买52",
        "price": 10.72,
        "volume": 100,
        "orders": 7,
        "details": [
          6,
          5,
          2,
          18,
          9,
          50,
          10
        ]
      },
      {
        "level": 53,
        "type": "买53",
        "price": 10.71,
        "volume": 127,
        "orders": 5,
        "details": [
          100,
          4,
          1,
          10,
          12
        ]
      },
      {
        "level": 54,
        "type": "买54",
        "price": 10.7,
        "volume": 333,
        "orders": 13,
        "details": [
          6,
          50,
          8,
          50,
          50,
          50,
          10,
          30,
          1,
          1,
          30,
          17,
          30
        ]
      },
      {
        "level": 55,
        "type": "买55",
        "price": 10.69,
        "volume": 10,
        "orders": 1,
        "details": [
          10
        ]
      },
      {
        "level": 56,
        "type": "买56",
        "price": 10.68,
        "volume": 108,
        "orders": 5,
        "details": [
          10,
          18,
          5,
          20,
          55
        ]
      },
      {
        "level": 57,
        "type": "买57",
        "price": 10.67,
        "volume": 28,
        "orders": 5,
        "details": [
          6,
          10,
          1,
          10,
          1
        ]
      },
      {
        "level": 58,
        "type": "买58",
        "price": 10.66,
        "volume": 123,
        "orders": 7,
        "details": [
          5,
          10,
          5,
          2,
          5,
          90,
          6
        ]
      },
      {
        "level": 59,
        "type": "买59",
        "price": 10.65,
        "volume": 60,
        "orders": 7,
        "details": [
          30,
          7,
          10,
          2,
          5,
          5,
          1
        ]
      },
      {
        "level": 60,
        "type": "买60",
        "price": 10.63,
        "volume": 34,
        "orders": 4,
        "details": [
          10,
          6,
          3,
          15
        ]
      },
      {
        "level": 61,
        "type": "买61",
        "price": 10.62,
        "volume": 30,
        "orders": 4,
        "details": [
          7,
          1,
          2,
          20
        ]
      },
      {
        "level": 62,
        "type": "买62",
        "price": 10.61,
        "volume": 132,
        "orders": 7,
        "details": [
          4,
          4,
          21,
          100,
          1,
          1,
          1
        ]
      },
      {
        "level": 63,
        "type": "买63",
        "price": 10.6,
        "volume": 141,
        "orders": 10,
        "details": [
          13,
          10,
          10,
          20,
          5,
          1,
          30,
          50,
          1,
          1
        ]
      },
      {
        "level": 64,
        "type": "买64",
        "price": 10.59,
        "volume": 1,
        "orders": 1,
        "details": [
          1
        ]
      },
      {
        "level": 65,
        "type": "买65",
        "price": 10.58,
        "volume": 176,
        "orders": 4,
        "details": [
          5,
          100,
          1,
          70
        ]
      },
      {
        "level": 66,
        "type": "买66",
        "price": 10.57,
        "volume": 2,
        "orders": 2,
        "details": [
          1,
          1
        ]
      },
      {
        "level": 67,
        "type": "买67",
        "price": 10.56,
        "volume": 8,
        "orders": 3,
        "details": [
          2,
          1,
          5
        ]
      },
      {
        "level": 68,
        "type": "买68",
        "price": 10.55,
        "volume": 3,
        "orders": 3,
        "details": [
          1,
          1,
          1
        ]
      },
      {
        "level": 69,
        "type": "买69",
        "price": 10.54,
        "volume": 3,
        "orders": 3,
        "details": [
          1,
          1,
          1
        ]
      },
      {
        "level": 70,
        "type": "买70",
        "price": 10.52,
        "volume": 1,
        "orders": 1,
        "details": [
          1
        ]
      },
      {
        "level": 71,
        "type": "买71",
        "price": 10.51,
        "volume": 52,
        "orders": 3,
        "details": [
          21,
          1,
          30
        ]
      },
      {
        "level": 72,
        "type": "买72",
        "price": 10.5,
        "volume": 125,
        "orders": 13,
        "details": [
          2,
          5,
          5,
          3,
          2,
          5,
          10,
          50,
          10,
          3,
          20,
          5,
          5
        ]
      },
      {
        "level": 73,
        "type": "买73",
        "price": 10.48,
        "volume": 32,
        "orders": 3,
        "details": [
          1,
          1,
          30
        ]
      },
      {
        "level": 74,
        "type": "买74",
        "price": 10.46,
        "volume": 2,
        "orders": 2,
        "details": [
          1,
          1
        ]
      },
      {
        "level": 75,
        "type": "买75",
        "price": 10.45,
        "volume": 11,
        "orders": 5,
        "details": [
          1,
          6,
          2,
          1,
          1
        ]
      },
      {
        "level": 76,
        "type": "买76",
        "price": 10.44,
        "volume": 57,
        "orders": 3,
        "details": [
          50,
          1,
          6
        ]
      },
      {
        "level": 77,
        "type": "买77",
        "price": 10.43,
        "volume": 1,
        "orders": 1,
        "details": [
          1
        ]
      },
      {
        "level": 78,
        "type": "买78",
        "price": 10.41,
        "volume": 1,
        "orders": 1,
        "details": [
          1
        ]
      },
      {
        "level": 79,
        "type": "买79",
        "price": 10.4,
        "volume": 37,
        "orders": 3,
        "details": [
          7,
          10,
          20
        ]
      },
      {
        "level": 80,
        "type": "买80",
        "price": 10.39,
        "volume": 1,
        "orders": 1,
        "details": [
          1
        ]
      },
      {
        "level": 81,
        "type": "买81",
        "price": 10.38,
        "volume": 50,
        "orders": 1,
        "details": [
          50
        ]
      },
      {
        "level": 82,
        "type": "买82",
        "price": 10.37,
        "volume": 1,
        "orders": 1,
        "details": [
          1
        ]
      },
      {
        "level": 83,
        "type": "买83",
        "price": 10.36,
        "volume": 22,
        "orders": 3,
        "details": [
          20,
          1,
          1
        ]
      },
      {
        "level": 84,
        "type": "买84",
        "price": 10.35,
        "volume": 3,
        "orders": 3,
        "details": [
          1,
          1,
          1
        ]
      },
      {
        "level": 85,
        "type": "买85",
        "price": 10.34,
        "volume": 11,
        "orders": 1,
        "details": [
          11
        ]
      },
      {
        "level": 86,
        "type": "买86",
        "price": 10.3,
        "volume": 740,
        "orders": 2,
        "details": [
          739,
          1
        ]
      },
      {
        "level": 87,
        "type": "买87",
        "price": 10.29,
        "volume": 6,
        "orders": 1,
        "details": [
          6
        ]
      },
      {
        "level": 88,
        "type": "买88",
        "price": 10.28,
        "volume": 1,
        "orders": 1,
        "details": [
          1
        ]
      },
      {
        "level": 89,
        "type": "买89",
        "price": 10.25,
        "volume": 3,
        "orders": 1,
        "details": [
          3
        ]
      },
      {
        "level": 90,
        "type": "买90",
        "price": 10.24,
        "volume": 1,
        "orders": 1,
        "details": [
          1
        ]
      },
      {
        "level": 91,
        "type": "买91",
        "price": 10.22,
        "volume": 14,
        "orders": 14,
        "details": [
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1
        ]
      },
      {
        "level": 92,
        "type": "买92",
        "price": 10.2,
        "volume": 7,
        "orders": 3,
        "details": [
          1,
          5,
          1
        ]
      },
      {
        "level": 93,
        "type": "买93",
        "price": 10.19,
        "volume": 112,
        "orders": 112,
        "details": [
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1
        ]
      },
      {
        "level": 94,
        "type": "买94",
        "price": 10.17,
        "volume": 11,
        "orders": 2,
        "details": [
          1,
          10
        ]
      },
      {
        "level": 95,
        "type": "买95",
        "price": 10.16,
        "volume": 4100,
        "orders": 1,
        "details": [
          4100
        ]
      },
      {
        "level": 96,
        "type": "买96",
        "price": 10.13,
        "volume": 30,
        "orders": 2,
        "details": [
          10,
          20
        ]
      },
      {
        "level": 97,
        "type": "买97",
        "price": 10.1,
        "volume": 9,
        "orders": 5,
        "details": [
          5,
          1,
          1,
          1,
          1
        ]
      },
      {
        "level": 98,
        "type": "买98",
        "price": 10.08,
        "volume": 10,
        "orders": 1,
        "details": [
          10
        ]
      },
      {
        "level": 99,
        "type": "买99",
        "price": 10.05,
        "volume": 30,
        "orders": 2,
        "details": [
          20,
          10
        ]
      },
      {
        "level": 100,
        "type": "买100",
        "price": 10.02,
        "volume": 3,
        "orders": 1,
        "details": [
          3
        ]
      },
      {
        "level": 101,
        "type": "买101",
        "price": 10.01,
        "volume": 4,
        "orders": 1,
        "details": [
          4
        ]
      },
      {
        "level": 102,
        "type": "买102",
        "price": 10,
        "volume": 902,
        "orders": 17,
        "details": [
          3,
          3,
          6,
          5,
          5,
          20,
          1,
          1,
          2,
          10,
          301,
          10,
          3,
          13,
          500,
          1,
          18
        ]
      },
      {
        "level": 103,
        "type": "买103",
        "price": 9.99,
        "volume": 1500,
        "orders": 1,
        "details": [
          1500
        ]
      },
      {
        "level": 104,
        "type": "买104",
        "price": 9.98,
        "volume": 220,
        "orders": 4,
        "details": [
          2,
          140,
          20,
          58
        ]
      },
      {
        "level": 105,
        "type": "买105",
        "price": 9.9,
        "volume": 254,
        "orders": 4,
        "details": [
          2,
          1,
          1,
          250
        ]
      },
      {
        "level": 106,
        "type": "买106",
        "price": 9.89,
        "volume": 47,
        "orders": 10,
        "details": [
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          38,
          1,
          1
        ]
      },
      {
        "level": 107,
        "type": "买107",
        "price": 9.88,
        "volume": 47,
        "orders": 4,
        "details": [
          39,
          1,
          1,
          6
        ]
      },
      {
        "level": 108,
        "type": "买108",
        "price": 9.87,
        "volume": 1,
        "orders": 1,
        "details": [
          1
        ]
      },
      {
        "level": 109,
        "type": "买109",
        "price": 9.86,
        "volume": 284,
        "orders": 5,
        "details": [
          280,
          1,
          1,
          1,
          1
        ]
      },
      {
        "level": 110,
        "type": "买110",
        "price": 9.85,
        "volume": 791,
        "orders": 72,
        "details": [
          1,
          1,
          1,
          1,
          1,
          2,
          1,
          4,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          10,
          1,
          1,
          500,
          1,
          1,
          10,
          5,
          1,
          3,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          1,
          6,
          6,
          6,
          6,
          6,
          6,
          4,
          3,
          3,
          3,
          3
        ]
      }
    ]
  },
  "sell": {
    "total_vol": 157435.95,
    "total_amt": 180154148.12,
    "avg_price": 11.44,
    "levels": [
      {
        "level": 1,
        "type": "卖1",
        "price": 11.24,
        "volume": 8208,
        "orders": 247,
        "details": [
          2859.2,
          10,
          10,
          30,
          10,
          10,
          2,
          100,
          5,
          2,
          5,
          10,
          500,
          27,
          4,
          40,
          6,
          1,
          3,
          30,
          2,
          19,
          5,
          6,
          2,
          10,
          5,
          3,
          7,
          1,
          1,
          20,
          100,
          5,
          20,
          20,
          10,
          1,
          3,
          45,
          20,
          4,
          16,
          10,
          200,
          20,
          50,
          21,
          53,
          10
        ]
      },
      {
        "level": 2,
        "type": "卖2",
        "price": 11.25,
        "volume": 36911,
        "orders": 1101,
        "details": [
          5,
          2,
          50,
          1,
          5,
          20,
          10,
          12,
          40,
          6,
          5,
          47,
          2,
          10,
          20,
          1,
          5,
          5,
          50,
          8,
          45,
          1,
          40,
          2,
          3,
          100,
          10,
          5,
          1,
          5,
          50,
          130,
          1,
          20,
          1,
          10,
          10,
          3,
          3,
          47,
          20,
          9,
          70,
          5,
          30,
          3,
          10,
          10,
          10,
          11
        ]
      },
      {
        "level": 3,
        "type": "卖3",
        "price": 11.26,
        "volume": 11304,
        "orders": 414,
        "details": [
          5,
          28,
          1,
          2,
          5,
          8,
          1,
          50,
          7,
          12,
          3,
          5,
          100,
          3,
          2,
          50,
          14,
          50,
          40,
          5,
          9,
          24,
          30,
          6,
          70,
          10,
          20,
          32,
          133
        ]
      },
      {
        "level": 4,
        "type": "卖4",
        "price": 11.27,
        "volume": 11176,
        "orders": 217,
        "details": [
          13,
          100,
          10,
          10,
          24,
          5,
          1,
          50,
          9,
          1,
          20,
          15,
          50,
          10,
          1,
          37,
          28,
          81
        ]
      },
      {
        "level": 5,
        "type": "卖5",
        "price": 11.28,
        "volume": 10965,
        "orders": 346,
        "details": [
          59,
          4,
          5,
          50,
          20,
          10,
          10,
          10,
          20,
          10,
          30,
          20,
          2,
          48,
          2,
          20,
          2,
          5,
          70,
          66,
          16
        ]
      },
      {
        "level": 6,
        "type": "卖6",
        "price": 11.29,
        "volume": 16696,
        "orders": 265,
        "details": [
          10,
          10,
          1,
          50,
          1,
          68,
          10,
          15,
          10,
          1,
          26,
          8
        ]
      },
      {
        "level": 7,
        "type": "卖7",
        "price": 11.3,
        "volume": 15109,
        "orders": 546,
        "details": [
          10,
          2,
          60,
          15,
          3,
          10,
          5,
          5,
          10,
          2182,
          1,
          30,
          5,
          20,
          10,
          33
        ]
      },
      {
        "level": 8,
        "type": "卖8",
        "price": 11.31,
        "volume": 3024,
        "orders": 80,
        "details": [
          7,
          30,
          77,
          110,
          111,
          314
        ]
      },
      {
        "level": 9,
        "type": "卖9",
        "price": 11.32,
        "volume": 2462,
        "orders": 85,
        "details": [
          15
        ]
      },
      {
        "level": 10,
        "type": "卖10",
        "price": 11.33,
        "volume": 4926,
        "orders": 113,
        "details": [
          112,
          43,
          100,
          70
        ]
      },
      {
        "level": 11,
        "type": "卖11",
        "price": 11.34,
        "volume": 10,
        "orders": 1,
        "details": [
          10
        ]
      },
      {
        "level": 12,
        "type": "卖12",
        "price": 11.35,
        "volume": 20,
        "orders": 2,
        "details": [
          10,
          10
        ]
      },
      {
        "level": 13,
        "type": "卖13",
        "price": 11.36,
        "volume": 285,
        "orders": 2,
        "details": [
          46,
          239
        ]
      },
      {
        "level": 14,
        "type": "卖14",
        "price": 11.37,
        "volume": 15,
        "orders": 1,
        "details": [
          15
        ]
      },
      {
        "level": 15,
        "type": "卖15",
        "price": 11.39,
        "volume": 110,
        "orders": 2,
        "details": [
          10,
          100
        ]
      },
      {
        "level": 16,
        "type": "卖16",
        "price": 11.4,
        "volume": 2,
        "orders": 2,
        "details": [
          1,
          1
        ]
      },
      {
        "level": 17,
        "type": "卖17",
        "price": 11.46,
        "volume": 4,
        "orders": 1,
        "details": [
          4
        ]
      },
      {
        "level": 18,
        "type": "卖18",
        "price": 11.47,
        "volume": 123,
        "orders": 2,
        "details": [
          15,
          108
        ]
      },
      {
        "level": 19,
        "type": "卖19",
        "price": 11.49,
        "volume": 5,
        "orders": 1,
        "details": [
          5
        ]
      },
      {
        "level": 20,
        "type": "卖20",
        "price": 11.5,
        "volume": 16,
        "orders": 2,
        "details": [
          15,
          1
        ]
      },
      {
        "level": 21,
        "type": "卖21",
        "price": 11.6,
        "volume": 20,
        "orders": 1,
        "details": [
          20
        ]
      },
      {
        "level": 22,
        "type": "卖22",
        "price": 11.66,
        "volume": 10,
        "orders": 1,
        "details": [
          10
        ]
      },
      {
        "level": 23,
        "type": "卖23",
        "price": 11.7,
        "volume": 1362,
        "orders": 3,
        "details": [
          267,
          330,
          765
        ]
      },
      {
        "level": 24,
        "type": "卖24",
        "price": 11.8,
        "volume": 505,
        "orders": 2,
        "details": [
          500,
          5
        ]
      },
      {
        "level": 25,
        "type": "卖25",
        "price": 11.88,
        "volume": 18,
        "orders": 1,
        "details": [
          18
        ]
      },
      {
        "level": 26,
        "type": "卖26",
        "price": 11.98,
        "volume": 3,
        "orders": 1,
        "details": [
          3
        ]
      },
      {
        "level": 27,
        "type": "卖27",
        "price": 12,
        "volume": 32,
        "orders": 1,
        "details": [
          32
        ]
      },
      {
        "level": 28,
        "type": "卖28",
        "price": 12.03,
        "volume": 34113,
        "orders": 341,
        "details": [
          1,
          10,
          2,
          4,
          3,
          30,
          5,
          6,
          3,
          20,
          4,
          5,
          15,
          5,
          4,
          20,
          3,
          150,
          347,
          3,
          1,
          20,
          50,
          2,
          1,
          1,
          1,
          10,
          20,
          10,
          7,
          100,
          10,
          61,
          5,
          30,
          8,
          10,
          20,
          9,
          1,
          10,
          2,
          8,
          7,
          20,
          3,
          2,
          50,
          5
        ]
      }
    ]
  }
}
```

### 个股实时资金流数据

- **函数**: `get_ch_stock_l2_fund_flow_sa`
- **说明**: 获取个股level2实时超大单，大单，中单，小单净流入金额。超大单：单笔≥50万股 或 金额≥100万；大单：50万股> 单笔 ≥10万股  或者 100万> 金额≥ 20万；中单：10万股> 单笔 ≥ 2万股  或 20万> 金额≥ 4万；小单：单笔 < 2万股 或 金额 < 4万；
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 时间 |
| `super_big_net_amt` | number | 超大单净额 |
| `big_net_amt` | number | 大单净额 |
| `medium_net_amt` | number | 中单净额 |
| `small_net_amt` | number | 小单净额 |

- **示例数据**:

```json
[
  {
    "time": "09:30:00",
    "super_big_net_amt": -850300,
    "big_net_amt": -3740000,
    "medium_net_amt": 1591700,
    "small_net_amt": 2998600,
    "price": 11,
    "change_pct": 0.55
  },
  {
    "time": "09:31:00",
    "super_big_net_amt": -13034432,
    "big_net_amt": -4765410,
    "medium_net_amt": 6369781,
    "small_net_amt": 11430061,
    "price": 10.93,
    "change_pct": -0.09
  }
]
```

### 获取个股最新逐笔成交

- **函数**: `get_ch_stock_l2_laster_transactions_sa`
- **说明**: 获取个股最新 100 条逐笔成交（约最近 1-2 分钟内数据）
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 时间 |
| `price` | number | 成交量 |
| `direction` | string | 买卖方向，buy-买，sell-卖，其他-中性 |

- **示例数据**:

```json
[
  {
    "id": "199016193",
    "time": "15:00:00",
    "price": 4.61,
    "volume": 20000,
    "direction": "sell",
    "index": "59086502"
  }
]
```

### 获取个股全部逐笔成交数据

- **函数**: `get_ch_stock_l2_all_transactions_sa`
- **说明**: 获取获取当日全部逐笔成交数据明细。数据量较大，单只个股获取时间较长
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 时间 |
| `price` | number | 成交价格 |
| `volume` | number | 成交量 |
| `direction` | string | 买卖方向，buy-买，sell-卖，其他-中性 |

- **示例数据**:

```json
[
  {
    "id": "199016193",
    "time": "15:00:00",
    "price": 4.61,
    "volume": 20000,
    "direction": "sell",
    "index": "59086502"
  }
]
```

### 市场实时资金流数据

- **函数**: `get_ch_all_market_l2_fund_flow`
- **说明**: 实时获取市场总体资金流数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 时间 |
| `date` | string | 日期 |
| `super_big_net_amt` | number | 超大单净流入金额 |
| `big_net_amt` | number | 大单净流入金额 |
| `medium_net_amt` | number | 中单净流入金额 |
| `small_net_amt` | number | 小单净流入金额 |
| `super_big_in` | number | 超大单买入金额 |
| `super_big_out` | number | 超大单卖出金额 |
| `big_in` | number | 大单买入金额 |
| `big_out` | number | 大单卖出金额 |
| `medium_in` | number | 中单买入金额 |
| `medium_out` | number | 中单卖出金额 |
| `small_in` | number | 小单买入金额 |
| `small_out` | number | 小单卖出金额 |

- **示例数据**:

```json
[
  {
    "time": "10:19:00",
    "date": "2026-06-18",
    "super_big_net_amt": -2389889024,
    "big_net_amt": -10093412864,
    "medium_net_amt": -8201449472,
    "small_net_amt": 20684699136,
    "super_big_in": 214083859712,
    "super_big_out": 216473748736,
    "big_in": 358645539584,
    "big_out": 368738952448,
    "medium_in": 451774112768,
    "medium_out": 459975562240,
    "small_in": 361554208512,
    "small_out": 340869509376
  }
]
```

### 上证指数实时资金流数据

- **函数**: `get_ch_sh_market_l2_fund_flow`
- **说明**: 上证指数实时资金流数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 时间 |
| `date` | string | 日期 |
| `super_big_net_amt` | number | 超大单净流入金额 |
| `big_net_amt` | number | 大单净流入金额 |
| `medium_net_amt` | number | 中单净流入金额 |
| `small_net_amt` | number | 小单净流入金额 |
| `super_big_in` | number | 超大单买入金额 |
| `super_big_out` | number | 超大单卖出金额 |
| `big_in` | number | 大单买入金额 |
| `big_out` | number | 大单卖出金额 |
| `medium_in` | number | 中单买入金额 |
| `medium_out` | number | 中单卖出金额 |
| `small_in` | number | 小单买入金额 |
| `small_out` | number | 小单卖出金额 |

- **示例数据**:

```json
[
  {
    "time": "10:29:00",
    "date": "2026-06-18",
    "super_big_net_amt": 462137024,
    "big_net_amt": -7088859008,
    "medium_net_amt": -4477754496,
    "small_net_amt": 11104413184,
    "super_big_in": 118583829120,
    "super_big_out": 118121692096,
    "big_in": 192254218112,
    "big_out": 199343077120,
    "medium_in": 232578667776,
    "medium_out": 237056422272,
    "small_in": 172077933440,
    "small_out": 160973520256
  }
]
```

### 深圳市场实时资金流数据

- **函数**: `get_ch_sz_market_l2_fund_flow`
- **说明**: 深圳市场实时资金流数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 时间 |
| `date` | string | 日期 |
| `super_big_net_amt` | number | 超大单净流入金额 |
| `big_net_amt` | number | 大单净流入金额 |
| `medium_net_amt` | number | 中单净流入金额 |
| `small_net_amt` | number | 小单净流入金额 |
| `super_big_in` | number | 超大单买入金额 |
| `super_big_out` | number | 超大单卖出金额 |
| `big_in` | number | 大单买入金额 |
| `big_out` | number | 大单卖出金额 |
| `medium_in` | number | 中单买入金额 |
| `medium_out` | number | 中单卖出金额 |
| `small_in` | number | 小单买入金额 |
| `small_out` | number | 小单卖出金额 |

- **示例数据**:

```json
[
  {
    "time": "10:30:00",
    "date": "2026-06-18",
    "super_big_net_amt": -1732657344,
    "big_net_amt": -4471252608,
    "medium_net_amt": -5342562432,
    "small_net_amt": 11546418176,
    "super_big_in": 117821062272,
    "super_big_out": 119553719616,
    "big_in": 203278766208,
    "big_out": 207750018816,
    "medium_in": 266322837248,
    "medium_out": 271665399680,
    "small_in": 230166198016,
    "small_out": 218619779840
  }
]
```

### 创业板实时资金流数据

- **函数**: `get_ch_cyb_market_l2_fund_flow`
- **说明**: 创业板实时资金流数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 时间 |
| `date` | string | 日期 |
| `super_big_net_amt` | number | 超大单净流入金额 |
| `big_net_amt` | number | 大单净流入金额 |
| `medium_net_amt` | number | 中单净流入金额 |
| `small_net_amt` | number | 小单净流入金额 |
| `super_big_in` | number | 超大单买入金额 |
| `super_big_out` | number | 超大单卖出金额 |
| `big_in` | number | 大单买入金额 |
| `big_out` | number | 大单卖出金额 |
| `medium_in` | number | 中单买入金额 |
| `medium_out` | number | 中单卖出金额 |
| `small_in` | number | 小单买入金额 |
| `small_out` | number | 小单卖出金额 |

- **示例数据**:

```json
[
  {
    "time": "10:40:00",
    "date": "2026-06-18",
    "super_big_net_amt": -106241328,
    "big_net_amt": 415667264,
    "medium_net_amt": -2661166656,
    "small_net_amt": 2351718784,
    "super_big_in": 65812027328,
    "super_big_out": 65918268656,
    "big_in": 113836520704,
    "big_out": 113420853440,
    "medium_in": 143009484160,
    "medium_out": 145670650816,
    "small_in": 110904102688,
    "small_out": 108552383904
  }
]
```

### 科创板实时资金流数据

- **函数**: `get_ch_kcb_market_l2_fund_flow`
- **说明**: 科创板实时资金流数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 时间 |
| `date` | string | 日期 |
| `super_big_net_amt` | number | 超大单净流入金额 |
| `big_net_amt` | number | 大单净流入金额 |
| `medium_net_amt` | number | 中单净流入金额 |
| `small_net_amt` | number | 小单净流入金额 |
| `super_big_in` | number | 超大单买入金额 |
| `super_big_out` | number | 超大单卖出金额 |
| `big_in` | number | 大单买入金额 |
| `big_out` | number | 大单卖出金额 |
| `medium_in` | number | 中单买入金额 |
| `medium_out` | number | 中单卖出金额 |
| `small_in` | number | 小单买入金额 |
| `small_out` | number | 小单卖出金额 |

- **示例数据**:

```json
[
  {
    "time": "10:45:00",
    "date": "2026-06-18",
    "super_big_net_amt": 3629187256,
    "big_net_amt": -498143568,
    "medium_net_amt": -2683148032,
    "small_net_amt": -447904856,
    "super_big_in": 53845142568,
    "super_big_out": 50215955312,
    "big_in": 90000077216,
    "big_out": 90498220784,
    "medium_in": 91177645616,
    "medium_out": 93860793648,
    "small_in": 37435554920,
    "small_out": 37883459776
  }
]
```

### 个股实时大单成交明细

- **函数**: `get_ch_stock_big_order`
- **说明**: 返回个股交易日当天实时成交大单明细
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码。如：000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `ticktime` | string | 时间 |
| `price` | number | 成交价 |
| `volume` | number | 成交量 |
| `amount` | number | 成交额 |
| `kind` | string | 成交类型。U 主动买入，D 主动卖出，E 中性 |

- **示例数据**:

```json
[ {'ticktime': '09:38:28', 'price': 10.44, 'volume': 103900, 'amount': 1084716, 'kind': 'D'}, {'ticktime': '09:33:37', 'price': 10.49, 'volume': 51100, 'amount': 536039, 'kind': 'U'}, {'ticktime': '09:33:16', 'price': 10.48, 'volume':
 427300, 'amount': 4478104, 'kind': 'U'}, {'ticktime': '09:32:15', 'price': 10.48, 'volume': 52400, 'amount': 549152, 'kind': 'U'}, {'ticktime': '09:30:53', 'price': 10.44, 'volume': 147700, 'amount': 1541988, 'kind': 'U'}, {'ticktime': '09:30:48', 'price': 10.44, 'volume': 112600, 'amount': 1175544, 'kind'
: 'U'}, {'ticktime': '09:30:42', 'price': 10.44, 'volume': 173200, 'amount': 1808208, 'kind': 'U'}, {'ticktime': '09:30:32', 'price': 10.46, 'volume': 51500, 'amount': 538690, 'kind': 'U'}, {'ticktime': '09:30:18', 'price': 10.43, 'volume': 53200, 'amount': 554876, 'kind': 'U'}, {'ticktime': '09:30:12', 'price': 10.42, 'volume': 50700, 'amount': 528294, 'kind': 'D'}, {'ticktime': '09:25:00', 'price': 10.5, 'volume': 50200, 'amount': 527100, 'kind': 'U'}]
```

### 订阅Level2个股成交明细通道

- **函数**: `subscribe_ch_stock_transaction`
- **说明**: 订阅全量个股Level2个股成交明细通道，实时推送变化个股

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `id` | string | 成交ID |
| `time` | string | 时间 |
| `price` | number | 成交价 |
| `vol` | number | 成交量 |
| `side` | string | 成交方向。B 主动买，S 主动卖，M 中性 |

- **示例数据**:

```json
{'sz300475': {'id': 59651716, 'time': '15:00:00.000', 'price': 271.0, 'vol': 4598, 'side': 'M'}}
```

---

## 新闻资讯

_重点资讯、国内/国际新闻、时评、个股新闻等全市场资讯数据_

### 重点资讯新闻

- **函数**: `get_core_new`
- **说明**: 获取指定日期重点资讯新闻
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式如 2026-03-01 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 发布日期时间 |
| `content` | string | 正文 |
| `title` | string | 标题 |

- **示例数据**:

```json
[
  {
    "title": "新型能源体系建设“十五五”规划出炉 2030年我国非化石能源发电量比重达到50%",
    "date": "2026-06-26 02:13:29",
    "content": "“十五五”时期，我国能源发展进入安全风险叠加演变期、低碳转型加力推进期、能源创新加速突破期、体制改革深度攻坚期、国际合作调整重塑期。为科学引领能源高质量发展，加快建设新型能源体系，6月25日，国家发展改革委、国家能源局发布消息，已于日前印发《新型能源体系建设“十五五”规划》（以下简称《规划》）。《规划》提出，2030年初步建成清洁低碳安全高效的新型能源体系。能源综合生产能力达到58亿吨标准煤，电力系统互补互济和安全韧性水平全面提升，能源进口多元可控；煤炭和石油消费达峰，非化石能源消费比重达到25%，风电和太阳能发电装机比重超过50%、成为电力装机主体，非化石能源发电量比重达到50%、成为电量主体；坚强韧性、绿色低碳、集成融合、智能高效的新型能源基础设施体系加快建设，新型电力系统初步建成；能源产业链关键技术装备实现总体自主可控，迈入世界能源科技创新国家前列；适应新型能源体系的市场和价格机制加快健全，全国统一电力市场体系基本建成。在空间布局上，将坚持“全国一盘棋”，统筹能源和经济、总量和结构、全国和区域、国内和国际，推动非化石能源供应形成五大增长板块，巩固优化化石能源生产基地，加强能源开发与用能产业布局协同，统筹优化能源骨干通道布局，不断拓展多元化进口通道。具体到供给端，《规划》构建多元协同的能源基础设施体系。其中，非化石能源供给规模将持续扩大，将积极推进地热能、氢能和绿色燃料发展，新能源非电利用规模实现倍增，同时建立完善新能源消纳综合评价指标体系，2030年新能源发电量占比达到30%；将加快推动主要流域水风光一体化基地规划建设。统筹推进主要流域水电规划调整，2030年常规水电装机达到4.1亿千瓦左右。此外，《规划》还提出积极安全有序发展核电，2030年在运核电装机达到1.1亿千瓦左右。针对高比例新能源消纳难题，将系统布局储能资源，目标抽水蓄能装机1.6亿千瓦、新型储能3亿千瓦；同时推动火电转型为调节支撑电源，发展虚拟电厂、车网互动，2030年车网互动聚合可调充电规模达到5000万千瓦左右。加快推进虚拟电厂规模化发展，2030年虚拟电厂调节能力达到5000万千瓦以上。化石能源方面，将优化山西、蒙西等五大煤炭基地与鄂尔多斯等油气基地布局，推进煤炭绿色智能开采、油气田低碳改造，稳住化石能源兜底保障基本盘。安全保障也是《规划》的核心主线。《规划》提出筑牢能源安全底线，一方面加大油气增储上产，稳定原油年产量2亿吨水平，完善四大油气进口通道与全国油气管网，2030年天然气管网一次管输能力达到5000亿立方米/年；另一方面强化新能源锂、硅等关键矿产保供，完善煤炭产能储备，2030年形成1亿吨/年以上煤炭产能储备。同时健全能源风险监测预警、重大基础设施防护机制，守住极端工况下能源供应安全红线。消费侧则将全面推进节能降碳与绿色用能升级。《规划》要求工业、建筑、交通领域优化能源清洁替代路径。民生用能配套也将同步提速，2030年充电基础设施增至4000万个，人均年生活用电量达到1500千瓦时，城乡清洁供暖、智慧供热体系将进一步铺开。（文章来源：证券时报）",
    "new_id": ""
  }
]
```

### 国内主要新闻

- **函数**: `get_domestic_financial_news`
- **说明**: 获取指定日期国内资讯新闻
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式 YYYY-MM-DD |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 发布日期 |
| `content` | string | 正文 |
| `title` | string | 标题 |

- **示例数据**:

```json
[
  {
    "title": "2026夏季达沃斯｜北京绿金院白韫雯：绿色金融对“新三样”的支持已产生显著环境效益",
    "date": "2026-06-26 00:02:37",
    "content": "6月23日至25日，2026年夏季达沃斯论坛在大连举行。当人工智能在本届夏季达沃斯论坛上抢尽风头，另一条线也在引发关注——绿色金融。这是由于环境议题正与经济增长、产业竞争力及国家安全紧密结合。在中国，绿色信贷规模全球第一、绿色债券市场规模全球前列的成绩单已然亮眼，但一个更大的命题浮出水面：当能源安全与地缘政治交织，当AI重塑产业逻辑，绿色金融还能在哪些维度释放潜能？AI技术能否成为打通绿色金融与C端的关键桥梁？新能源汽车“出海”热潮中，中国企业又该如何输出不只是产品、更是标准的竞争力？围绕这些问题，北京绿色金融与可持续发展研究院副院长白韫雯接受了北京商报记者的专访，给出了她的观察与思考。AI溯源的想象力：让绿色消费不再“盲选”今年达沃斯论坛上，AI是最热的关键词。但白韫雯看到的，是AI与绿色金融之间一条尚待开掘的连接线。以往，绿色金融主要服务于大企业和大项目，普通消费者很难直接感知，如银行发放的绿色贷款投向了哪座光伏电站、哪条地铁线路，与日常消费似乎隔着千山万水。白韫雯认为，AI的讨论与可持续发展和消费者息息相关。以往绿色金融主要服务于大企业和大项目，难以直接关联消费者。AI技术增加了产品的可溯源性，使消费者能够了解产品来源，例如所饮牛奶是否来自恢复的草场、是否在草畜平衡环境下生产，从而增强消费信心。整体而言，绿色金融可以在其中扮演多重角色：前端通过识别绿色生产活动，向生产者提供挂钩贷款等支持，促进其绿色转型；中间环节支持绿色贸易。但在消费端，则需要更谨慎地甄别。当前C端绿色消费领域存在一些乱象。如部分电商或银行以绿色分期为噱头提供利率优惠，或部分新能源家装品牌伪造低碳认证以获取金融贴息。白韫雯对此表示，确实存在此类情况。在一些熟悉领域，标签规范且有第三方认证支撑，但许多产品随意标注“自然”“健康”或使用树叶图标，导致市场混乱。那么，消费者该如何选择？白韫雯的建议是：首先应查看包装上的标签，因为标签代表标准和认证背书。AI技术的发展使未来产品可通过扫码追溯生产过程，如用水量、土地利用变化、生态修复成效等，有助于消费者更清晰地了解产品，从而为自然资本付费。在制度层面，绿色产品已有一定认定标准，如有机标签、环境产品标签、家电节能标签，相关规范也在不断完善。但目前品类尚未覆盖所有日常消费品，标准体系仍待拓展。白韫雯特别提到欧盟的做法——欧盟为落实绿色新政，已在许多产品上设置数字产品护照（二维码），扫码可了解产地、碳排放、用水量等信息。此外，从绿色金融角度看，投资者在进行资产配置时已有较为成熟的标准体系可依循。人民银行等部门持续修订完善绿色金融标准，使绿色界定更加清晰统一，有效指导金融机构和投资者识别合格的绿色项目与经济活动。当然，标准体系固然至关重要，但要确保市场公信力，还需健全第三方认证与核证机制，为绿色属性提供可信的外部验证。从道义到赛道：绿色金融成“压舱石”绿色金融对中国经济究竟意味着什么？白韫雯给出了一个宏观视角：“金融是经济的命脉。当前全球面临气候变化、极端天气及自然退化等可持续发展挑战。国际上，《巴黎协定》设定了温控目标，《昆蒙框架》也明确了到2030年生物多样性保护目标。在这些目标下，需要推动经济平稳绿色转型。这一过程已从传统上对可持续发展的道义讨论，转向关乎经济安全的议题。”白韫雯观察到，这一认知转变在近年来尤为明显。以往绿色金融常被视为金融机构的表率性企业社会责任，而如今绿色金融已成为金融“五篇大文章”之一，逐渐与主流金融融为一体。这背后是政策逻辑的深刻变化，从激励引导到制度嵌入，绿色金融正在成为金融体系的有机组成部分。具体而言，白韫雯将绿色金融的助力归纳为三个层面：一是，金融资源优化配置引领产业升级。通过绿色金融的激励机制和细化的标准体系，引导资本从高碳、高污染行业退出并转向绿色低碳产业，以及生态修复、可持续农业等生态溢价显著的领域，促进经济结构性转型与高质量发展。二是，助力企业和金融机构强化风险防范。白韫雯表示，全球超过一半的经济活动高度或中度依赖自然资本和生态系统服务，而高温热浪、极端天气以及生态系统持续退化让经济系统脆弱性加剧。识别、评估和管理这类风险，也能帮助企业和金融机构前瞻性地把握低碳与自然向好转型的机遇，切实增强自身供应链韧性与长期竞争力。三是提升全球金融治理的制度构建能力与话语权。在白韫雯看来，过去几年，绿色金融推动了绿色产业快速发展，我国绿色债券和绿色贷款规模已居全球首位，产品体系与质量也在不断提升，与此同时，我国积极参与国际绿色金融标准与规则的制定，在全球可持续金融治理中发挥了重要的作用。从B端到C端：新能源叙事还有“下半场”传统绿色金融产品，如绿色债券和绿色贷款，主要面向B端或G端，以项目为主。面向C端的产品相对有限。但近年来个人也可以购买标注为绿色或ESG的理财产品。此类产品已开始标签化，有助于提升公众意识、引导消费行为，为消费者提供更多选择。“可借鉴To B端产品中可持续挂钩贷款和债券的做法，不仅投向绿色项目，还与环境绩效直接挂钩。”白韫雯提出，未来C端产品也应如此，例如碳减排量和生态效益应更加透明，有助于消费者做出更明智的选择。对于绿色消费产品的更长远展望，白韫雯的思考触及了一个新概念——自然市场。“当前我们从 ‘为自然融资’迈向‘构建自然市场’，核心思路是将生态保护效益与金融产品乃至个人消费行为直接挂钩。除了实现产品的全链条可溯源外，还可将土壤健康改善、红树林保护等生态效益标准化为可计量、可交易的‘生态商品’，也就是一个生物多样性信用。本质上都是让‘保护自然’这件事有经济回报，让保护者不再只靠情怀和补贴。”白韫雯如是表示。谈及绿色金融已有显著成效的领域，白韫雯认为新能源汽车是最成功的例子之一。绿色金融在过去有效支持了“新三样”（新能源汽车、锂电池、光伏产品）的发展，环境效益显著。而下一个应用场景，仍是AI。白韫雯观察到，未来其新应用场景在于AI技术，例如无人驾驶已从规则驱动转向AI驱动，使驾驶更顺畅，体验感大幅提升。新能源汽车在AI场景下的应用促进智能交通，协调道路与车辆关系，推动节能减排和绿色能源利用。更值得关注的是中国新能源汽车“走出去”的叙事升级。白韫雯指出，新能源汽车也是中国产业链“走出去”的重要行业，如比亚迪、蔚来等在泰国等国家海外布局，不仅输出产品和延伸产业链，更应输出ESG能力，助力“一带一路”国家绿色低碳转型。值得关注的是，针对美伊冲突及霍尔木兹海峡受阻引发的能源安全讨论，白韫雯表示，这反而为新能源发展带来利好。从能源安全角度看，AI的发展需要绿色能源支撑，绿色能源发展领先的国家将在AI领域更具竞争力。外部地缘政治变化可能带来微小调整，但大方向不变。（文章来源：北京商报）",
    "new_id": ""
  }
]
```

### 国际主要新闻

- **函数**: `get_global_financial_news`
- **说明**: 获取指定日期国际主要新闻
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式：YYYY-MM-DD |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 发布日期 |
| `content` | string | 正文 |
| `title` | string | 标题 |

- **示例数据**:

```json
[
  {
    "title": "房地美表示 美国上周30年期按揭贷款/抵押贷款利率6.49% 前值6.47%",
    "date": "2026-06-26 00:02:05",
    "content": "房地美表示，美国上周30年期按揭贷款/抵押贷款利率6.49%，前值6.47%。（文章来源：财联社）",
    "new_id": ""
  }
]
```

### 时评类新闻

- **函数**: `get_options_news`
- **说明**: 获取指定日期时评类新闻
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式：YYYY-MM-DD |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 发布日期 |
| `content` | string | 正文 |
| `title` | string | 标题 |

- **示例数据**:

```json
[
  {
    "title": "国金证券：美光科技推进长协落地 供需缺口有望持续",
    "date": "2026-06-26 07:53:00",
    "content": "人民财讯6月26日电，国金证券研报认为，美光科技推进长协落地，供需缺口有望持续。美光科技已经与客户完成16个SCA（战略客户合作协议），下游涵盖数据中心、消费电子、汽车市场。SCA中汽车客户签订时间为三年，其他客户基本为五年。16个SCA协议已经占到美光科技20%的DRAM出货量，1/3的NAND出货量。美光科技签订的SCA的价格区间中下限也可以带来超过过去周期顶点的盈利能力。美光科技预计2027年DRAM与NAND供应将持续紧张。国金证券认为存储行业供给有望持续紧张，美光科技有望持续维持高盈利能力。美光科技与下游客户推进长协签订，有望降低公司产品出货价的周期性波动，降低公司业绩周期性。（文章来源：证券时报网）",
    "new_id": ""
  }
]
```

### 个股新闻

- **函数**: `get_ch_stock_month_news`
- **说明**: 获取个股指定年-月的新闻数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |
| `day` | string | 是 | 年月，格式 2026-04 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 发布日期 |
| `content` | string | 新闻内容 |
| `title` | string | 新闻标题 |

- **示例数据**:

```json
[
  {
    "title": "中小银行改革化险节奏加快，银行ETF博时(159253)涨超1%",
    "date": "2026-06-05 10:27",
    "content": "截至2026年6月5日 10:11，中证银行指数(399986)强势上涨1.02%，成分股成都银行上涨1.81%，南京银行上涨1.63%，江苏银行上涨1.60%，平安银行，长沙银行等个股跟涨。银行ETF博时(159253)上涨1.09%，最新价报0.93元。拉长时间看，截至2026年6月4日，银行ETF博时近1周累计上涨1.54%。流动性方面，银行ETF博时盘中换手0.18%，成交109.99万元。拉长时间看，截至6月4日，银行ETF博时近1月日均成交3050.81万元。消息面上，近日，国家金融监督管理总局许可证信息系统显示，河南农商银行在漯河市落地29家分支机构。此次机构新设，标志着该行对漯河区域农信机构整合落地，河南全省农信改制、分批并入省级农商行的工作再进一步。湘财证券指出，截至2026年5月末，银行理财产品存续规模回升至约32.6万亿元，二季度以来增长趋势延续但增速放缓；同期理财产品近1年加权平均年化收益率升至2.93%，其中权益类与混合类产品收益率分别达5.32%和3.63%，表现持续走强，而现金管理类产品收益率则小幅下行至1.18%。在权益市场结构性行情支撑下，“固收+”产品破净率降至近一年低位，显示整体风险偏好趋于稳定。西部证券分析认为，银行通过投贷联动模式深度参与硬科技企业融资，如长鑫科技、长江存储等关键技术领域项目，既响应国家战略支持科技自立，亦有助于拓宽非息收入来源以对冲息差收窄压力。以长鑫科技为例，若其上市后市值达万亿，建设银行、徽商银行等将显著受益于股权增值带来的利润增厚，国有大行普遍参与，股份行与城商行参与度相对有限。该模式标志着银行正从传统信贷提供者向“耐心资本”角色转型。银行ETF博时紧密跟踪中证银行指数，为反映中证全指指数样本中不同行业公司证券的整体表现，为投资者提供分析工具，将中证全指指数样本按中证行业分类分为11个一级行业、35个二级行业、90余个三级行业及200余个四级行业，再以进入各一、二、三、四级行业的全部证券作为样本编制指数，形成中证全指行业指数。数据显示，截至2026年5月29日，中证银行指数(399986)前十大权重股分别为招商银行、兴业银行、工商银行、农业银行、交通银行、江苏银行、浦发银行、平安银行、宁波银行、上海银行，前十大权重股合计占比63.66%。银行ETF博时(159253)，场外联接(博时中证银行ETF联接C：018591；博时中证银行ETF联接A：160517)。（文中个股仅作示例，不构成实际投资建议。基金有风险，投资需谨慎。）以上产品风险等级为：中（此为管理人评级，具体销售以各代销机构评级为准）风险提示：基金不同于银行储蓄和债券等固定收益预期的金融工具，不同类型的基金风险收益情况不同，投资人既可能分享基金投资所产生的收益，也可能承担基金投资所带来的损失。基金的过往业绩并不预示其未来表现。投资者应了解基金的风险收益情况，结合自身投资目的、期限、投资经验及风险承受能力谨慎决策并自行承担风险，不应采信不符合法律法规要求的销售行为及违规宣传推介材料。\n相关新闻\n加载中\n点击加载更多",
    "new_id": "6ff13094ec4ca24c"
  }
]
```

### 财经快讯(数据源sn)

- **函数**: `get_ch_sn_kx`
- **说明**: 获取指定日期快讯数据，包含正文全文、来源、标签、关联股票等信息。返回数据格式为Dict
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 查询日期，格式 YYYY-MM-DD |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 YYYY-MM-DD |
| `id` | string | 快讯唯一ID |
| `title` | string | 标题 |
| `content` | string | 正文全文 |
| `time_ms` | number | 发布时间(毫秒时间戳) |
| `tags_json` | string | 标签JSON，包含话题标签和关联股票信息 |

- **示例数据**:

```json
{
  "date": "2026-06-26",
  "data": [
    {
      "id": "3980674",
      "title": "国际油价25日上涨 布油涨超2%",
      "content": "人民财讯6月26日电，国际油价25日上涨。截至当天收盘，纽约商品交易所8月交货的轻质原油期货价格上涨1.58美元，收于每桶71.92美元，涨幅为2.25%；8月交货的伦敦布伦特原油期货价格上涨1.52美元，收于每桶75.26美元，涨幅为2.06%。",
      "time_ms": "1782428339000",
      "source": "人民财讯",
      "tags_json": "{\"tags\": [[{\"name\": \"国际油价\", \"title\": \"国际油价\", \"tag_id\": 4984, \"url\": \"/article/kx-tag-detail.html?tag=F8vwj31dM3Ir\"}, {\"name\": \"纽约商品交易...\", \"title\": \"纽约商品交易所\", \"tag_id\": 498097, \"url\": \"/article/kx-tag-detail.html?tag=EvxwJRCb3x68\"}, {\"name\": \"轻质原油期货\", \"title\": \"轻质原油期货\", \"tag_id\": 498179, \"url\": \"/article/kx-tag-detail.html?tag=hcEqERxBZE_w\"}, {\"name\": \"油价上涨\", \"title\": \"油价上涨\", \"tag_id\": 553565, \"url\": \"/article/kx-tag-detail.html?tag=xuW0LHSWw7D6\"}], []], \"tag_ids\": [4984, 498097, 498179, 553565], \"stock_codes\": []}",
      "is_red": 0,
      "is_top": 0
    }
  ]
}
```

### 财经快讯(数据源SA)

- **函数**: `get_ch_sa_kx`
- **说明**: 获取市场财经快讯(数据源SA)
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `content` | string | 快讯内容 |
| `time_ms` | string | 时间戳字符串 |
| `tags_json` | string | 关联的标签列表 |
| `title` | string | 标题 |
| `date` | string | 日期 |

- **示例数据**:

```json
{
  "date": "2026-06-14",
  "data": [
    {
      "id": "4933958",
      "content": "伊朗方面表示，现阶段不会提及核问题，解冻伊朗被冻结资产是相关协议的必要内容。",
      "time_ms": "1781366883000",
      "source": "SA",
      "tags_json": "[{\"id\": \"102\", \"name\": \"国际\"}]",
      "title": "",
      "is_red": 0,
      "is_top": 0
    },
    {
      "id": "4933959",
      "content": "伊朗法尔斯通讯社：各方商定，现阶段暂不提及核问题。",
      "time_ms": "1781366915000",
      "source": "SA",
      "tags_json": "[{\"id\": \"102\", \"name\": \"国际\"}]",
      "title": "",
      "is_red": 0,
      "is_top": 0
    }
}
```

### 个股公告

- **函数**: `get_ch_stock_announce`
- **说明**: 获取个股指定日期公告信息，如果返回数据为空，表示当天无公告。
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码 |
| `date` | string | 是 | 日期，格式为：YYYY-MM-DD |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `data` | list | 日内发布的公告列表数据 |
| `ann_id` | string | 公告ID |
| `title` | string | 公告标题 |
| `content` | string | 公告内容 |

- **示例数据**:

```json
{
  "date": "2026-06-05",
  "data": [
    {
      "ann_id": "1225352449",
      "title": "2025年年度权益分派实施公告",
      "content": "证券代码：000001\n\n证券简称：平安银行\n\n公告编号：2026-025\n\n平安银行股份有限公司 2025 年年度权益分派实施公告\n\n本公司及董事会全体成员保证信息披露的内容真实、准确、完整，没有虚假记载、误导\n\n性陈述或重大遗漏。\n\n平安银行股份有限公司 2025 年年度权益分派方案已获 2026 年 5 月 22 日召\n\n开的本公司 2025 年年度股东会审议通过，现将权益分派事宜公告如下：\n\n一、股东会审议通过利润分配方案等情况\n\n1、2026 年 5 月 22 日，本公司 2025 年年度股东会审议通过了《平安银行股\n\n份有限公司 2025 年度利润分配方案》：以本公司 2025 年 12 月 31 日的总股本\n\n19,405,918,198 股为基数，2025 年全年以每 10 股派发现金股利人民币 5.96 元（含\n\n税），其中：2025 年中期已按每 10 股派发现金股利人民币 2.36 元（含税）；2025\n\n年末期以每 10 股派发现金股利人民币 3.60 元（含税），不送红股，不以公积金\n\n转增股本。\n\n2、自分配方案披露至实施期间本公司股本总额未发生变化。本次分配方案\n\n以分配总额不变的原则实施。\n\n3、本次实施的分配方案与股东会审议通过的分配方案一致。\n\n4、本次实施分配方案距离股东会审议通过的时间未超过两个月。\n\n二、本次实施的权益分派方案\n\n本次实施的权益分派方案为：以公司现有总股本 19,405,918,198 股为基数，\n\n向全体股东每 10 股派 3.6000 元人民币现金（含税；扣税后，通过深股通持有股\n\n份的香港市场投资者、境外机构（含 QFII、RQFII）以及持有首发前限售股的个\n\n人和证券投资基金每 10 股派 3.2400 元；持有首发后限售股、股权激励限售股及\n\n无限售流通股的个人股息红利税实行差别化税率征收，本公司暂不扣缴个人所得\n\n税，待个人转让股票时，根据其持股期限计算应纳税额【注】；持有首发后限售\n\n股、股权激励限售股及无限售流通股的证券投资基金所涉红利税，对香港投资者\n\n持有基金份额部分按 10%征收，对内地投资者持有基金份额部分实行差别化税率\n\n征收）。\n\n1\n\n\f【注：根据先进先出的原则，以投资者证券账户为单位计算持股期限，持股\n\n1 个月（含 1 个月）以内，每 10 股补缴税款 0.7200 元；持股 1 个月以上至 1 年\n\n（含 1 年）的，每 10 股补缴税款 0.3600 元；持股超过 1 年的，不需补缴税款。】\n\n三、股权登记日与除权除息日\n\n本次权益分派股权登记日为：2026 年 6 月 11 日，除权除息日为：2026 年 6\n\n月 12 日。\n\n四、权益分派对象\n\n本次分派对象为：截止 2026 年 6 月 11 日下午深圳证券交易所收市后，在中\n\n国证券登记结算有限责任公司深圳分公司（以下简称“中国结算深圳分公司”）\n\n登记在册的本公司全体股东。\n\n五、权益分派方法\n\n本公司此次委托中国结算深圳分公司代派的 A 股股东现金红利将于 2026 年\n\n6 月 12 日通过股东托管证券公司（或其他托管机构）直接划入其资金账户。\n\n六、咨询机构\n\n咨询地址：广东省深圳市福田区益田路 5023 号平安金融中心 B 座\n\n咨询联系人：平安银行股份有限公司董事会办公室\n\n咨询电话：0755-82080387\n\n传真电话：0755-82080386\n\n七、备查文件\n\n1、本公司第十三届董事会第三次会议决议；\n\n2、本公司 2025 年年度股东会决议。\n\n特此公告。\n\n平安银行股份有限公司董事会\n\n2026 年 6 月 5 日\n\n2",
      "date_time": ""
    }
  ]
}
```

### 个股研报

- **函数**: `get_ch_stock_research_report`
- **说明**: 获取个股指定日期研报信息。如果对应日期返回为空，则表示当日无研报数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码 |
| `date` | string | 是 | 日期。格式YYYY-MM-DD |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `reports` | list | 当天发布的研报数据表 |
| `title` | string | 研报名称 |
| `org` | string | 研报发布机构名称 |
| `analyst` | string | 研报分析员 |
| `content` | string | 研报内容 |

- **示例数据**:

```json
{
  "date": "2026-05-09",
  "reports": [
    {
      "title": "平安银行(000001)2026一季报点评：营收业绩增速均转正 底部位置确立",
      "report_type": "公司",
      "org": "国盛证券股份有限公司",
      "analyst": "刘斐然/朱广越",
      "rptid": "831679231047",
      "content": "事件：\n平安银行披露2026 年一季报，公司2026 年第一季度实现营业收入352.77亿元，同比+4.7%，实现归母净利润145.23 亿元，同比+3%。\n一、营收利润增速均转正。\n营收、利润增速环比均提升。公司1Q26 末实现营收352.77 亿元，同比+4.7%，1Q26 增速较2025A 环比+15pct；1Q26 末实现归母净利润145.23亿元，同比+3%，1Q26 增速较2025A 环比+7.2pct。\n分拆业绩贡献因素：1）净利息收入降幅收窄。规模方面，1Q26 生息资产规模贡献业绩4.1%，幅度较2025A 提升1.9pct；价格方面，1Q26 净息差拖累公司业绩7.2%，1Q26 较2025A 少拖累0.8pct。2）手续费及佣金收入贡献幅度提升。1Q26 贡献业绩3.3%,较2025A 提升2.3%。3）其他非息收入形成正向贡献。1Q26 净其他非息收入贡献业绩4.4%，主要受去年同期低基数影响。4）拨备对业绩贡献转负。1Q26 拨备计提拖累业绩1.3%。\n二、信贷规模稳步增长，个贷同比增速回正。\n公司1Q26 末资产总计、负债总计分别为6.03 万亿元、5.49 万亿元，同比分别+4.43%、+4.14%，1Q26 同比增速较2025 年末分别增长1.72pct、2.24pct，较上年同期分别增长3.59pt、3.61pct。\n分结构来看：1）资产端，个贷同比增速回正。公司1Q26 末发放贷款总额3.46 万亿元，同比+1.55%，增速较上年同期增长3.57pct。其中，1Q26末发放对公贷款总额1.73 万亿元，同比+2.87%，增速较上年同期降低2.04pct；1Q26 末发放个人贷款总额1.73 万亿元，同比+0.26%，增速较上年同期增加8.2pct。2）负债端，存款增速有所回落。公司1Q26 末吸收存款总额3.7 万亿元，同比+0.96%，增速较上年同期降低5.27pct。其中，1Q26 末吸收对公存款总额2.37 万亿元，同比+1.45%，增速较上年同期降低4.88pct；1Q26 末吸收个人存款总额1.33 万亿元，同比+0.09%，增速较上年同期降低5.95pct。\n三、净息差环比略升。\n公司1Q26 末净息差1.79%，较去年同期下降4bp，较2025 年全年上升1bp。具体来看：1）生息资产收益率压力持续。根据测算，公司1Q26 末生息资产收益率2.74%，同比-47bp。1Q26 发放贷款平均收益率3.67%，同比-48bp。2）负债成本持续优化。根据测算1，Q2公6司末计息成本负债率1.38%，同比-38bp，主要因公司持续强化客户拓展和经营，促进低成本存款的吸收，推动存款结构和成本优化。1Q26 吸收存款平均付息率1.41%，同比-40bp。对公存款平均付息率1.32%，同比-41bp，个人存款平均付息率1.56%，同比-40bp。\n四、非息收入实现高增，为贡献营收核心因素。\n1Q26 末平安银行实现非利息净收入131.96 亿元，同比增长20.8%，财富管理与交易服务等业务的非利息净收入同比增长，收入结构持续优化。\n具体来看，1Q26 公司手续费及佣金净收入73.62 亿元，同比增长11.7%，增速较2025 末提升12.6pct。1Q26 公司财富管理手续费收入达18.74 亿元，同比增长 55.1%；其中，代理个人保险收入6.83 亿元，同比增长98.5%，代理个人理财收入3.40 亿元，同比增长14.1%，代理个人基金收入7.69 亿元，同比增长47.3%。此外，1Q26 公司净其他非息收入58.34亿元，同比增长34.8%，较2025 末同比-33%的增速有明显提升。1Q26公司境内外机构销售的现券交易量2.16 万亿元，同比增长113.9%，交易服务业务对公司营收形成有力贡献。\n五、资产质量保持平稳。\n公司1Q26 末不良贷款率为1.05%，较上年末持平。1Q26 末对公贷款不良率0.87%，个人贷款不良率1.23%，均较2025 年末持平，其中关注度较高的对公房地产贷款不良率为2.13%，较上年末下降9bp，不良率整体保持平稳。从前瞻性指标来看，1Q26 末关注率与逾期率分别为1.78%、1.46%，分别较2025 年末上升3bp、上升12bp，指标有所波动，但预计整体资产质量维持稳健。1Q26 末拨备覆盖率219.59%，环比2025 年末略微下降1.29pct。\n投资建议：\n平安银行历经数年业务结构调整转型与存量不良出清，目前公司经营基本面预估已筑底企稳。同时，平安银行依托平安集团综合金融与客群渠道等多重优势，业务动能修复可期，未来业绩增长具备向上弹性。预计公司2026-2028 年归母净利润同比增长0.13%、0.85%、2.13%，维持“ 买入”评级。\n风险提示：\n1）经济增长不及预期；\n2）居民信贷需求持续低迷；\n3）海外环境不确定性上升，出口超预期下滑。"
    }
  ]
}
```

---

## 特色数据

_ST个股、指数成分股权重、除权除息、分红排行、股本变化、资金流明细、限售解禁、融资买入排行等特色数据_

### 每日ST股信息

- **函数**: `get_ch_stock_st_history`
- **说明**: 获取指定交易日ST个股列表
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 交易日期，格式：YYYY-MM-DD |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `reason` | string | 加ST/加*ST |
| `change_date` | string | 变更为ST股时间 |
| `code` | string | 个股代码 |

- **示例数据**:

```json
[
  {
    "code": "000010",
    "reason": "加*ST",
    "change_date": "2026-04-30"
  },
  {
    "code": "000016",
    "reason": "加*ST",
    "change_date": "2026-04-30"
  }
]
```

### 沪深300成分股权重

- **函数**: `get_ch_hs300_constituent_weight_history`
- **说明**: 获取沪深300指数成分股，每月权重信息。数据从2015年1月到目前，
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式如 YYYY-MM |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `weight` | number | 权重数值 |
| `code` | string | 个股代码 |
| `date` | string | 日期 |

- **示例数据**:

```json
{
  "date": "2026-05",
  "stocks": [
    {
      "code": "000001",
      "weight": 0.397
    },
    {
      "code": "000002",
      "weight": 0.09
    }
}
```

### 上证50成分股权重

- **函数**: `get_ch_sz50_constituent_weight_history`
- **说明**: 获取上证50指数成分股，每月权重信息。数据从2015年1月到目前，
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式如 YYYY-MM |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `weight` | number | 权重数值 |
| `code` | string | 个股代码 |
| `date` | string | 日期 |

- **示例数据**:

```json
{
  "date": "2026-05",
  "stocks": [
    {
      "code": "000001",
      "weight": 0.397
    },
    {
      "code": "000002",
      "weight": 0.09
    }
}
```

### 中证500成分股权重

- **函数**: `get_ch_zz500_constituent_weight_history`
- **说明**: 获取中证500指数成分股，每月权重信息。数据从2015年1月到目前，
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式 YYYY-MM |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `weight` | number | 权重数值 |
| `code` | string | 个股代码 |
| `date` | string | 日期 |

- **示例数据**:

```json
{
  "date": "2026-05",
  "stocks": [
    {
      "code": "000001",
      "weight": 0.397
    },
    {
      "code": "000002",
      "weight": 0.09
    }
}
```

### 中证1000成分股权重

- **函数**: `get_ch_zz1000_constituent_weight_history`
- **说明**: 获取中证1000指数成分股，每月权重信息。数据从2015年1月到目前，
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式  YYYY-MM |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `weight` | number | 权重数值 |
| `code` | string | 个股代码 |
| `date` | string | 日期 |

- **示例数据**:

```json
{
  "date": "2026-05",
  "stocks": [
    {
      "code": "000001",
      "weight": 0.397
    },
    {
      "code": "000002",
      "weight": 0.09
    }
}
```

### 个股除权除息历史

- **函数**: `get_ch_stock_dividend_history`
- **说明**: 获取指定个股除权除息历史
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `type` | string | 类型 1 除权除息 2 扩/缩股 3 配股调整 |
| `bonus` | number | 红利 (元) |
| `share_bonus` | number | 送股数量 |
| `allotment` | number | 配股数量 |
| `allo_price` | number | 配股价格 |
| `date` | string | 日期 |

- **示例数据**:

```json
[
  {
    "date": "1990-03-01",
    "type": 1,
    "allotment": 1,
    "allo_price": 3.56,
    "bonus": 0,
    "share_bonus": 0
  },
  {
    "date": "1991-05-02",
    "type": 1,
    "bonus": 3,
    "share_bonus": 4,
    "allotment": 0,
    "allo_price": 0
  }
]
```

### 年度高送转/分红

- **函数**: `get_ch_year_high_stock_dividend`
- **说明**: 获取自然年内所有高送转，分红派息个股数据。数据从1992年至今，每日更新数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `year` | string | 是 | 年份，如 2026 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 股票名称 |
| `capitalization_issue` | number | 转增(每10股) |
| `stock_dividend` | number | 送股(每10股) |
| `cash_dividend` | number | 派现(每10股 元) |
| `recorde_date` | number | 股权登记日 |
| `dps` | number | 每股收益(元) |
| `reps` | number | 每股未分配利润(元) |
| `crps` | number | 每股资本公积金(元) |
| `tag_date` | string | 公告日期 |
| `report_type` | string | 公告类型 |
| `code` | string | 股票代码 |

- **示例数据**:

```json
[
  {
    "code": "300741",
    "name": "华宝股份",
    "cash_dividend": 0.5,
    "recorde_date": "2026-05-19",
    "dps": 0.07,
    "reps": 1.9184,
    "crps": 7.6706,
    "tag_date": "2026-04-29",
    "report_type": "一季报",
    "capitalization_issue": 0,
    "stock_dividend": 0
  },
  {
    "code": "300760",
    "name": "迈瑞医疗",
    "cash_dividend": 12.5,
    "recorde_date": "2026-05-27",
    "dps": 1.9225,
    "reps": 26.7819,
    "crps": 4.9527,
    "tag_date": "2026-04-29",
    "report_type": "一季报",
    "capitalization_issue": 0,
    "stock_dividend": 0
  }
]
```

### 个股股本变化历史

- **函数**: `get_ch_stock_share_capital`
- **说明**: 获取指定个股每个交易日股本情况。从个股上市到今日。每日更新
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `total_shares` | string | 总股本(股) |
| `circulating_shares` | number | 流通股本(股) |
| `date` | number | 日期 |

- **示例数据**:

```json
[
  {
    "date": "1991-04-03",
    "total_shares": 48500172,
    "circulating_shares": 26500000
  },
  {
    "date": "1991-04-04",
    "total_shares": 48500172,
    "circulating_shares": 26500000
  }
]
```

### 个股资金流明细历史

- **函数**: `get_ch_stock_fund_flow_detail_history`
- **说明**: 获取指定个股历史资金流详细数据。目前数据从2010年到现在，该数据会定期更新
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `change_percent` | string | 涨跌幅(%) |
| `turnover_amount` | number | 成交额(万元) |
| `main_net_inflow` | number | 主力净流入金额(万元) |
| `main_net_inflow_ratio` | number | 主力资金净流入比率(%) |
| `super_large_buy_amount` | number | 超大单买入金额(万元) |
| `super_large_buy_volume` | number | 超大单买入量(万股) |
| `super_large_buy_avg_price` | number | 超大单买入均价(元) |
| `super_large_sell_amount` | number | 超大单卖出金额(万元) |
| `super_large_sell_volume` | number | 超大单卖出量(万股) |
| `super_large_sell_avg_price` | number | 超大单卖出均价(元) |
| `super_large_net_buy_amount` | number | 超大单净买入金额(万元) |
| `large_buy_amount` | number | 大单买入金额(万元) |
| `large_buy_volume` | number | 大单买入量(万股) |
| `large_buy_avg_price` | number | 大单买入均价(元) |
| `large_sell_amount` | number | 大单卖出金额(万元) |
| `large_sell_volume` | number | 大单卖出量(万股) |
| `large_sell_avg_price` | number | 大单卖出均价(元) |
| `large_net_buy_amount` | number | 大单净买入金额(万元) |
| `medium_buy_amount` | number | 中单买入金额(万元) |
| `medium_buy_volume` | number | 中单买入量(万股) |
| `medium_buy_avg_price` | number | 中单买入均价(元) |
| `medium_sell_amount` | number | 中单卖出金额(万元) |
| `medium_sell_volume` | number | 中单卖出量(万股) |
| `medium_sell_avg_price` | number | 中单卖出均价(元) |
| `medium_net_buy_amount` | number | 中单净买入金额(万元) |
| `small_buy_amount` | number | 小单买入金额(万元) |
| `small_buy_volume` | number | 小单买入量(万股) |
| `small_buy_avg_price` | number | 小单买入均价(元) |
| `small_sell_amount` | number | 小单卖出金额(万元) |
| `small_sell_volume` | number | 小单卖出量(万股) |
| `small_sell_avg_price` | number |  小单卖出均价(元) |
| `small_net_buy_amount` | number | 小单净买入金额(万元) |

- **示例数据**:

```json
[
  {
    "date": "2026-04-30",
    "change_percent": -0.2604,
    "turnover_amount": 131282.78,
    "main_net_inflow": 923.28,
    "main_net_inflow_ratio": 0.7,
    "super_large_buy_amount": 28592.37,
    "super_large_buy_volume": 2478.68,
    "super_large_buy_avg_price": 11.54,
    "super_large_sell_amount": 22515.23,
    "super_large_sell_volume": 1953.33,
    "super_large_sell_avg_price": 11.53,
    "super_large_net_buy_amount": 6077.14,
    "large_buy_amount": 31619.82,
    "large_buy_volume": 2742.19,
    "large_buy_avg_price": 11.53,
    "large_sell_amount": 36773.68,
    "large_sell_volume": 3190.32,
    "large_sell_avg_price": 11.53,
    "large_net_buy_amount": -5153.86,
    "medium_buy_amount": 40682.17,
    "medium_buy_volume": 3531.92,
    "medium_buy_avg_price": 11.52,
    "medium_sell_amount": 35801.13,
    "medium_sell_volume": 3106.73,
    "medium_sell_avg_price": 11.52,
    "medium_net_buy_amount": 4881.04,
    "small_buy_amount": 27955.49,
    "small_buy_volume": 2427.94,
    "small_buy_avg_price": 11.51,
    "small_sell_amount": 33759.81,
    "small_sell_volume": 2930.35,
    "small_sell_avg_price": 11.52,
    "small_net_buy_amount": -5804.32
  }
]
```

### 年度解禁数据

- **函数**: `get_ch_year_stock_lock_up`
- **说明**: 获取自然年内所有限售解禁个股信息，数据从2006年到2035年。定时更新
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `year` | string | 是 | 年份，如 2026 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 股票名称 |
| `expiration_date` | string | 解禁日期 |
| `expiration_count` | number | 解禁数量(万股) |
| `expiration_float_rate` | number | 解禁占已流通A股比例(%) |
| `expiration_total_rate` | number | 解禁占总股本比例(%) |
| `expiration_amount` | number | 解禁市值(万元) |
| `expiration_type` | string | 解禁类型 |
| `code` | string |  |

- **示例数据**:

```json
[
  {
    "code": "600654",
    "name": "中安科",
    "expiration_date": "2026-12-31",
    "expiration_count": 21196.6251,
    "expiration_float_rate": 9.146601,
    "expiration_total_rate": 7.366093,
    "expiration_amount": 83090.770392,
    "expiration_type": "延长限售锁定期流通"
  },
  {
    "code": "600212",
    "name": "绿能慧充",
    "expiration_date": "2026-12-31",
    "expiration_count": 393.5,
    "expiration_float_rate": 0.740803,
    "expiration_total_rate": 0.55883,
    "expiration_amount": 2778.11,
    "expiration_type": "股权激励限售流通"
  }
]
```

### 1日融资买入排行

- **函数**: `get_ch_rz_buy_1_day`
- **说明**: 获取近1日融资买入信息

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 股票名称 |
| `buy_amount` | number | 融资净买入(万元) |
| `rz_balance` | number | 融资余额(万元) |
| `increase` | number | 增幅(%) |
| `float_cap_percent` | number | 占流通市值比例(%) |
| `margin_balance` | number | 两融余额(万元) |
| `date` | string | 日期 |
| `code` | string | 股票代码 |

- **示例数据**:

```json
{
  "date": "2026-06-25",
  "data": [
    {
      "code": "600584",
      "name": "长电科技",
      "buy_amount": 153474.309,
      "rz_balance": 994486.727,
      "increase": 18.248756,
      "float_cap_percent": 5.33513431862,
      "margin_balance": 996356.5785
    },
    {
      "code": "688981",
      "name": "中芯国际",
      "buy_amount": 117900.4769,
      "rz_balance": 1431413.4473,
      "increase": 8.975965,
      "float_cap_percent": 4.56370852194,
      "margin_balance": 1435684.682356
    }
}
```

### 5日融资买入排行

- **函数**: `get_ch_rz_buy_5_day`
- **说明**: 获取近5日融资买入信息

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 股票名称 |
| `buy_amount` | number | 融资净买入(万元) |
| `rz_balance` | number | 融资余额(万元) |
| `increase` | number | 增幅(%) |
| `float_cap_percent` | number | 占流通市值比例(%) |
| `margin_balance` | number | 两融余额(万元) |
| `date` | string | 日期 |
| `code` | string | 股票代码 |

- **示例数据**:

```json
{
  "date": "2026-06-25",
  "data": [
    {
      "code": "600584",
      "name": "长电科技",
      "buy_amount": 277893.985,
      "rz_balance": 994486.727,
      "increase": 38.779905,
      "float_cap_percent": 5.33513431862,
      "margin_balance": 996356.5785
    },
    {
      "code": "300308",
      "name": "中际旭创",
      "buy_amount": 272655.6164,
      "rz_balance": 4575316.9261,
      "increase": 6.336906,
      "float_cap_percent": 3.11480337233,
      "margin_balance": 4590553.6273
    }
}
```

### 20日融资买入排行

- **函数**: `get_ch_rz_buy_20_day`
- **说明**: 获取近20日融资买入信息

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 股票名称 |
| `buy_amount` | number | 融资净买入(万元) |
| `rz_balance` | number | 融资余额(万元) |
| `increase` | number | 增幅(%) |
| `float_cap_percent` | number | 占流通市值比例(%) |
| `margin_balance` | number | 两融余额(万元) |
| `code` | string | 股票代码 |
| `date` | string | 日期 |

- **示例数据**:

```json
{
  "date": "2026-06-25",
  "data": [
    {
      "code": "600584",
      "name": "长电科技",
      "buy_amount": 277893.985,
      "rz_balance": 994486.727,
      "increase": 38.779905,
      "float_cap_percent": 5.33513431862,
      "margin_balance": 996356.5785
    },
    {
      "code": "300308",
      "name": "中际旭创",
      "buy_amount": 272655.6164,
      "rz_balance": 4575316.9261,
      "increase": 6.336906,
      "float_cap_percent": 3.11480337233,
      "margin_balance": 4590553.6273
    }
}
```

### 个股一致行动人信息

- **函数**: `get_ch_stock_pacs`
- **说明**: 获取A股个股一致行动人信息。一致行动人指通过协议、合作等途径扩大对上市公司表决权的一群人，数据包含一致行动组持股总量及各成员持股明细，数据从2013年至今
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `stock_code` | string | 股票代码 |
| `col_cutoff_date` | string | 截止日期 |
| `col_shareholder` | string | 股东名称 |
| `col_type` | string | 股东性质 |
| `col_group_qty` | number | 一致行动组持股数量(股) |
| `col_group_pct` | number | 一致行动组占总股本比例(%) |
| `col_group_mv` | number | 一致行动组期末参考市值(元) |
| `col_sh_qty` | number | 股东持股数量(股) |
| `col_sh_pct` | number | 股东持股占总股本比例(%) |
| `col_sh_mv` | number | 股东持股期末参考市值(元) |
| `col_sh_nature` | number | 股东股本性质 |
| `col_sh_rank` | number | 股东股东排名 |
| `col_sh_t_qty` | number | 股东持流通股数量(股) |
| `col_sh_t_pct` | number | 股东持流通股占总股本比例(%) |
| `col_sh_t_mv` | number | 股东持流通股期末参考市值(元) |
| `col_sh_t_nature` | string | 股东持流通股股本性质 |
| `col_sh_t_rank` | number | 股东持流通股股东排名 |
| `col_group_t_qty` | number | 一致行动组持流通股(股) |
| `col_group_t_pct` | number | 一致行动组持流通股占总股本比例(%) |
| `col_group_t_mv` | number | 一致行动组持流通股期末参考市值(元) |

- **示例数据**:

```json
{
  "stock_code": "000001",
  "dates": [
    {
      "col_cutoff_date": "2013-12-31",
      "data": [
        {
          "col_shareholder": "中国平安保险(集团)股份有限公司-集团本级-自有资金",
          "col_type": "保险公司",
          "col_group_qty": 5611946661,
          "col_group_pct": 68,
          "col_group_mv": 68746346597,
          "col_sh_qty": 4779077016,
          "col_sh_pct": 58,
          "col_sh_mv": 58543693446,
          "col_sh_nature": "流通A股,限售流通A股",
          "col_sh_rank": 1,
          "col_group_t_qty": 0,
          "col_group_t_pct": 0,
          "col_group_t_mv": 0,
          "col_sh_t_qty": 0,
          "col_sh_t_pct": 0,
          "col_sh_t_mv": 0,
          "col_sh_t_nature": "",
          "col_sh_t_rank": 0
        }
      ]
    }
  ]
}
```

### 市场每个交易日涨跌平数量

- **函数**: `get_ch_day_zd_count_history`
- **说明**: 返回市场历史上每个交易日上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-11",
    "sz": 1370,
    "xd": 4069,
    "pp": 72
  },
  {
    "date": "2026-06-12",
    "sz": 3923,
    "xd": 1515,
    "pp": 74
  }
]
```

### 上证A股每个交易日涨跌平数量

- **函数**: `get_ch_sh_day_zd_count_history`
- **说明**: 获取上证A股每个交易日，上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-11",
    "sz": 676,
    "xd": 1602,
    "pp": 34
  },
  {
    "date": "2026-06-12",
    "sz": 1669,
    "xd": 616,
    "pp": 26
  }
]
```

### 深圳A股每个交易日涨跌平数量

- **函数**: `get_ch_sz_day_zd_count_history`
- **说明**: 获取深圳A股每个交易日，上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
{
    "date": "2026-06-11",
    "sz": 672,
    "xd": 2171,
    "pp": 38
  },
  {
    "date": "2026-06-12",
    "sz": 2039,
    "xd": 797,
    "pp": 47
```

### 创业板每个交易日涨跌平数量

- **函数**: `get_ch_cyb_day_zd_count_history`
- **说明**: 获取创业板每个交易日，上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-11",
    "sz": 313,
    "xd": 1079,
    "pp": 3
  },
  {
    "date": "2026-06-12",
    "sz": 929,
    "xd": 447,
    "pp": 20
  }
]
```

### 科创板每个交易日涨跌平数量

- **函数**: `get_ch_kcb_day_zd_count_history`
- **说明**: 获取科创板每个交易日，上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-11",
    "sz": 224,
    "xd": 378,
    "pp": 5
  },
  {
    "date": "2026-06-12",
    "sz": 366,
    "xd": 236,
    "pp": 4
  }
]
```

### 北证每个交易日涨跌平数量

- **函数**: `get_ch_bj_day_zd_count_history`
- **说明**: 获取北证每个交易日，上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2021-11-15",
    "sz": 18,
    "xd": 59,
    "pp": 0
  },
  {
    "date": "2021-11-16",
    "sz": 7,
    "xd": 70,
    "pp": 0
  }
]
```

### 市场每个交易周涨跌平数量

- **函数**: `get_ch_week_zd_count_history`
- **说明**: 返回市场历史上每个交易周上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | string | 上涨数量 |
| `xd` | string | 下跌数量 |
| `pp` | string | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-05",
    "sz": 1884,
    "xd": 3582,
    "pp": 48
  },
  {
    "date": "2026-06-12",
    "sz": 1383,
    "xd": 4109,
    "pp": 20
  }
]
```

### 上证A股每个交易周涨跌平数量

- **函数**: `get_ch_sh_week_zd_count_history`
- **说明**: 返回上证A股历史上每个交易周上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨 |
| `xd` | number | 下跌 |
| `pp` | number | 平盘 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-05",
    "sz": 724,
    "xd": 1565,
    "pp": 22
  },
  {
    "date": "2026-06-12",
    "sz": 710,
    "xd": 1591,
    "pp": 10
  }
]
```

### 深圳A股每个交易周涨跌平数量

- **函数**: `get_ch_sz_week_zd_count_history`
- **说明**: 返回深圳A股历史上每个交易周上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-05",
    "sz": 914,
    "xd": 1947,
    "pp": 25
  },
  {
    "date": "2026-06-12",
    "sz": 639,
    "xd": 2235,
    "pp": 9
  }
]
```

### 创业板每个交易周涨跌平数量

- **函数**: `get_ch_cyb_week_zd_count_history`
- **说明**: 返回创业板历史上每个交易周上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-05",
    "sz": 486,
    "xd": 904,
    "pp": 6
  },
  {
    "date": "2026-06-12",
    "sz": 275,
    "xd": 1118,
    "pp": 3
  }
]
```

### 科创板每个交易周涨跌平数量

- **函数**: `get_ch_kcb_week_zd_count_history`
- **说明**: 返回科创板历史上每个交易周上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-05",
    "sz": 184,
    "xd": 422,
    "pp": 2
  },
  {
    "date": "2026-06-12",
    "sz": 207,
    "xd": 399,
    "pp": 0
  }
]
```

### 北证每个交易周涨跌平数量

- **函数**: `get_ch_bj_week_zd_count_history`
- **说明**: 返回北证历史上每个交易周上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-05",
    "sz": 246,
    "xd": 70,
    "pp": 1
  },
  {
    "date": "2026-06-12",
    "sz": 34,
    "xd": 283,
    "pp": 1
  }
]
```

### 市场每个交易月涨跌平数量

- **函数**: `get_ch_month_zd_count_history`
- **说明**: 返回市场历史上每个交易月上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-05-29",
    "sz": 1522,
    "xd": 3977,
    "pp": 7
  },
  {
    "date": "2026-06-12",
    "sz": 1375,
    "xd": 4120,
    "pp": 17
  }
]
```

### 上证A股每个交易月涨跌平数量

- **函数**: `get_ch_sh_month_zd_count_history`
- **说明**: 返回上证A股历史上每个交易月上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-05-29",
    "sz": 676,
    "xd": 1628,
    "pp": 3
  },
  {
    "date": "2026-06-12",
    "sz": 618,
    "xd": 1681,
    "pp": 12
  }
]
```

### 深圳A股每个交易月涨跌平数量

- **函数**: `get_ch_sz_month_zd_count_history`
- **说明**: 返回深圳A股历史上每个交易月上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-05-29",
    "sz": 801,
    "xd": 2078,
    "pp": 4
  },
  {
    "date": "2026-06-12",
    "sz": 655,
    "xd": 2223,
    "pp": 5
  }
]
```

### 创业板每个交易月涨跌平数量

- **函数**: `get_ch_cyb_month_zd_count_history`
- **说明**: 返回创业板历史上每个交易月上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
{
  "date": "2026-06-12",
  "sz": 311,
  "xd": 1082,
  "pp": 3
}
```

### 科创板每个交易月涨跌平数量

- **函数**: `get_ch_kcb_month_zd_count_history`
- **说明**: 返回科创板历史上每个交易月上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-05-29",
    "sz": 246,
    "xd": 361,
    "pp": 1
  },
  {
    "date": "2026-06-12",
    "sz": 178,
    "xd": 428,
    "pp": 0
  }
]
```

### 北证每个交易月涨跌平数量

- **函数**: `get_ch_bj_month_zd_count_history`
- **说明**: 返回北证历史上每个交易月上涨，下跌，平盘数量

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `sz` | number | 上涨数量 |
| `xd` | number | 下跌数量 |
| `pp` | number | 平盘数量 |

- **示例数据**:

```json
[
  {
    "date": "2026-05-29",
    "sz": 45,
    "xd": 271,
    "pp": 0
  },
  {
    "date": "2026-06-12",
    "sz": 102,
    "xd": 216,
    "pp": 0
  }
]
```

### 中国全社会用电量同比

- **函数**: `get_ch_electricity_use_history`
- **说明**: 返回中国全社会用电量同比历史数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `tag_date` | string | 发布日期 |
| `attache_date` | string | 数据所属月份 |
| `val` | string | 数值 |
| `pre_val` | string | 前值 |
| `except_val` | string | 预期值 |

- **示例数据**:

```json
[{'tag_date': '2026-06-18', 'attache_date': '2026-05 ', 'val': '6.9', 'pre_val': '6', 'except_val': ''}, {'tag_date': '2026-05-19', 'attache_date': '2026-04 ', 'val': '6', 'pre_val': '3.5', 'except_val': ''}, {'tag_date': '2026-04-20', 'attache_date': '2026-03 ', 'val': '3.5', 'pre_val': '', 'except_val': '
'}, {'tag_date': '2025-12-24', 'attache_date': '2025-11 ', 'val': '6.2', 'pre_val': '10.4', 'except_val': ''}]
```

### 全市场PE/PB 月数据历史

- **函数**: `get_ch_market_pe_pb_month_history`
- **说明**: 返回全市体市场PE，PB 历史数据，按月统计

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `pe` | number | 市场市盈率(不包含亏损股) |
| `pe_loss` | number | 市场市盈率(包含亏损股) |
| `pb` | number | 市场市净率 |

- **示例数据**:

```json
[{'date': '2026-07-10', 'pe': 18.46, 'pe_loss': 23.34, 'pb': 1.67}, {'date': '2026-06-30', 'pe': 19.04, 'pe_loss': 24.09, 'pb': 1.72}, {'date': '2026-05-29', 'pe': 18.9, 'pe_loss': 23.95, 'pb': 1.71}, {'date': '2026-04-30', 'pe': 18.77, 'pe_loss': 23.88, 'pb': 1.7}]
```

### 全市场PE/PB 日数据历史

- **函数**: `get_ch_market_pe_pb_day_history`
- **说明**: 返回全市体市场PE，PB 历史数据，按日统计。在增量存储中

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date` | string | 日期 |
| `pe` | number | 市场市盈率(不包含亏损股) |
| `pe_loss` | number | 市场市盈率(包含亏损股) |
| `pb` | number | 市场市净率 |

- **示例数据**:

```json
[{'date': '2026-07-10', 'pe': 18.46, 'pe_loss': 23.34, 'pb': 1.67}]
```

---

## 港股行情

_港股实时行情、指数行情、个股历史K线、指数历史K线、财务报表等港股市场数据接口_

### 订阅港股实时行情通道

- **函数**: `subscribe_hk_stock_real`
- **说明**: 订阅个股实时行情通道，通道采用全量数据推送

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 个股名称 |
| `last_close` | string | 昨日收盘价 |
| `open` | string | 今日开盘价 |
| `high` | string | 今日最高价 |
| `low` | string | 今日最低价 |
| `close` | string | 现价 |
| `amount` | string | 成交额（万元） |
| `change` | string | 涨跌幅 |
| `volume` | string | 成交量(手) |
| `time` | string | 时间 |

### 获取港股实时行情

- **函数**: `get_hk_stock_real`
- **说明**: 获取全量港股个股实时行情数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 个股名称 |
| `last_close` | string | 昨日收盘价 |
| `open` | string | 今日开盘价 |
| `high` | string | 今日最高价 |
| `low` | string | 今日最低价 |
| `close` | string | 现价 |
| `amount` | string | 成交额（万元） |
| `change` | string | 涨跌幅 |
| `volume` | string | 成交量(手) |
| `time` | string | 时间 |

### 订阅港股指数实时行情通道

- **函数**: `subscribe_hk_market_real`
- **说明**: 订阅指数实时行情通道，通道采用全量数据推送。包括恒生指数，恒生中企指数，恒生科技指数，恒生红筹指数

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 指数名称 |
| `last_close` | string | 昨日收盘价 |
| `open` | string | 今日开盘价 |
| `high` | string | 今日最高价 |
| `low` | string | 今日最低价 |
| `close` | string | 现价 |
| `amount` | string | 成交额（万元） |
| `change` | string | 涨跌幅 |
| `date` | string | 日期 |
| `time` | string | 时间 |

### 获取港股指数实时行情

- **函数**: `get_hk_market_real`
- **说明**: 获取所有指数实时行情数据。包括恒生指数，恒生中企指数，恒生科技指数，恒生红筹指数

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 指数名称 |
| `last_close` | string | 昨日收盘价 |
| `open` | string | 今日开盘价 |
| `high` | string | 今日最高价 |
| `low` | string | 今日最低价 |
| `close` | string | 现价 |
| `amount` | string | 成交额（万元） |
| `change` | string | 涨跌幅 |
| `date` | string | 日期 |
| `time` | string | 时间 |

### 港股股票列表

- **函数**: `get_hk_stock`
- **说明**: 获取所有个股基础信息

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `code` | string | 个股代码 |
| `total_shares` | string | 总股本(股) |
| `time_to_market` | string | 上市日期 |

### 港股个股历史日线

- **函数**: `get_hk_stock_day_history`
- **说明**: 获取指定个股日线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股个股代码，如 00700.HK |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | string | 开盘价 |
| `high` | string | 最高价 |
| `low` | string | 最低价 |
| `last_close` | string | 昨收价 |
| `volume` | string | 成交量(股) |
| `amount` | string | 成交额(万元) |
| `date` | string | 日期 |

### 港股个股历史周线

- **函数**: `get_hk_stock_week_history`
- **说明**: 获取指定个股周线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股个股代码，如 00700.HK |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | string | 开盘价 |
| `high` | string | 最高价 |
| `low` | string | 最低价 |
| `last_close` | string | 昨收价 |
| `volume` | string | 成交量(股) |
| `amount` | string | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | string | 周内交易天数 |

### 港股个股历史月线

- **函数**: `get_hk_stock_month_history`
- **说明**: 获取指定个股月线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股个股代码，如 00700.HK |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | string | 开盘价 |
| `high` | string | 最高价 |
| `low` | string | 最低价 |
| `last_close` | string | 昨收价 |
| `volume` | string | 成交量(股) |
| `amount` | string | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | string | 周内交易天数 |

### 港股指数历史日线

- **函数**: `get_hk_market_history`
- **说明**: 获取指数日线数据，目前支持获取恒生指数，恒生中企指数，恒生科技指数，恒生红筹指数
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股指数代码，如 HSI |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | string | 开盘价 |
| `high` | string | 最高价 |
| `low` | string | 最低价 |
| `last_close` | string | 昨收价 |
| `volume` | string | 成交量(股) |
| `amount` | string | 成交额(万元) |
| `date` | string | 日期 |

### 港股指数历史周线

- **函数**: `get_hk_market_week_history`
- **说明**: 获取指数周线数据，目前支持获取恒生指数，恒生中企指数，恒生科技指数，恒生红筹指数
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股指数代码，如 HSI |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | string | 开盘价 |
| `high` | string | 最高价 |
| `low` | string | 最低价 |
| `last_close` | string | 昨收价 |
| `volume` | string | 成交量(股) |
| `amount` | string | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | string | 周内交易天数 |

### 港股指数历史月线

- **函数**: `get_hk_market_month_history`
- **说明**: 获取指数月线数据，目前支持获取恒生指数，恒生中企指数，恒生科技指数，恒生红筹指数
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股指数代码，如 HSI |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | string | 开盘价 |
| `high` | string | 最高价 |
| `low` | string | 最低价 |
| `last_close` | string | 昨收价 |
| `volume` | string | 成交量(股) |
| `amount` | string | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | string | 周内交易天数 |

### 港股主要财务指标

- **函数**: `get_hk_stock_main_fin_data`
- **说明**: 获取指定个股历史主要财务指标数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股个股代码，如 00700.HK |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `diluted_eps` | string | 稀释每股收益(元) |
| `ttm_eps` | string | TTM每股收益(元) |
| `bvps` | string | 每股净资产(元) |
| `ops_cash_per_share` | string | 每股经营现金流(元) |
| `ops_rev_per_share` | string | 每股营业收入(元) |
| `total_revenue` | string | 营业总收入(元) |
| `revenue_yoy` | string | 营业总收入同比增长(%) |
| `revenue_qoq` | string | 营业总收入滚动环比增长(%) |
| `gross_profit` | string | 毛利润(元) |
| `gp_yoy` | string | 毛利润同比增长(%) |

### 港股资产负债表

- **函数**: `get_hk_stock_balance_sheet`
- **说明**: 获取指定个股资产负债表历史
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股个股代码，如 00700.HK |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `investment_property` | string | 投资物业 |
| `intangible_assets` | string | 无形资产 |
| `land_use_rights` | string | 土地使用权 |
| `construction_in_progress` | string | 在建工程 |
| `deferred_tax_assets` | string | 递延所得税资产 |
| `prepayments_other_assets` | string | 预付款项、按金及其他资产 |
| `investment_in_associates` | string | 于联营公司的投资 |
| `investment_in_joint_ventures` | string | 于合营公司的投资 |
| `fvtpl_financial_assets` | string | 指定以公允价值记账之金融资产 |
| `time_deposits` | string | 定期存款 |

### 港股利润表

- **函数**: `get_hk_stock_profit_statement`
- **说明**: 获取指定个股利润表历史
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股个股代码，如 00700.HK |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `report_type` | string | 报告类型 |
| `turnover` | string | 营业额 |
| `other_revenue` | string | 其他收入 |
| `total_revenue` | string | 总收入 |
| `cost_of_revenue` | string | 收入成本 |
| `gross_profit` | string | 毛利 |
| `other_income_loss_net` | string | 其他收益/(亏损)净额 |
| `sales_marketing_expenses` | string | 销售及市场推广开支 |
| `general_admin_expenses` | string | 一般及行政开支 |
| `operating_profit` | string | 经营盈利 |

### 港股现金流表

- **函数**: `get_hk_stock_cash_flow`
- **说明**: 获取指定个股现金流表历史
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 港股个股代码，如 00700.HK |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `report_type` | string | 报告类型 |
| `profit_before_tax_subtotal` | string | 除税前溢利小计 |
| `interest_income` | string | 利息收入 |
| `interest_and_related_expenses` | string | 利息及相关开支 |
| `dividend_income` | string | 股息收入 |
| `share_of_associates_jv_profit_loss` | string | 分占联营公司及合营公司的(盈利)/亏损净额 |
| `impairment_loss` | string | 无形资产、土地使用权、使用权资产、投资物业以及物业、设备及器材的减值净额 |
| `fv_gain_loss` | string | 以公允价值计量且其变动计入损益的金融资产及其他金融工具的公允价值收益净额 |
| `gain_on_disposal_of_assets` | string | 减:出售资产之溢利 |
| `depreciation_amortization` | string | 加:折旧及摊销 |

---

## 个股数据

### 获取股票列表

- **函数**: `get_ch_stock`
- **说明**: 获取所有A股个股信息列表

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 股票名称 |
| `total_shares` | number | 总股本(股) |
| `circulating_shares` | number | 流通股本(股) |
| `time_to_market` | string | 上市日期 |
| `belong_hs300` | number | 是否属于沪深300 1 属于  0  不属于 |
| `belong_rzrq` | number | 是否属于融资融券标的 1 属于  0  不属于 |
| `belong_hsgt` | number | 是否属于沪深股通 1 属于  0  不属于 |
| `is_st` | number | 是否是ST股票 1 属于  0  不属于 |
| `code` | string | 股票代码 |

- **示例数据**:

```json
{
  "300001": {
    "name": "特锐德",
    "code": "300001",
    "total_shares": 1055537700,
    "circulating_shares": 1026828500,
    "time_to_market": "2009-10-30",
    "belong_rzrq": 1,
    "belong_hsgt": 1,
    "belong_hs300": 0,
    "is_st": 0
  },
  "300002": {
    "name": "神州泰岳",
    "code": "300002",
    "total_shares": 1967173900,
    "circulating_shares": 1851049100,
    "time_to_market": "2009-10-30",
    "belong_rzrq": 1,
    "belong_hsgt": 1,
    "belong_hs300": 0,
    "is_st": 0
  }
}
```

### 订阅实时行情通道

- **函数**: `subscribe_ch_stock_real`
- **说明**: 订阅个股实时行情通道，采用增量发送模式，数据在交易时段实时推送。返回五档盘口、成交量、换手率、市值、市盈率等核心指标。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 数据时间，格式 yyyy-MM-dd HH:mm:ss |
| `close` | number | 当前价（元） |
| `open` | number | 开盘价（元） |
| `high` | number | 最高价（元） |
| `low` | number | 最低价（元） |
| `last_close` | number | 上个交易日收盘价（元） |
| `amount` | number | 成交额（元） |
| `volume` | number | 成交量（手） |
| `pre_volume` | number | 前成交量（手） |
| `buy_five` | list | 买五档价格 |
| `buy_five_vol` | list | 买五档量 |
| `sell_five` | list | 卖五档价格 |
| `sell_five_vol` | list | 卖五档量 |
| `turnover` | number | 换手率（%） |
| `volume_ratio` | number | 量比 |
| `bid_ask_ratio` | number | 委比（%） |
| `market_cap` | number | 总市值（元） |
| `float_cap` | number | 流通市值（元） |
| `dynamic_pe` | number | 动态市盈率 |
| `static_pe` | number | 静态市盈率 |
| `pb` | number | 市净率 |

- **示例数据**:

```json
{'301578': {'time': '2026-07-01 15:00:04', 'close': 20.55, 'open': 20.38, 'high': 20.86, 
'low': 19.94, 'last_close': 20.39, 'amount': 29170200.0, 'volume': 14284, 'pre_volume': 1428377, 'buy_five': [20.55, 20.54, 20.53, 20.5, 20.48], 'buy_five_vol': [13, 96, 500, 77, 6], 'sell_five': [20.58, 20.59, 20.6, 20.61, 20.62], 'sell_five_vol': [16, 31, 16, 44, 2], 'turnover': 4.74, 'volume_ratio': 1.18
, 'bid_ask_ratio': 72.78, 'market_cap': 2177000000.0, 'float_cap': 619000000.0, 'dynamic_pe': -124.08, 'static_pe': 166.21, 'pb': 2.34}}
```

### 获取所有个股实时行情

- **函数**: `get_ch_stock_real`
- **说明**: 随时获取全量A股实时行情数据，返回所有个股的最新价、涨跌幅、成交量、盘口、市值等核心指标。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 数据时间，格式 yyyy-MM-dd HH:mm:ss |
| `close` | number | 当前价（元） |
| `open` | number | 开盘价（元） |
| `high` | number | 最高价（元） |
| `low` | number | 最低价（元） |
| `last_close` | number | 上个交易日收盘价（元） |
| `amount` | number | 成交额（元） |
| `volume` | number | 成交量（手） |
| `pre_volume` | number | 前成交量（手） |
| `buy_five` | list | 买五档价格 |
| `buy_five_vol` | list | 买五档量 |
| `sell_five` | list | 卖五档价格 |
| `sell_five_vol` | list | 卖五档量 |
| `turnover` | number | 换手率（%） |
| `volume_ratio` | number | 量比 |
| `bid_ask_ratio` | number | 委比（%） |
| `market_cap` | number | 总市值（元） |
| `float_cap` | number | 流通市值（元） |
| `dynamic_pe` | number | 动态市盈率 |
| `static_pe` | number | 静态市盈率 |
| `pb` | number | 市净率 |

- **示例数据**:

```json
{'301578': {'time': '2026-07-01 15:00:04', 'close': 20.55, 'open': 20.38, 'high': 20.86, 
'low': 19.94, 'last_close': 20.39, 'amount': 29170200.0, 'volume': 14284, 'pre_volume': 1428377, 'buy_five': [20.55, 20.54, 20.53, 20.5, 20.48], 'buy_five_vol': [13, 96, 500, 77, 6], 'sell_five': [20.58, 20.59, 20.6, 20.61, 20.62], 'sell_five_vol': [16, 31, 16, 44, 2], 'turnover': 4.74, 'volume_ratio': 1.18
, 'bid_ask_ratio': 72.78, 'market_cap': 2177000000.0, 'float_cap': 619000000.0, 'dynamic_pe': -124.08, 'static_pe': 166.21, 'pb': 2.34}}
```

### 获取单只个股实时行情

- **函数**: `get_ch_one_stock_real`
- **说明**: 查询单只个股实时行情，返回数据中包含该股的Level2大单数据、竞价金额、成交量涨速、委托情况等增强指标。
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001.SZ |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 数据时间 |
| `close` | number | 当前价（元） |
| `open` | number | 开盘价（元） |
| `high` | number | 最高价（元） |
| `low` | number | 最低价（元） |
| `last_close` | number | 上个交易日收盘价（元） |
| `amount` | number | 成交额（元） |
| `volume` | number | 成交量（手） |
| `pre_volume` | number | 前成交量（手） |
| `buy_five` | list | 买五档价格 |
| `buy_five_vol` | list | 买五档量 |
| `sell_five` | list | 卖五档价格 |
| `sell_five_vol` | list | 卖五档量 |
| `turnover` | number | 换手率（%） |
| `volume_ratio` | number | 量比 |
| `bid_ask_ratio` | number | 委比（%） |
| `market_cap` | number | 总市值（元） |
| `float_cap` | number | 流通市值（元） |
| `dynamic_pe` | number | 动态市盈率 |
| `static_pe` | number | 静态市盈率 |
| `pb` | number | 市净率 |
| `action_amount` | number | 当日竞价成交金额（万元） |
| `pre_action_amount` | number | 昨日竞价成交金额（万元） |
| `l2_vol_rise_speed` | number | 成交量涨速 |
| `l2_total_buy_vol` | number | 买入委托总量 |
| `l2_total_sell_vol` | number | 卖出委托总量 |
| `l2_buy_cancel` | number | 撤销的买入委托总量 |
| `l2_sell_cancel` | number | 撤销的卖出委托总量 |
| `l2_deal_tick_num` | integer | 成交笔数 |
| `l2_order_tick_num` | integer | 委托笔数 |

- **示例数据**:

```json
{
  "time": "2026-07-01 15:00:04",
  "close": 10.16,
  "open": 10.05,
  "high": 10.18,
  "low": 9.99,
  "last_close": 10.05,
  "amount": 915838500,
  "volume": 906890,
  "pre_volume": 90688982,
  "buy_five": [
    10.15,
    10.14,
    10.13,
    10.12,
    10.11
  ],
  "buy_five_vol": [
    6308,
    2428,
    2108,
    2627,
    1147
  ],
  "sell_five": [
    10.16,
    10.17,
    10.18,
    10.19,
    10.2
  ],
  "sell_five_vol": [
    2078,
    6037,
    15339,
    8841,
    12588
  ],
  "turnover": 0.47,
  "volume_ratio": 0.8,
  "bid_ask_ratio": -50.86,
  "market_cap": 197164000000,
  "float_cap": 197161000000,
  "dynamic_pe": 3.39,
  "static_pe": 4.53,
  "pb": 0.42,
  "action_amount": 707.12,
  "pre_action_amount": 246.92,
  "l2_vol_rise_speed": 0.61,
  "l2_total_buy_vol": 127978,
  "l2_total_sell_vol": 168492,
  "l2_buy_cancel": 440845,
  "l2_sell_cancel": 289299,
  "l2_deal_tick_num": 72479,
  "l2_order_tick_num": 130559
}
```

### 个股实时分钟K线

- **函数**: `get_ch_stock_minute_real`
- **说明**: 获取个股当日实时分钟成交数据，支持1分钟、5分钟、15分钟、30分钟、60分钟周期。该接口仅在交易时段有效。
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001.SZ |
| `minute` | integer | 是 | 分钟周期，可选值：1, 5, 15, 30, 60 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `date_time` | string | 日期时间 |
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `close` | number | 收盘价 |
| `amount` | number | 成交额（元） |
| `volume` | number | 成交量（手） |

- **示例数据**:

```json
[
  {
    "date_time": "2026-05-26 09:31:00",
    "open": 12.35,
    "high": 12.38,
    "low": 12.33,
    "close": 12.36,
    "amount": 1250000,
    "volume": 1000
  }
]
```

### 个股实时逐笔成交

- **函数**: `get_ch_stock_transaction_real`
- **说明**: 获取个股交易当天实时逐笔成交明细数据，包含时间、价格、成交量及买卖方向。该接口仅在交易时段有效。
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001.SZ |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 成交时间 |
| `price` | number | 成交价格 |
| `volume` | number | 成交量（手） |
| `buy_or_sell` | integer | 买卖方向：0=买盘，1=卖盘 |

- **示例数据**:

```json
[
  {
    "time": "14:58:03",
    "price": 12.35,
    "volume": 100,
    "buy_or_sell": 0
  },
  {
    "time": "14:58:05",
    "price": 12.36,
    "volume": 200,
    "buy_or_sell": 1
  }
]
```

### 前复权日线

- **函数**: `get_ch_stock_front_day_history`
- **说明**: 获取指定个股前复权日线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": -2.87,
    "open": -2.87,
    "high": -2.87,
    "low": -2.87,
    "last_close": -2.71,
    "volume": 100,
    "amount": 0.49,
    "date": "1991-04-03"
  },
  {
    "close": -2.87,
    "open": -2.87,
    "high": -2.87,
    "low": -2.87,
    "last_close": -2.87,
    "volume": 300,
    "amount": 1.5,
    "date": "1991-04-04"
  }
]
```

### 前复权周线

- **函数**: `get_ch_stock_front_week_history`
- **说明**: 获取指定个股前复权周线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | number | 周内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": -2.87,
    "open": -2.87,
    "high": -2.87,
    "low": -2.87,
    "last_close": -2.71,
    "volume": 600,
    "amount": 2.99,
    "date": "1991-04-05",
    "trading_days": 3
  },
  {
    "close": -2.89,
    "open": -2.88,
    "high": -2.88,
    "low": -2.89,
    "last_close": -2.87,
    "volume": 2900,
    "amount": 13.8,
    "date": "1991-04-12",
    "trading_days": 4
  }
]
```

### 前复权月线

- **函数**: `get_ch_stock_front_month_history`
- **说明**: 获取指定个股前复权月线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | number | 月内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": -2.93,
    "open": -2.87,
    "high": -2.87,
    "low": -2.93,
    "last_close": -2.71,
    "volume": 11700,
    "amount": 53.49,
    "date": "1991-04-30",
    "trading_days": 17
  },
  {
    "close": -2.8,
    "open": -2.72,
    "high": -2.72,
    "low": -2.8,
    "last_close": -2.93,
    "volume": 176000,
    "amount": 719.47,
    "date": "1991-05-31",
    "trading_days": 21
  }
]
```

### 后复权日线

- **函数**: `get_ch_stock_back_day_history`
- **说明**: 获取指定个股后复权日线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 49,
    "open": 49,
    "high": 49,
    "low": 49,
    "last_close": 61.49,
    "volume": 100,
    "amount": 0.49,
    "date": "1991-04-03"
  },
  {
    "close": 48.76,
    "open": 48.76,
    "high": 48.76,
    "low": 48.76,
    "last_close": 49,
    "volume": 300,
    "amount": 1.5,
    "date": "1991-04-04"
  }
]
```

### 后复权周线

- **函数**: `get_ch_stock_back_week_history`
- **说明**: 获取指定个股后复权周线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | number | 周内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 48.52,
    "open": 49,
    "high": 49,
    "low": 48.52,
    "last_close": 61.49,
    "volume": 600,
    "amount": 2.99,
    "date": "1991-04-05",
    "trading_days": 3
  },
  {
    "close": 47.08,
    "open": 48.04,
    "high": 48.04,
    "low": 47.08,
    "last_close": 48.52,
    "volume": 2900,
    "amount": 13.8,
    "date": "1991-04-12",
    "trading_days": 4
  }
]
```

### 后复权月线

- **函数**: `get_ch_stock_back_month_history`
- **说明**: 获取指定个股后复权月线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | number | 月内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 43.68,
    "open": 49,
    "high": 49,
    "low": 43.68,
    "last_close": 61.49,
    "volume": 11700,
    "amount": 53.49,
    "date": "1991-04-30",
    "trading_days": 17
  },
  {
    "close": 53.98,
    "open": 61.14,
    "high": 61.14,
    "low": 53.98,
    "last_close": 43.69,
    "volume": 176000,
    "amount": 719.47,
    "date": "1991-05-31",
    "trading_days": 21
  }
]
```

### 历史分笔

- **函数**: `get_ch_stock_transaction_history`
- **说明**: 获取指定个股历史分笔个数。按照年份加月份进行查询
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001.SZ |
| `year` | string | 是 | 年份 |
| `month` | string | 是 | 月份，为1-12的整数 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `price` | number | 价格 |
| `volume` | number | 成交量 |
| `buy_or_sell` | number | 买卖方向  0 买盘  1 卖盘 |
| `time` | string | 时间 |

- **示例数据**:

```json
{
  "2026-01-05": [
    {
      "time": "14:16",
      "price": 11.49,
      "volume": 205,
      "buy_or_sell": 1
    },
    {
      "time": "14:16",
      "price": 11.49,
      "volume": 15,
      "buy_or_sell": 1
    },
    {
      "time": "14:16",
      "price": 11.5,
      "volume": 14,
      "buy_or_sell": 0
    }
  ]
}
```

### 主力评分数据

- **函数**: `get_ch_stock_primer_info`
- **说明**: 获取指定个股主力成本及相关评分数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `score_change` | number | 评分较上一日变动 |
| `stock_rank` | number | 评分打败股票比例 |
| `score_msg` | string | 评分总结文字 |
| `tomorrow_up_percent` | number | 次日上涨概率 |
| `tomorrow_avg_zf` | number | 次日平均涨幅 |
| `tomorrow_cal_count` | number | 次日信息计算样本数量 |
| `next_five_up_percent` | number | 后5日上涨概率 |
| `next_five_avg_zf` | number | 后5日均涨幅 |
| `next_five_cal_count` | number | 后5日信息计算样本数量 |
| `score_history` | list | 评分历史数据 |

- **示例数据**:

```json
{
  "total_score": 69.08,
  "score_change": 4.75,
  "stock_rank": 90.07,
  "score_msg": "近期消息面活跃，主力资金有介入迹象，短期呈现震荡趋势，市场关注意愿一般。",
  "tomorrow_up_percent": 43.14,
  "tomorrow_avg_zf": 0.13,
  "tomorrow_cal_count": 5480,
  "next_five_up_percent": 43.81,
  "next_five_avg_zf": -0.17,
  "next_five_cal_count": 4789,
  "score_history": [
    {
      "date": "2026-02-27",
      "score": 58.34,
      "price": 10.9
    },
    {
      "date": "2026-03-02",
      "score": 59.14,
      "price": 10.85
    }
  ]
}
```

### 个股资金流

- **函数**: `get_ch_stock_fund_flow`
- **说明**: 获取指定个股历史资金流，该数据每日盘后更新
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `primer_amount_ratio` | number | 主力净流入占比 |
| `xl_order_net_amount` | number | 超大单净额(元) |
| `xl_order_amount_ratio` | number | 超大单净额占比 |
| `big_order_net_amount` | number | 大单净额(元) |
| `big_order_amount_ratio` | number | 大单净额占比 |
| `medium_order_net_amount` | number | 中单净额(元) |
| `medium_order_amount_ratio` | number | 中单净额占比 |
| `small_order_net_amount` | number | 小单净额(元) |
| `small_order_amount_ratio` | number | 小单净额占比 |
| `primer_net_amount` | number | 主力净流入(元) |

- **示例数据**:

```json
{
  "2025-11-14": {
    "primer_net_amount": 128244752,
    "primer_amount_ratio": 8.26,
    "xl_order_net_amount": 194619136,
    "xl_order_amount_ratio": 12.54,
    "big_order_net_amount": -66374384,
    "big_order_amount_ratio": -4.28,
    "medium_order_net_amount": -102424528,
    "medium_order_amount_ratio": -6.6,
    "small_order_net_amount": -25820235,
    "small_order_amount_ratio": -1.66
  },
  "2026-05-19": {
    "primer_net_amount": -41708781,
    "primer_amount_ratio": -4.84,
    "xl_order_net_amount": 13295991,
    "xl_order_amount_ratio": 1.54,
    "big_order_net_amount": -55004772,
    "big_order_amount_ratio": -6.38,
    "medium_order_net_amount": 44602382,
    "medium_order_amount_ratio": 5.17,
    "small_order_net_amount": -2893606,
    "small_order_amount_ratio": -0.34
  }
}
```

### 人气排名数据

- **函数**: `get_ch_stock_attention_tank`
- **说明**: 获取个股历史交易日内，在市场以及行业内人气排名数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `market_rank` | number | 全市场人气排名 |
| `classified_rank` | number | 行业内人气排名 |
| `date` | string | 日期 |

- **示例数据**:

```json
[
  {
    "date": "2020-12-28",
    "market_rank": 28,
    "classified_rank": 1
  },
  {
    "date": "2020-12-29",
    "market_rank": 24,
    "classified_rank": 1
  }
]
```

### 股东人数历史

- **函数**: `get_ch_stock_share_holder`
- **说明**: 获取个股历史股东人数变化数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `holder_count` | string | 股东人数(户) |
| `date` | string | 日期 |

- **示例数据**:

```json
[
  {
    "date": "1997-12-31",
    "holder_count": "833471"
  },
  {
    "date": "1998-06-30",
    "holder_count": "918331"
  }
]
```

### 大宗交易历史

- **函数**: `get_ch_stock_block_trading`
- **说明**: 获取个股历史大宗交易数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `price` | number | 成交价 |
| `amount` | number | 成交金额(万元) |
| `date` | string | 日期 |

- **示例数据**:

```json
[
  {
    "date": "2012-08-09",
    "price": 15.04,
    "amount": 326.82
  },
  {
    "date": "2012-09-11",
    "price": 14.02,
    "amount": 491.82
  }
]
```

### 增减持历史

- **函数**: `get_ch_stock_inc_or_dec`
- **说明**: 获取个股增减持历史数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `price` | number | 成交均价，如未披露价格，该值为0 |
| `count` | number | 增减持数量(股)，负数表示减持 |
| `date` | string | 日期 |

- **示例数据**:

```json
[
  {
    "date": "2007-07-09",
    "price": 27.9,
    "count": "1600"
  },
  {
    "date": "2009-08-19",
    "price": 21.04,
    "count": "46200"
  }
]
```

### 等比前复权日线

- **函数**: `get_ch_stock_front_ratio_history`
- **说明**: 获取指定个股等比前复权日线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 0.46,
    "open": 0.46,
    "high": 0.46,
    "low": 0.46,
    "last_close": 61.49,
    "volume": 100,
    "amount": 0.49,
    "date": "1991-04-03"
  },
  {
    "close": 0.45,
    "open": 0.45,
    "high": 0.45,
    "low": 0.45,
    "last_close": 49,
    "volume": 300,
    "amount": 1.5,
    "date": "1991-04-04"
  }
]
```

### 等比前复权周线

- **函数**: `get_ch_stock_front_ratio_week_history`
- **说明**: 获取指定个股前复权周线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | number | 日期 |
| `trading_days` | string | 周内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 0.45,
    "open": 0.46,
    "high": 0.46,
    "low": 0.45,
    "last_close": 61.49,
    "volume": 600,
    "amount": 2.99,
    "date": "1991-04-05",
    "trading_days": 3
  },
  {
    "close": 0.44,
    "open": 0.45,
    "high": 0.45,
    "low": 0.44,
    "last_close": 48.52,
    "volume": 2900,
    "amount": 13.8,
    "date": "1991-04-12",
    "trading_days": 4
  }
]
```

### 等比前复权月线

- **函数**: `get_ch_stock_front_ratio_month_history`
- **说明**: 获取指定个股等比前复权月线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | number | 月内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 0.41,
    "open": 0.46,
    "high": 0.46,
    "low": 0.41,
    "last_close": 61.49,
    "volume": 11700,
    "amount": 53.49,
    "date": "1991-04-30",
    "trading_days": 17
  },
  {
    "close": 0.5,
    "open": 0.57,
    "high": 0.57,
    "low": 0.5,
    "last_close": 30.99,
    "volume": 176000,
    "amount": 719.47,
    "date": "1991-05-31",
    "trading_days": 21
  }
]
```

### 等比后复权日线

- **函数**: `get_ch_stock_back_ratio_history`
- **说明**: 获取指定个股等比后复权日线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 49,
    "open": 49,
    "high": 49,
    "low": 49,
    "last_close": 61.49,
    "volume": 100,
    "amount": 0.49,
    "date": "1991-04-03"
  },
  {
    "close": 48.76,
    "open": 48.76,
    "high": 48.76,
    "low": 48.76,
    "last_close": 49,
    "volume": 300,
    "amount": 1.5,
    "date": "1991-04-04"
  }
]
```

### 历史分钟数据

- **函数**: `get_ch_stock_minute_history`
- **说明**: 获取指定个股历史分钟数据。按照年份加月份进行查询
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |
| `minute` | string | 是 | 分钟数，可指定1,5,15,30,60 |
| `date` | string | 是 | 年月字符串，格式为 20263 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `close` | number | 收盘价 |
| `amount` | number | 成交额 |
| `volume` | number | 成交量 |
| `date_time` | string |  日期时间 |

- **示例数据**:

```json
[
  {
    "date_time": "2026-06-01 09:35",
    "open": 10.9,
    "high": 10.91,
    "low": 10.81,
    "close": 10.83,
    "amount": 119599670,
    "volume": 11021500
  }
]
```

---

## 板块数据

### 获取概念板块列表

- **函数**: `get_ch_concept`
- **说明**: 获取A股概念板块列表

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 板块名称 |
| `stocks` | list | 成分股股票代码列表 |
| `code` | string | 概念板块对应的代码 |

- **示例数据**:

```json
{
  "880502.SH": {
    "name": "含B股",
    "code": "880502.SH",
    "stocks": [
      "000011",
      "000012",
      "000016",
      "000017",
      "000019",
      "000020",
      "000025",
      "000026",
      "000028",
      "000029",
      "000030",
      "000037"
    ]
  }
}
```

### 获取行业板块列表

- **函数**: `get_ch_industry`
- **说明**: 获取A股概念板块列表

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 板块名称 |
| `stocks` | list | 成分股股票代码列表 |
| `code` | string | 行业板块代码 |

- **示例数据**:

```json
{
  "881071.SH": {
    "name": "工业金属",
    "code": "881071.SH",
    "stocks": [
      "000060",
      "000426",
      "000612",
      "000630",
      "000688",
      "000737",
      "000751"
    ]
  }
}
```

### 订阅概念板块实时行情通道

- **函数**: `subscribe_ch_concept_real`
- **说明**: 订阅概念板块实时行情通道，全量推送所有概念板块的实时数据，包括涨跌幅、成交量、成分股涨跌数量统计等。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `code` | string | 板块代码 |
| `name` | string | 板块名称 |
| `last_close` | number | 昨日收盘价 |
| `open` | number | 今日开盘价 |
| `high` | number | 今日最高价 |
| `close` | number | 现价 |
| `low` | number | 最低价 |
| `volume` | number | 成交量（手） |
| `amount` | number | 成交额（万元） |
| `change` | number | 涨跌幅（%） |
| `date` | string | 日期 |
| `time` | string | 时间 |
| `up_count` | integer | 上涨数量 |
| `down_count` | integer | 下跌数量 |
| `limit_up_count` | integer | 涨停数量 |
| `limit_down_count` | integer | 跌停数量 |

- **示例数据**:

```json
{
  "880575.SH": {
    "code": "880575.SH",
    "name": "地热能",
    "last_close": 2798.08,
    "open": 2806.4,
    "high": 2844.42,
    "low": 2796.39,
    "close": 2844.42,
    "volume": 9028825,
    "amount": 1082951.6,
    "change": 1.66,
    "date": "2026-07-01",
    "time": "15:00:00",
    "up_count": 15,
    "down_count": 5,
    "limit_up_count": 0,
    "limit_down_count": 0
  },
  "880661.SH": {
    "code": "880661.SH",
    "name": "6G概念",
    "last_close": 2701.19,
    "open": 2708.4,
    "high": 2745,
    "low": 2674.4,
    "close": 2692.97,
    "volume": 43580504,
    "amount": 20788280,
    "change": -0.3,
    "date": "2026-07-01",
    "time": "15:00:00",
    "limit_up_count": 2,
    "up_count": 50,
    "down_count": 46,
    "limit_down_count": 0
  }
}
```

### 获取概念板块实时行情

- **函数**: `get_ch_concept_real`
- **说明**: 随时获取所有概念板块实时行情数据，包括板块涨跌幅、成交量、成分股涨跌统计等关键指标。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `code` | string | 板块代码 |
| `name` | string | 板块名称 |
| `last_close` | number | 昨日收盘价 |
| `open` | number | 今日开盘价 |
| `high` | number | 今日最高价 |
| `close` | number | 现价 |
| `low` | number | 最低价 |
| `volume` | number | 成交量（手） |
| `amount` | number | 成交额（万元） |
| `change` | number | 涨跌幅（%） |
| `date` | string | 日期 |
| `time` | string | 时间 |
| `up_count` | integer | 上涨数量 |
| `down_count` | integer | 下跌数量 |
| `limit_up_count` | integer | 涨停数量 |
| `limit_down_count` | integer | 跌停数量 |

- **示例数据**:

```json
{
  "880575.SH": {
    "code": "880575.SH",
    "name": "地热能",
    "last_close": 2798.08,
    "open": 2806.4,
    "high": 2844.42,
    "low": 2796.39,
    "close": 2844.42,
    "volume": 9028825,
    "amount": 1082951.6,
    "change": 1.66,
    "date": "2026-07-01",
    "time": "15:00:00",
    "up_count": 15,
    "down_count": 5,
    "limit_up_count": 0,
    "limit_down_count": 0
  },
  "880661.SH": {
    "code": "880661.SH",
    "name": "6G概念",
    "last_close": 2701.19,
    "open": 2708.4,
    "high": 2745,
    "low": 2674.4,
    "close": 2692.97,
    "volume": 43580504,
    "amount": 20788280,
    "change": -0.3,
    "date": "2026-07-01",
    "time": "15:00:00",
    "limit_up_count": 2,
    "up_count": 50,
    "down_count": 46,
    "limit_down_count": 0
  }
}
```

### 订阅行业板块实时行情通道

- **函数**: `subscribe_ch_industry_real`
- **说明**: 订阅行业板块实时行情通道，全量推送所有行业板块的实时数据，包括涨跌幅、成交量、成分股涨跌数量统计等。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `code` | string | 板块代码 |
| `name` | string | 板块名称 |
| `last_close` | number | 昨日收盘价 |
| `open` | number | 今日开盘价 |
| `high` | number | 今日最高价 |
| `close` | number | 现价 |
| `low` | number | 最低价 |
| `volume` | number | 成交量（手） |
| `amount` | number | 成交额（万元） |
| `change` | number | 涨跌幅（%） |
| `date` | string | 日期 |
| `time` | string | 时间 |
| `up_count` | integer | 上涨数量 |
| `down_count` | integer | 下跌数量 |
| `limit_up_count` | integer | 涨停数量 |
| `limit_down_count` | integer | 跌停数量 |

- **示例数据**:

```json
{
  "880575.SH": {
    "code": "880575.SH",
    "name": "地热能",
    "last_close": 2798.08,
    "open": 2806.4,
    "high": 2844.42,
    "low": 2796.39,
    "close": 2844.42,
    "volume": 9028825,
    "amount": 1082951.6,
    "change": 1.66,
    "date": "2026-07-01",
    "time": "15:00:00",
    "up_count": 15,
    "down_count": 5,
    "limit_up_count": 0,
    "limit_down_count": 0
  },
  "880661.SH": {
    "code": "880661.SH",
    "name": "6G概念",
    "last_close": 2701.19,
    "open": 2708.4,
    "high": 2745,
    "low": 2674.4,
    "close": 2692.97,
    "volume": 43580504,
    "amount": 20788280,
    "change": -0.3,
    "date": "2026-07-01",
    "time": "15:00:00",
    "limit_up_count": 2,
    "up_count": 50,
    "down_count": 46,
    "limit_down_count": 0
  }
}
```

### 获取行业板块实时行情

- **函数**: `get_ch_industry_real`
- **说明**: 随时获取所有行业板块实时行情数据，包括板块涨跌幅、成交量、成分股涨跌统计等关键指标。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `code` | string | 板块代码 |
| `name` | string | 板块名称 |
| `last_close` | number | 昨日收盘价 |
| `open` | number | 今日开盘价 |
| `high` | number | 今日最高价 |
| `close` | number | 现价 |
| `low` | number | 最低价 |
| `volume` | number | 成交量（手） |
| `amount` | number | 成交额（万元） |
| `change` | number | 涨跌幅（%） |
| `date` | string | 日期 |
| `time` | string | 时间 |
| `up_count` | integer | 上涨数量 |
| `down_count` | integer | 下跌数量 |
| `limit_up_count` | integer | 涨停数量 |
| `limit_down_count` | integer | 跌停数量 |

- **示例数据**:

```json
{
  "880575.SH": {
    "code": "880575.SH",
    "name": "地热能",
    "last_close": 2798.08,
    "open": 2806.4,
    "high": 2844.42,
    "low": 2796.39,
    "close": 2844.42,
    "volume": 9028825,
    "amount": 1082951.6,
    "change": 1.66,
    "date": "2026-07-01",
    "time": "15:00:00",
    "up_count": 15,
    "down_count": 5,
    "limit_up_count": 0,
    "limit_down_count": 0
  },
  "880661.SH": {
    "code": "880661.SH",
    "name": "6G概念",
    "last_close": 2701.19,
    "open": 2708.4,
    "high": 2745,
    "low": 2674.4,
    "close": 2692.97,
    "volume": 43580504,
    "amount": 20788280,
    "change": -0.3,
    "date": "2026-07-01",
    "time": "15:00:00",
    "limit_up_count": 2,
    "up_count": 50,
    "down_count": 46,
    "limit_down_count": 0
  }
}
```

### 概念板块日线

- **函数**: `get_ch_concept_day_history`
- **说明**: 获取概念版块日线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 板块代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 223.13,
    "open": 223.56,
    "high": 231.59,
    "low": 219.85,
    "last_close": 223.56,
    "volume": 1920105,
    "amount": 143121.31,
    "date": "2005-06-07"
  }
]
```

### 概念板块周线

- **函数**: `get_ch_concept_week_history`
- **说明**: 获取概念板块周线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 概念板块代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | number | 周内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 237.03,
    "open": 223.56,
    "high": 247.92,
    "low": 219.85,
    "last_close": 223.56,
    "volume": 10442151,
    "amount": 724003.6,
    "date": "2005-06-10",
    "trading_days": 4
  }
]
```

### 概念板块月线

- **函数**: `get_ch_concept_month_history`
- **说明**: 获取概念板块月线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 概念板块代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | number | 周内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 219.66,
    "open": 223.56,
    "high": 247.92,
    "low": 216.05,
    "last_close": 223.56,
    "volume": 29823504,
    "amount": 1947223.5,
    "date": "2005-06-30",
    "trading_days": 18
  }
]
```

### 行业板块日线

- **函数**: `get_ch_industry_day_history`
- **说明**: 获取行业版块日线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 板块代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 1314.48,
    "open": 1305.84,
    "high": 1331.8,
    "low": 1297.06,
    "last_close": 1305.84,
    "volume": 19466352,
    "amount": 2231496,
    "date": "2011-01-04"
  }
]
```

### 行业板块周线

- **函数**: `get_ch_industry_week_history`
- **说明**: 获取行业板块周线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 行业板块代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | number | 周内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 1272.62,
    "open": 1305.84,
    "high": 1331.8,
    "low": 1267.08,
    "last_close": 1305.84,
    "volume": 53458176,
    "amount": 5734948,
    "date": "2011-01-07",
    "trading_days": 4
  }
]
```

### 行业板块月线

- **函数**: `get_ch_industry_month_history`
- **说明**: 获取行业板块月线数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 行业板块代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `trading_days` | number | 周内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
{
  "close": 1177.46,
  "open": 1305.84,
  "high": 1331.8,
  "low": 1101.76,
  "last_close": 1305.84,
  "volume": 189639020,
  "amount": 17898436,
  "date": "2011-01-31",
  "trading_days": 20
}
```

---

## 市场数据

### 获取融资融券余额

- **函数**: `get_rzrq_balance`
- **说明**: 获取融资融券余额历史数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `rz_balance` | number | 融资余额(万元) |
| `rq_balance` | number | 融券余额(万元) |
| `dae` | string | 日期 |

- **示例数据**:

```json
[
  {
    "date": "2026-04-13",
    "rz_balance": 261160450,
    "rq_balance": 1913146.6
  }
]
```

### 上交所每日统计信息

- **函数**: `get_sh_market_daily_info`
- **说明**: 获取上海证券交易所每日统计信息，包括上证A股，上证B股，科创板等。包含总成交量，成交额，换手率，pe等信息
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式 2026-03-01 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `a_stock` | dict | 上证A股 |
| `b_stock` | dict | 上证B股 |
| `kcb_stock` | dict | 科创板 |
| `market` | dict | 上交所总体 |
| `date` | string | 日期 |
| `total_value` | number | 总市值(亿元) |
| `trade_vol` | number | 成交量(亿股) |
| `avg_pe` | number | 平均市盈率(倍) |
| `total_to_rate` | number | 换手率(%) |
| `nego_to_rate` | number | 流通换手率(%) |
| `trade_amt` | number | 成交金额(亿元) |
| `nego_value` | number | 流通市值(亿元) |
| `list_num` | number | 股票数 |

- **示例数据**:

```json
{
  "date": "2026-06-01",
  "a_stock": {
    "total_value": 541203.56,
    "trade_vol": 616.24,
    "avg_pe": 14.28,
    "total_to_rate": 1.6563,
    "nego_to_rate": 1.726,
    "trade_amt": 8963.72,
    "nego_value": 519349.97,
    "list_num": 1705
  },
  "b_stock": {
    "total_value": 1022.29,
    "trade_vol": 0.41,
    "avg_pe": 10.52,
    "total_to_rate": 0.1596,
    "nego_to_rate": 0.23,
    "trade_amt": 1.63,
    "nego_value": 709.22,
    "list_num": 41
  },
  "kcb_stock": {
    "total_value": 133436.66,
    "trade_vol": 59.69,
    "avg_pe": 91.38,
    "total_to_rate": 3.1754,
    "nego_to_rate": 3.8966,
    "trade_amt": 4237.1,
    "nego_value": 108738.96,
    "list_num": 610
  },
  "market": {
    "total_value": 675662.56,
    "trade_vol": 676.34,
    "avg_pe": 16.62,
    "total_to_rate": 1.954,
    "nego_to_rate": 2.0996,
    "trade_amt": 13202.46,
    "nego_value": 628798.1,
    "list_num": 2356
  }
}
```

### 上交所每周统计信息

- **函数**: `get_sh_market_week_info`
- **说明**: 获取上海证券交易所每周统计信息，包括上证A股，上证B股，科创板等。包含总成交量，成交额，换手率，pe等信息
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式 2026-03-01 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `a_stock` | dict | 上证A股 |
| `b_stock` | dict | 上证B股 |
| `kcb_stock` | dict | 科创板 |
| `market` | dict | 上交所总体 |
| `begin_date` | string | 周起始日期 |
| `end_date` | string | 周结束日期 |
| `low_vol` | number | 最低成交量(亿股) |
| `low_vol_date` | string | 最低成交量日期 |
| `low_amt` | number | 最低成交金额(亿元) |
| `low_amt_date` | number | 最低成交金额日期 |
| `avg_pe_rate` | number | 平均市盈率(倍) |
| `trade_amt` | number | 成交金额(亿元) |
| `list_num` | number | 股票数量 |
| `high_amt` | number | 最高成交金额(亿元) |
| `high_amt_date` | string | 最高成交金额日期 |
| `high_vol` | number | 最高成交量(亿股) |
| `high_vol_date` | string | 最高成交量日期 |
| `total_value` | number | 市价总值(亿元) |
| `trade_vol` | number | 成交量(亿股) |
| `total_to_rate` | number | 换手率(%) |
| `nego_value` | number | 流通市值(亿元) |
| `trade_days` | number | 交易天数 |
| `to_rate` | number | 流通换手率(%) |

- **示例数据**:

```json
{
  "begin_date": "2026-06-01",
  "end_date": "2026-06-07",
  "a_stock": {
    "low_vol": 568.9223,
    "low_vol_date": "2026-06-04",
    "low_amt": 8909.455,
    "low_amt_date": "2026-06-04",
    "avg_pe_rate": 14.12,
    "trade_amt": 46171.992,
    "list_num": 1705,
    "high_amt": 9775.991,
    "high_amt_date": "2026-06-03",
    "high_vol": 616.2396,
    "high_vol_date": "2026-06-01",
    "total_value": 534770.1,
    "trade_vol": 2986.259,
    "total_to_rate": 8.5598,
    "nego_value": 513204.75,
    "trade_days": 5,
    "to_rate": 8.9187
  },
  "b_stock": {
    "low_vol": 0.2962,
    "low_vol_date": "2026-06-04",
    "low_amt": 1.2996,
    "low_amt_date": "2026-06-04",
    "avg_pe_rate": 10.31,
    "trade_amt": 7.4464,
    "list_num": 41,
    "high_amt": 1.6315,
    "high_amt_date": "2026-06-01",
    "high_vol": 0.4083,
    "high_vol_date": "2026-06-01",
    "total_value": 1001.97,
    "trade_vol": 1.7395,
    "total_to_rate": 0.7371,
    "nego_value": 702.55,
    "trade_days": 5,
    "to_rate": 1.0545
  },
  "kcb_stock": {
    "low_vol": 53.7142,
    "low_vol_date": "2026-06-02",
    "low_amt": 3763.98,
    "low_amt_date": "2026-06-02",
    "avg_pe_rate": 93.46,
    "trade_amt": 20578.74,
    "list_num": 610,
    "high_amt": 4541.6836,
    "high_amt_date": "2026-06-03",
    "high_vol": 60.8215,
    "high_vol_date": "2026-06-05",
    "total_value": 136156.77,
    "trade_vol": 286.7599,
    "total_to_rate": 15.0703,
    "nego_value": 110340.44,
    "trade_days": 5,
    "to_rate": 18.5485
  },
  "market": {
    "low_vol": 623.0451,
    "low_vol_date": "2026-06-04",
    "low_amt": 12779.428,
    "low_amt_date": "2026-06-04",
    "avg_pe_rate": 16.53,
    "trade_amt": 66758.18,
    "list_num": 2356,
    "high_amt": 14319.174,
    "high_amt_date": "2026-06-03",
    "high_vol": 676.3412,
    "high_vol_date": "2026-06-01",
    "total_value": 671928.9,
    "trade_vol": 3274.7583,
    "total_to_rate": 9.8605,
    "nego_value": 624247.75,
    "trade_days": 5,
    "to_rate": 10.6067
  },
  "query_date": ""
}
```

### 上交所每月统计信息

- **函数**: `get_sh_market_month_info`
- **说明**: 获取上海证券交易所每月统计信息，包括上证A股，上证B股，科创板等。包含总成交量，成交额，换手率，pe等信息
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 月份，格式 2026-03 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `a_stock` | dict | 上证A股 |
| `b_stock` | dict | 上证B股 |
| `kcb_stock` | dict | 科创板 |
| `market` | dict | 上交所总体 |
| `query_date` | string | 查询日期 |
| `low_vol` | number | 最低成交量(亿股) |
| `low_vol_date` | string | 最低成交量日期 |
| `low_amt` | number | 最低成交金额(亿元) |
| `low_amt_date` | string | 最低成交金额日期 |
| `avg_pe_rate` | number | 平均市盈率(倍) |
| `trade_amt` | number | 成交金额(亿元) |
| `list_num` | number | 股票数量 |
| `high_amt` | number | 最高成交金额(亿元) |
| `high_amt_date` | number | 最高成交金额日期 |
| `high_vol` | number | 最高成交量(亿股) |
| `high_vol_date` | string | 最高成交量日期 |
| `total_value` | number | 市价总值(亿元) |
| `trade_vol` | number | 成交量(亿股) |
| `total_to_rate` | number | 换手率(%) |
| `nego_value` | number | 流通市值(亿元) |
| `trade_days` | number | 交易天数 |
| `to_rate` | number | 流通换手率(%) |

- **示例数据**:

```json
{
  "query_date": "2026-04",
  "a_stock": {
    "low_vol": 441.6343,
    "low_vol_date": "2026-04-07",
    "low_amt": 5323.584,
    "low_amt_date": "2026-04-03",
    "avg_pe_rate": 15.06,
    "trade_amt": 153713.39,
    "list_num": 1703,
    "high_amt": 9115.964,
    "high_amt_date": "2026-04-23",
    "high_vol": 621.6485,
    "high_vol_date": "2026-04-23",
    "total_value": 552636.94,
    "trade_vol": 11123.024,
    "total_to_rate": 28.0521,
    "nego_value": 531155.94,
    "trade_days": 21,
    "to_rate": 29.1939
  },
  "b_stock": {
    "low_vol": 0.1732,
    "low_vol_date": "2026-04-07",
    "low_amt": 0.845,
    "low_amt_date": "2026-04-20",
    "avg_pe_rate": 10.98,
    "trade_amt": 31.6279,
    "list_num": 41,
    "high_amt": 3.0529,
    "high_amt_date": "2026-04-24",
    "high_vol": 0.5038,
    "high_vol_date": "2026-04-24",
    "total_value": 1026.23,
    "trade_vol": 6.2076,
    "total_to_rate": 3.2869,
    "nego_value": 725.54,
    "trade_days": 21,
    "to_rate": 4.5329
  },
  "kcb_stock": {
    "low_vol": 32.2002,
    "low_vol_date": "2026-04-07",
    "low_amt": 1817.175,
    "low_amt_date": "2026-04-03",
    "avg_pe_rate": 81.02,
    "trade_amt": 59004.1,
    "list_num": 609,
    "high_amt": 4077.219,
    "high_amt_date": "2026-04-30",
    "high_vol": 62.4691,
    "high_vol_date": "2026-04-30",
    "total_value": 127648.32,
    "trade_vol": 951.5772,
    "total_to_rate": 50.5823,
    "nego_value": 104455.61,
    "trade_days": 21,
    "to_rate": 61.1503
  },
  "market": {
    "low_vol": 474.0076,
    "low_vol_date": "2026-04-07",
    "low_amt": 7141.9023,
    "low_amt_date": "2026-04-03",
    "avg_pe_rate": 16.97,
    "trade_amt": 212749.12,
    "list_num": 2353,
    "high_amt": 12770.297,
    "high_amt_date": "2026-04-30",
    "high_vol": 672.3541,
    "high_vol_date": "2026-04-23",
    "total_value": 681311.5,
    "trade_vol": 12080.81,
    "total_to_rate": 31.9693,
    "nego_value": 636337.06,
    "trade_days": 21,
    "to_rate": 34.1131
  }
}
```

### 订阅指数实时行情通道

- **函数**: `subscribe_ch_market_real`
- **说明**: 订阅指数实时行情通道，全量推送上证指数、深证成指、创业板指、科创综指、科创50、北证50的实时行情数据。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `code` | string | 指数代码 |
| `name` | string | 指数名称 |
| `last_close` | number | 昨日收盘价 |
| `open` | number | 今日开盘价 |
| `high` | number | 今日最高价 |
| `close` | number | 现价 |
| `low` | number | 最低价 |
| `volume` | number | 成交量（手） |
| `amount` | number | 成交额（万元） |
| `change` | number | 涨跌幅（%） |
| `date` | string | 日期 |
| `time` | string | 时间 |
| `up_count` | number | 上涨数量 |
| `down_count` | number | 下跌数量 |

- **示例数据**:

```json
{'899050': {'code': '899050', 'name': '北证50', 'last_close': 1264.94, 'open': 1244.51, 'high': 1268.52, 'low': 1241.89, 'close': 1265.23, 'volume': 3317399.0, 'amount': 811691.75, 'change': 0.02, 'date': '2026-07-02', 'time': '09:59:42', 'up_c
ount': 253, 'down_count': 68}}
```

### 获取指数实时行情

- **函数**: `get_ch_market_real`
- **说明**: 随时获取六大指数（上证指数、深证成指、创业板指、科创综指、科创50、北证50）的实时行情数据。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `code` | string | 指数代码 |
| `name` | string | 指数名称 |
| `last_close` | number | 昨日收盘价 |
| `open` | number | 今日开盘价 |
| `high` | number | 今日最高价 |
| `close` | number | 现价 |
| `low` | number | 最低价 |
| `volume` | number | 成交量（手） |
| `amount` | number | 成交额（万元） |
| `change` | number | 涨跌幅（%） |
| `date` | string | 日期 |
| `time` | string | 时间 |
| `up_count` | integer | 上涨数量 |
| `down_count` | integer | 下跌数量 |

- **示例数据**:

```json
{'899050': {'code': '899050', 'name': '北证50', 'last_close': 1264.94, 'open': 1244.51, 'high': 1268.52, 'low': 1241.89, 'close': 1265.23, 'volume': 3317399.0, 'amount': 811691.75, 'change': 0.02, 'date': '2026-07-02', 'time': '09:59:42', 'up_c
ount': 253, 'down_count': 68}}
```

### 涨跌停数量历史

- **函数**: `get_ch_limit_up_down`
- **说明**: 获取交易日涨跌停数量历史数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `limit_up` | number | 涨停数量 |
| `limit_down` | number | 跌停数量 |
| `touch_limit_up` | number | 触及涨停数量 |
| `touch_limit_down` | number | 触及跌停数量 |
| `limit_up_percent` | number | 涨停封板率 |
| `limit_down_percent` | number | 跌停封板率 |
| `date` | string | 日期 |

- **示例数据**:

```json
[
  {
    "date": "2026-06-11",
    "limit_up": 69,
    "touch_limit_up": 44,
    "limit_down": 55,
    "touch_limit_down": 31,
    "limit_up_percent": 61.06,
    "limit_down_percent": 63.95
  }
]
```

### 指数日线

- **函数**: `get_ch_market_day_history`
- **说明**: 获取指数日线数据，目前支持获取上证指数， 深证成指，创业板指，科创综指，科创50，北证50
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 指数代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | string | 日期 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 223.13,
    "open": 223.56,
    "high": 231.59,
    "low": 219.85,
    "last_close": 223.56,
    "volume": 1920105,
    "amount": 143121.31,
    "date": "2005-06-07"
  }
]
```

### 指数周线

- **函数**: `get_ch_market_week_history`
- **说明**: 获取指定指数周线数据，目前支持获取上证指数， 深证成指，创业板指，科创综指，科创50，北证50
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 指数代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | number | 日期 |
| `trading_days` | string | 周内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 237.03,
    "open": 223.56,
    "high": 247.92,
    "low": 219.85,
    "last_close": 223.56,
    "volume": 10442151,
    "amount": 724003.6,
    "date": "2005-06-10",
    "trading_days": 4
  }
]
```

### 指数月线

- **函数**: `get_ch_market_month_history`
- **说明**: 获取指定指数月线数据，目前支持获取上证指数， 深证成指，创业板指，科创综指，科创50，北证50
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 指数代码 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `open` | number | 开盘价 |
| `high` | number | 最高价 |
| `low` | number | 最低价 |
| `last_close` | number | 昨收价 |
| `volume` | number | 成交量(股) |
| `amount` | number | 成交额(万元) |
| `date` | number | 日期 |
| `trading_days` | string | 周内交易天数 |
| `close` | number | 收盘价 |

- **示例数据**:

```json
[
  {
    "close": 219.66,
    "open": 223.56,
    "high": 247.92,
    "low": 216.05,
    "last_close": 223.56,
    "volume": 29823504,
    "amount": 1947223.5,
    "date": "2005-06-30",
    "trading_days": 18
  }
]
```

### 龙虎榜数据

- **函数**: `get_lhb_data`
- **说明**: 获取指定日期龙虎榜数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `date` | string | 是 | 日期，格式 2026-03-01 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 个股名称 |
| `code` | string | 个股代码 |
| `lhb_net_amount` | number | 龙虎榜净买额(元) |
| `lhb_buy_amount` | number | 龙虎榜买入额(元) |
| `lhb_sell_amount` | number | 龙虎榜卖出额(元) |
| `lhb_deal_amount` | number | 龙虎榜成交额(元) |
| `amount` | number | 今日总成交额 |
| `net_amount_ratio` | number | 净买额占成交额比例 |
| `deal_amount_ratio` | number | 龙虎榜成交金额占总成交额比例 |
| `reason` | string | 上榜原因 |
| `buy_seat` | list | 买入席位信息 |
| `sell_seat` | list | 卖出席位信息 |
| `buy_seat.name` | string | 席位名称 |
| `buy_seat.buy_amount` | number | 席位买入金额(元) |
| `buy_seat.buy_amount_ratio` | number | 席位买入金额占总成交额比例 |
| `buy_seat.sell_amount` | number | 席位卖出金额(元) |
| `buy_seat.sell_amount_ratio` | number | 席位卖出金额占总成交额比例 |
| `buy_seat.net_amount` | number | 席位净额(元) |

- **示例数据**:

```json
[{'name': '国华退', 'code': '000004', 'lhb_net_amount': 284993.4, 'lhb_buy_amount': 638369.4, 'lhb_sell_amount': 353376.0, 'lhb_deal_amount': 991745.4, 'amount': 815800.0, 'net_amount_ratio': 34.934224074528, 'deal_amount_ratio': 121.5672223584
21, 'reason': '退市整理期', 'buy_seat': [{'name': '广发证券股份有限公司南京泰山路证券营业部', 'buy_amount': 235144.0, 'buy_amount_ratio': 28.82, 'net_amount': 235144.0, 'sell_amount': 0.0, 'sell_amount_ratio': 0.0}, {'name': '东方财富证券股份有
公司拉萨东环路第二证券营业部', 'buy_amount': 204511.4, 'buy_amount_ratio': 25.07, 'sell_amount': 4114.0, 'sell_amount_ratio': 0.5, 'net_amount': 200397.4}]
```

### 市场资金流历史

- **函数**: `get_ch_market_fund_flow`
- **说明**: 获取市场总体资金流历史数据

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `xl_order_net_amount` | number | 超大单净额(元) |
| `big_order_net_amount` | number | 大单净额(元) |
| `medium_order_net_amount` | number | 中单净额(元) |
| `small_order_net_amount` | number | 小单净额(元) |
| `primer_amount_ratio` | number | 主力净流入占比 |
| `xl_order_amount_ratio` | number | 超大单净额占比 |
| `big_order_amount_ratio` | number | 大单净额占比 |
| `medium_order_amount_ratio` | number | 中单净额占比 |
| `small_order_amount_ratio` | number | 小单净额占比 |
| `primer_net_amount` | number | 主机净额 |

- **示例数据**:

```json
{'2025-12-08': {'primer_net_amount': -666746880.0, 'primer_amount_ratio': -0.03, 'xl_order_net_amount'
: 9857163264.0, 'xl_order_amount_ratio': 0.48, 'big_order_net_amount': -10523910144.0, 'big_order_amount_ratio': -0.52, 'medium_order_net_amount': -7577845760.0, 'medium_order_amount_ratio': -0.37, 'small_order_net_amount': 8244592640.0, 'small
_order_amount_ratio': 0.4}, '2026-01-28': {'primer_net_amount': -43598020608.0, 'primer_amount_ratio': -1.47, 'xl_order_net_amount': -18492960768.0, 'xl_order_amount_ratio': -0.62, 'big_order_net_amount': -25105059840.0, 'big_order_amount_ratio': -0.85, 'medium_order_net_amount': 3970121728.0, 'medium_order_amount_ratio': 0.13, 'small_order_net_amount': 39627902976.0, 'small_order_amount_ratio': 1.34}}
```

### 全市场买卖对比

- **函数**: `get_ch_all_market_bear_compare`
- **说明**: 全市场全天买一，卖一金额对比

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `tradetime` | string | 时间 |
| `bid` | number | 买一金额 |
| `ask` | number | 卖一金额 |

- **示例数据**:

```json
[{'tradetime': '09:38:02', 'bid': 8640666444.82, 'ask': 1484923560.13}, {'tradetime': '09:37:01', 'bid': 9081330313.37, 'ask': 1485783183.51}, {'tradetime': '09:36:02', 'bid': 79975
32781.0, 'ask': 1441054958.25}, {'tradetime': '09:35:02', 'bid': 7547271071.83, 'ask': 1483705759.97}, {'tradetime': '09:34:02', 'bid': 7229564611.41, 'ask': 1529772167.34}, {'tradetime': '09:33:02', 'bid': 5585810515.91, 'ask': 1420520280.8}, {'tradetime': '09:32:02', 'bid': 5481907868.66, 'ask': 1226396727.59}, {'tradetime': '09:31:01', 'bid': 5648826744.47, 'ask': 1372673423.56}, {'tradetime': '09:30:03', 'bid': 7541239872.54, 'ask': 1845408777.78}]
```

### 上证买卖对比

- **函数**: `get_ch_sh_market_bear_compare`
- **说明**: 上海市场全天买一，卖一金额对比

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `tradetime` | string | 时间 |
| `bid` | number | 买一金额 |
| `ask` | number | 卖一金额 |

- **示例数据**:

```json
[{'tradetime': '09:38:02', 'bid': 8640666444.82, 'ask': 1484923560.13}, {'tradetime': '09:37:01', 'bid': 9081330313.37, 'ask': 1485783183.51}, {'tradetime': '09:36:02', 'bid': 79975
32781.0, 'ask': 1441054958.25}, {'tradetime': '09:35:02', 'bid': 7547271071.83, 'ask': 1483705759.97}, {'tradetime': '09:34:02', 'bid': 7229564611.41, 'ask': 1529772167.34}, {'tradetime': '09:33:02', 'bid': 5585810515.91, 'ask': 1420520280.8}, {'tradetime': '09:32:02', 'bid': 5481907868.66, 'ask': 1226396727.59}, {'tradetime': '09:31:01', 'bid': 5648826744.47, 'ask': 1372673423.56}, {'tradetime': '09:30:03', 'bid': 7541239872.54, 'ask': 1845408777.78}]
```

### 深证买卖对比

- **函数**: `get_ch_sz_market_bear_compare`
- **说明**: 深圳市场全天买一，卖一金额对比

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `tradetime` | string | 时间 |
| `bid` | number | 买一金额 |
| `ask` | number | 卖一金额 |

- **示例数据**:

```json
[{'tradetime': '09:38:02', 'bid': 8640666444.82, 'ask': 1484923560.13}, {'tradetime': '09:37:01', 'bid': 9081330313.37, 'ask': 1485783183.51}, {'tradetime': '09:36:02', 'bid': 79975
32781.0, 'ask': 1441054958.25}, {'tradetime': '09:35:02', 'bid': 7547271071.83, 'ask': 1483705759.97}, {'tradetime': '09:34:02', 'bid': 7229564611.41, 'ask': 1529772167.34}, {'tradetime': '09:33:02', 'bid': 5585810515.91, 'ask': 1420520280.8}, {'tradetime': '09:32:02', 'bid': 5481907868.66, 'ask': 1226396727.59}, {'tradetime': '09:31:01', 'bid': 5648826744.47, 'ask': 1372673423.56}, {'tradetime': '09:30:03', 'bid': 7541239872.54, 'ask': 1845408777.78}]
```

### 创业板买卖对比

- **函数**: `get_ch_cyb_market_bear_compare`
- **说明**: 创业板全天买一，卖一金额对比

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `tradetime` | string | 时间 |
| `bid` | number | 买一金额 |
| `ask` | number | 卖一金额 |

- **示例数据**:

```json
[{'tradetime': '09:38:02', 'bid': 8640666444.82, 'ask': 1484923560.13}, {'tradetime': '09:37:01', 'bid': 9081330313.37, 'ask': 1485783183.51}, {'tradetime': '09:36:02', 'bid': 79975
32781.0, 'ask': 1441054958.25}, {'tradetime': '09:35:02', 'bid': 7547271071.83, 'ask': 1483705759.97}, {'tradetime': '09:34:02', 'bid': 7229564611.41, 'ask': 1529772167.34}, {'tradetime': '09:33:02', 'bid': 5585810515.91, 'ask': 1420520280.8}, {'tradetime': '09:32:02', 'bid': 5481907868.66, 'ask': 1226396727.59}, {'tradetime': '09:31:01', 'bid': 5648826744.47, 'ask': 1372673423.56}, {'tradetime': '09:30:03', 'bid': 7541239872.54, 'ask': 1845408777.78}]
```

### 科创板买卖对比

- **函数**: `get_ch_kcb_market_bear_compare`
- **说明**: 科创板全天买一，卖一金额对比

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `tradetime` | string | 时间 |
| `bid` | number | 买一金额 |
| `ask` | number | 卖一金额 |

- **示例数据**:

```json
[{'tradetime': '09:38:02', 'bid': 8640666444.82, 'ask': 1484923560.13}, {'tradetime': '09:37:01', 'bid': 9081330313.37, 'ask': 1485783183.51}, {'tradetime': '09:36:02', 'bid': 79975
32781.0, 'ask': 1441054958.25}, {'tradetime': '09:35:02', 'bid': 7547271071.83, 'ask': 1483705759.97}, {'tradetime': '09:34:02', 'bid': 7229564611.41, 'ask': 1529772167.34}, {'tradetime': '09:33:02', 'bid': 5585810515.91, 'ask': 1420520280.8}, {'tradetime': '09:32:02', 'bid': 5481907868.66, 'ask': 1226396727.59}, {'tradetime': '09:31:01', 'bid': 5648826744.47, 'ask': 1372673423.56}, {'tradetime': '09:30:03', 'bid': 7541239872.54, 'ask': 1845408777.78}]
```

### 北证买卖对比

- **函数**: `get_ch_bj_market_bear_compare`
- **说明**: 北证全天买一，卖一金额对比

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `tradetime` | string | 时间 |
| `bid` | number | 买一金额 |
| `ask` | number | 卖一金额 |

- **示例数据**:

```json
[{'tradetime': '09:38:02', 'bid': 8640666444.82, 'ask': 1484923560.13}, {'tradetime': '09:37:01', 'bid': 9081330313.37, 'ask': 1485783183.51}, {'tradetime': '09:36:02', 'bid': 79975
32781.0, 'ask': 1441054958.25}, {'tradetime': '09:35:02', 'bid': 7547271071.83, 'ask': 1483705759.97}, {'tradetime': '09:34:02', 'bid': 7229564611.41, 'ask': 1529772167.34}, {'tradetime': '09:33:02', 'bid': 5585810515.91, 'ask': 1420520280.8}, {'tradetime': '09:32:02', 'bid': 5481907868.66, 'ask': 1226396727.59}, {'tradetime': '09:31:01', 'bid': 5648826744.47, 'ask': 1372673423.56}, {'tradetime': '09:30:03', 'bid': 7541239872.54, 'ask': 1845408777.78}]
```

---

## 财务数据

### 利润表

- **函数**: `get_ch_stock_income_statement`
- **说明**: 获取指定个股利润表历史数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `net_profit_adjusted` | number | 扣除非经常性损益后的净利润 |
| `tag_time` | number | 报告期 |
| `net_profit_minority` | number | 少数股东损益 |
| `basic_eps` | number | 基本每股收益 |
| `me` | number | 综合收益总额 |
| `adjusted_eps` | number | 扣除非经常性损益每股收益 |
| `operating_revenue` | number | 营业收入 |
| `comprehensive_income` | number | 归属于母公司综合收益 |
| `operating_costs` | number | 营业成本 |
| `announce_time` | number | 营业税金及附加 |
| `sales_expenses` | number | sales_expenses |
| `management_expenses` | number | 管理费用 |
| `financial_expenses` | number | 财务费用 |
| `rd_expenses` | number | 研发费用 |
| `other_gains` | number | 其他收益 |
| `investment_income` | number | 投资收益 |
| `fair_value_gain_loss` | number | 公允价值变动损益 |
| `asset_impairment_loss` | number | 资产减值损失 |
| `credit_impairment_loss` | number | 信用减值损失 |
| `asset_disposal_gain_loss` | number | 资产处置收益 |
| `operating_profit` | number | 营业利润 |
| `non_operating_income` | number | 营业外收入 |
| `total_profit` | number | 利润总额 |
| `income_tax_expense` | number | 所得税费用 |
| `net_profit` | number | 净利润 |
| `net_profit_attributable_parent` | number | 归属于母公司所有者的净利润 |
| `other_comprehensive_income` | number | 其他综合收益 |
| `total_comprehensive_income` | number | 综合收益总额 |
| `comprehensive_income_parent` | number | 归属于母公司综合收益 |
| `comprehensive_income_minority` | number | 归属于少数股东综合收益 |
| `diluted_eps` | number | 稀释每股收益 |
| `operating_revenue_ttm` | number | 营业总收入TTM |
| `operating_revenue_single_quarter` | number | 营业总收入(单季度) |
| `net_profit_single_quarter` | number | 净利润（单季度） |
| `operating_costs_single_quarter` | number | 营业成本（单季度） |
| `interest_income` | number | 利息收入 |
| `premium_earned` | number | 已赚保费 |
| `commission_income` | number | 手续费及佣金收入 |
| `interest_expense` | number | 利息支出 |
| `commission_expense` | number | 手续费及佣金支出 |
| `surrender_value` | number | 退保金 |
| `net_claims_expense` | number | 赔付支出净额 |
| `net_insurance_contract_reserve` | number | 提取保险合同准备金净额 |
| `policy_dividend_expense` | number | 保单红利支出 |
| `reinsurance_expense` | number | 分保费用 |
| `exchange_gain_loss` | number | 汇兑收益 |
| `net_fair_value_hedge_gain` | number | 净敞口套期收益 |
| `other_business_income` | number | 其他业务收入 |
| `business_management_expenses` | number | 业务及管理费 |
| `other_business_costs` | number | 其他业务成本 |

- **示例数据**:

```json
[
  {
    "announce_time": "19901231",
    "tag_time": "19901231",
    "basic_eps": 1.46,
    "adjusted_eps": 0,
    "operating_revenue": 0,
    "operating_costs": 0,
    "operating_expenses": 0,
    "sales_expenses": 0,
    "management_expenses": 0,
    "financial_expenses": 0,
    "rd_expenses": 0,
    "other_gains": 0,
    "investment_income": 0,
    "fair_value_gain_loss": 0,
    "asset_impairment_loss": 0,
    "credit_impairment_loss": 0,
    "asset_disposal_gain_loss": 0,
    "operating_profit": 0,
    "non_operating_income": 0,
    "non_operating_expenses": 0,
    "total_profit": 0,
    "income_tax_expense": 0,
    "net_profit": 0,
    "net_profit_attributable_parent": 0,
    "net_profit_adjusted": 0,
    "net_profit_minority": 0,
    "other_comprehensive_income": 0,
    "total_comprehensive_income": 0,
    "comprehensive_income_parent": 0,
    "comprehensive_income_minority": 0,
    "diluted_eps": 0,
    "operating_revenue_ttm": 0,
    "operating_revenue_single_quarter": 0,
    "net_profit_single_quarter": 0,
    "operating_costs_single_quarter": 0,
    "interest_income": 0,
    "premium_earned": 0,
    "commission_income": 0,
    "interest_expense": 0,
    "commission_expense": 0,
    "surrender_value": 0,
    "net_claims_expense": 0,
    "net_insurance_contract_reserve": 0,
    "policy_dividend_expense": 0,
    "reinsurance_expense": 0,
    "exchange_gain_loss": 0,
    "net_fair_value_hedge_gain": 0,
    "other_business_income": 0,
    "business_management_expenses": 0,
    "other_business_costs": 0
  }
]
```

### 现金流表

- **函数**: `get_ch_stock_cash_flow_statement`
- **说明**: 获取指定个股现金流表历史数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `announce_time` | string | 公告日期 |
| `tag_time` | string | 报告期 |
| `cash_from_sales` | number | 销售商品、提供劳务收到的现金 |
| `tax_refunds_received` | number | 收到的税费返还 |
| `other_operating_cash_in` | number | 收到其他与经营活动有关的现金 |
| `total_operating_cash_in` | number | 经营活动现金流入小计 |
| `cash_for_goods` | number | 购买商品、接受劳务支付的现金 |
| `cash_to_employees` | number | 支付给职工以及为职工支付的现金 |
| `tax_payments` | number | 支付的各项税费 |
| `other_operating_cash_out` | number | 支付其他与经营活动有关的现金 |
| `total_operating_cash_out` | number | 经营活动现金流出小计 |
| `net_operating_cash_flow` | number | 经营活动产生的现金流量净额 |
| `net_operating_cash_flow2` | number | 经营活动产生的现金流量净额2 |
| `cash_from_investment_recovery` | number | 收回投资收到的现金 |
| `cash_from_investment_income` | number | 取得投资收益收到的现金 |
| `cash_from_asset_disposal` | number | 处置固定资产、无形资产和其他长期资产收回的现金净额 |
| `cash_from_subsidiary_disposal` | number | 处置子公司及其他营业单位收到的现金净额 |
| `other_investing_cash_in` | number | 收到其他与投资活动有关的现金 |
| `total_investing_cash_in` | number | 投资活动现金流入小计 |
| `cash_for_asset_purchase` | number | 购建固定资产、无形资产和其他长期资产支付的现金 |
| `cash_for_investment` | number | 投资支付的现金 |
| `cash_for_subsidiary_acquisition` | number | 取得子公司及其他营业单位支付的现金净额 |
| `other_investing_cash_out` | number | 支付其他与投资活动有关的现金 |
| `total_investing_cash_out` | number | 投资活动现金流出小计 |
| `net_investing_cash_flow` | number | 投资活动产生的现金流量净额 |
| `cash_from_capital_absorption` | number | 吸收投资收到的现金 |
| `cash_from_borrowing` | number | 取得借款收到的现金 |
| `other_financing_cash_in` | number | 收到其他与筹资活动有关的现金 |
| `total_financing_cash_in` | number | 筹资活动现金流入小计 |
| `cash_for_debt_repayment` | number | 偿还债务支付的现金 |
| `cash_for_dividends` | number | 分配股利、利润或偿付利息支付的现金 |
| `other_financing_cash_out` | number | 支付其他与筹资活动有关的现金 |
| `total_financing_cash_out` | number | 筹资活动现金流出小计 |
| `net_financing_cash_flow` | number | 筹资活动产生的现金流量净额 |
| `exchange_rate_effect` | number | 汇率变动对现金的影响 |
| `other_cash_effects` | number | 其他原因对现金的影响 |
| `net_cash_increase` | number | 现金及现金等价物净增加额 |
| `beginning_cash_balance` | number | 期初现金及现金等价物余额 |
| `ending_cash_balance` | number | 期末现金及现金等价物余额 |
| `asset_impairment_provision` | number | 资产减值准备 |
| `depreciation_amortization` | number | 固定资产折旧、油气资产折耗、生产性生物资产折旧 |
| `intangible_assets_amortization` | number | 无形资产摊销 |
| `long_term_prepaid_expenses_amortization` | number | 长期待摊费用摊销 |
| `loss_on_asset_disposal` | number | 处置固定资产、无形资产和其他长期资产的损失 |
| `loss_on_fixed_assets_retirement` | number | 固定资产报废损失 |
| `fair_value_change_loss` | number | 公允价值变动损失 |
| `financial_expenses_cf` | number | 财务费用 |
| `investment_loss` | number | 投资损失 |
| `deferred_tax_assets_decrease` | number | 递延所得税资产减少 |
| `deferred_tax_liabilities_increase` | number | 递延所得税负债增加 |
| `inventory_decrease` | number | 存货的减少 |
| `operating_receivables_decrease` | number | 经营性应收项目的减少 |
| `operating_payables_increase` | number | 经营性应付项目的增加 |
| `other_adjustments` | number | 其他 |
| `net_increase_customer_deposits` | number | 客户存款和同业存放款项净增加额 |
| `net_increase_central_bank_borrowing` | number | 向中央银行借款净增加额 |
| `net_increase_other_financial_institutions` | number | 向其他金融机构拆入资金净增加额 |
| `cash_from_insurance_premiums` | number | 收到原保险合同保费取得的现金 |
| `net_cash_from_reinsurance` | number | 收到再保险业务现金净额 |
| `net_increase_policy_holder_deposits` | number | 保户储金及投资款净增加额 |
| `net_increase_trading_assets` | number | 处置以公允价值计量且其变动计入当期损益的金融资产净增加额 |
| `cash_from_interest_commission` | number | 收取利息、手续费及佣金的现金 |
| `net_increase_borrowed_funds` | number | 拆入资金净增加额 |
| `net_increase_repurchase` | number | 回购业务资金净增加额 |
| `net_increase_customer_loans` | number | 客户贷款及垫款净增加额 |
| `net_increase_deposits_central_bank` | number | 存放中央银行和同业款项净增加额 |
| `cash_for_insurance_claims` | number | 支付原保险合同赔付款项的现金 |
| `cash_for_interest_commission` | number | 支付利息、手续费及佣金的现金 |
| `cash_for_policy_dividends` | number | 支付保单红利的现金 |
| `investment_property_depreciation` | number | 投资性房地产的折旧及摊销 |
| `right_of_use_assets_depreciation` | number | 使用权资产折旧 |
| `net_increase_interest_fees` | number | 收取利息和手续费净增加额(金融类) |
| `cash_for_fees` | number | 支付手续费的现金(金融类) |
| `cash_for_bond_issuance` | number | 发行债券支付的现金(金融类) |

- **示例数据**:

```json
[
  {
    "announce_time": "19901231",
    "tag_time": "19901231",
    "cash_from_sales": 0,
    "tax_refunds_received": 0,
    "other_operating_cash_in": 0,
    "total_operating_cash_in": 0,
    "cash_for_goods": 0,
    "cash_to_employees": 0,
    "tax_payments": 0,
    "other_operating_cash_out": 0,
    "total_operating_cash_out": 0,
    "net_operating_cash_flow": 0,
    "net_operating_cash_flow2": 0,
    "cash_from_investment_recovery": 0,
    "cash_from_investment_income": 0,
    "cash_from_asset_disposal": 0,
    "cash_from_subsidiary_disposal": 0,
    "other_investing_cash_in": 0,
    "total_investing_cash_in": 0,
    "cash_for_asset_purchase": 0,
    "cash_for_investment": 0,
    "cash_for_subsidiary_acquisition": 0,
    "other_investing_cash_out": 0,
    "total_investing_cash_out": 0,
    "net_investing_cash_flow": 0,
    "cash_from_capital_absorption": 0,
    "cash_from_borrowing": 0,
    "other_financing_cash_in": 0,
    "total_financing_cash_in": 0,
    "cash_for_debt_repayment": 0,
    "cash_for_dividends": 0,
    "other_financing_cash_out": 0,
    "total_financing_cash_out": 0,
    "net_financing_cash_flow": 0,
    "exchange_rate_effect": 0,
    "other_cash_effects": 0,
    "net_cash_increase": 0,
    "beginning_cash_balance": 0,
    "ending_cash_balance": 0,
    "asset_impairment_provision": 0,
    "depreciation_amortization": 0,
    "intangible_assets_amortization": 0,
    "long_term_prepaid_expenses_amortization": 0,
    "loss_on_asset_disposal": 0,
    "loss_on_fixed_assets_retirement": 0,
    "fair_value_change_loss": 0,
    "financial_expenses_cf": 0,
    "investment_loss": 0,
    "deferred_tax_assets_decrease": 0,
    "deferred_tax_liabilities_increase": 0,
    "inventory_decrease": 0,
    "operating_receivables_decrease": 0,
    "operating_payables_increase": 0,
    "other_adjustments": 0,
    "net_increase_customer_deposits": 0,
    "net_increase_central_bank_borrowing": 0,
    "net_increase_other_financial_institutions": 0,
    "cash_from_insurance_premiums": 0,
    "net_cash_from_reinsurance": 0,
    "net_increase_policy_holder_deposits": 0,
    "net_increase_trading_assets": 0,
    "cash_from_interest_commission": 0,
    "net_increase_borrowed_funds": 0,
    "net_increase_repurchase": 0,
    "net_increase_customer_loans": 0,
    "net_increase_deposits_central_bank": 0,
    "cash_for_insurance_claims": 0,
    "cash_for_interest_commission": 0,
    "cash_for_policy_dividends": 0,
    "investment_property_depreciation": 0,
    "right_of_use_assets_depreciation": 0,
    "net_increase_interest_fees": 0,
    "cash_for_fees": 0,
    "cash_for_bond_issuance": 0
  }
]
```

### 财务主表

- **函数**: `get_ch_stock_financial_indicators`
- **说明**: 获取指定个股财务主表历史数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `announce_time` | string | 公告日期 |
| `tag_time` | string | 报告期 |
| `eps` | number | 基本每股收益 |
| `adjusted_eps` | number | 扣除非经常性损益每股收益 |
| `undistributed_profit_per_share` | number | 每股未分配利润 |
| `net_assets_per_share` | number | 每股净资产 |
| `capital_reserve_per_share` | number | 每股资本公积金 |
| `operating_cash_flow_per_share` | number | 每股经营现金流量 |
| `free_cash_flow_per_share` | number | 每股企业自由现金流 |
| `shareholder_free_cash_flow_per_share` | number | 每股股东自由现金流 |
| `roe` | number | 净资产收益率 |
| `weighted_roe` | number | 加权净资产收益率 |
| `roic` | number | 投入资本回报率(ROIC) |
| `return_on_investment` | number | 投资收益率 |
| `net_profit_margin` | number | 销售净利率 |
| `total_assets_profit_margin` | number | 总资产净利率 |
| `profit_margin` | number | 净利润率 |
| `gross_margin` | number | 销售毛利率 |
| `cost_profit_margin` | number | 成本费用利润率 |
| `operating_profit_margin` | number | 营业利润率 |
| `tax_rate` | number | 营业税金率 |
| `cost_rate` | number | 营业成本率 |
| `three_expense_ratio` | number | 三费比重 |
| `management_expense_ratio` | number | 管理费用率 |
| `financial_expense_ratio` | number | 财务费用率 |
| `ebit` | number | 息税前利润(EBIT) |
| `ebitda` | number | 息税折旧摊销前利润(EBITDA) |
| `ebitda_to_revenue` | number | EBITDA/营业总收入 |
| `accounts_receivable_turnover` | number | 应收帐款周转率 |
| `inventory_turnover` | number | 存货周转率 |
| `working_capital_turnover` | number | 运营资金周转率 |
| `total_assets_turnover` | number | 总资产周转率 |
| `fixed_assets_turnover` | number | 固定资产周转率 |
| `accounts_receivable_turnover_days` | number | 应收帐款周转天数 |
| `inventory_turnover_days` | number | 存货周转天数 |
| `current_assets_turnover` | number | 流动资产周转率 |
| `current_assets_turnover_days` | number | 流动资产周转天数 |
| `total_assets_turnover_days` | number | 总资产周转天数 |
| `equity_turnover` | number | 股东权益周转率 |
| `current_ratio` | number | 流动比率 |
| `quick_ratio` | number | 速动比率 |
| `cash_ratio` | number | 现金比率 |
| `interest_coverage_ratio` | number | 利息保障倍数 |
| `non_current_liabilities_ratio` | number | 非流动负债比率 |
| `current_liabilities_ratio` | number | 流动负债比率 |
| `tangible_assets_debt_ratio` | number | 有形资产净值债务率 |
| `equity_multiplier` | number | 权益乘数 |
| `equity_to_liabilities` | number | 股东的权益/负债合计 |
| `tangible_assets_to_liabilities` | number | 有形资产/负债合计 |
| `operating_cash_flow_to_liabilities` | number | 经营活动产生的现金流量净额/负债合计 |
| `ebitda_to_liabilities` | number | EBITDA/负债合计 |
| `asset_liability_ratio` | number | 资产负债率 |
| `current_assets_ratio` | number | 流动资产比率 |
| `cash_ratio_to_assets` | number | 货币资金比率 |
| `inventory_ratio` | number | 存货比率 |
| `fixed_assets_ratio` | number | 固定资产比率 |
| `liability_structure_ratio` | number | 负债结构比 |
| `parent_equity_to_invested_capital` | number | 归属于母公司股东权益/全部投入资本 |
| `equity_to_interest_bearing_debt` | number | 股东的权益/带息债务 |
| `tangible_assets_to_net_debt` | number | 有形资产/净债务 |
| `interest_bearing_debt_ratio` | number | 有息负债率 |
| `revenue_growth` | number | 营业收入增长率 |
| `net_profit_growth` | number | 净利润增长率 |
| `net_assets_growth` | number | 净资产增长率 |
| `fixed_assets_growth` | number | 固定资产增长率 |
| `total_assets_growth` | number | 总资产增长率 |
| `investment_income_growth` | number | 投资收益增长率 |
| `operating_profit_growth` | number | 营业利润增长率 |
| `adjusted_eps_growth` | number | 扣非每股收益同比 |
| `adjusted_net_profit_growth` | number | 扣非净利润同比 |
| `operating_cash_flow_to_revenue` | number | 经营活动产生的现金流量净额/营业收入 |
| `sales_cash_to_revenue` | number | 销售商品提供劳务收到的现金/营业收入 |
| `revenue_cash_content` | number | 营业收入现金含量 |
| `operating_cash_flow_to_profit` | number | 经营活动产生的现金流量净额/经营活动净收益 |
| `capital_expenditure_to_depreciation` | number | 资本支出/折旧和摊销 |
| `net_cash_flow_per_share` | number | 每股现金流量净额 |
| `operating_cash_flow_to_short_term_debt` | number | 经营净现金比率（短期债务） |
| `operating_cash_flow_to_total_debt` | number | 经营净现金比率（全部债务） |
| `operating_cash_flow_to_net_profit` | number | 经营活动现金净流量与净利润比率 |
| `total_assets_cash_recovery` | number | 全部资产现金回收率 |
| `audit_opinion` | integer | 审计意见 0-未审计,1-无保留意见,2-带强调事项段的无保留意见,3-保留意见,4-无法表示意见,5-否定意见及其他 |
| `dividend_payout_ratio` | number | 股利支付率 |
| `financial_total_score` | number | 财务总评分 |

- **示例数据**:

```json
[
  {
    "announce_time": "19901231",
    "tag_time": "19901231",
    "eps": 1.46,
    "undistributed_profit_per_share": 1.12,
    "net_assets_per_share": 3.51,
    "free_cash_flow_per_share": 0.96,
    "shareholder_free_cash_flow_per_share": 0.96,
    "roe": 41.6,
    "roic": 7.55,
    "total_assets_profit_margin": 3.08,
    "ebit": 101290000,
    "equity_multiplier": 1,
    "fixed_assets_ratio": 0.81,
    "parent_equity_to_invested_capital": 1234.28,
    "equity_to_interest_bearing_debt": -108.82,
    "tangible_assets_to_net_debt": -23.74,
    "net_profit_growth": 64.75,
    "net_assets_growth": 73.59,
    "fixed_assets_growth": 121.66,
    "total_assets_growth": 73.59,
    "dividend_payout_ratio": 17.09,
    "adjusted_eps": 0,
    "capital_reserve_per_share": 0,
    "operating_cash_flow_per_share": 0,
    "weighted_roe": 0,
    "return_on_investment": 0,
    "net_profit_margin": 0,
    "profit_margin": 0,
    "gross_margin": 0,
    "cost_profit_margin": 0,
    "operating_profit_margin": 0,
    "tax_rate": 0,
    "cost_rate": 0,
    "three_expense_ratio": 0,
    "management_expense_ratio": 0,
    "financial_expense_ratio": 0,
    "ebitda": 0,
    "ebitda_to_revenue": 0,
    "accounts_receivable_turnover": 0,
    "inventory_turnover": 0,
    "working_capital_turnover": 0,
    "total_assets_turnover": 0,
    "fixed_assets_turnover": 0,
    "accounts_receivable_turnover_days": 0,
    "inventory_turnover_days": 0,
    "current_assets_turnover": 0,
    "current_assets_turnover_days": 0,
    "total_assets_turnover_days": 0,
    "equity_turnover": 0,
    "current_ratio": 0,
    "quick_ratio": 0,
    "cash_ratio": 0,
    "interest_coverage_ratio": 0,
    "non_current_liabilities_ratio": 0,
    "current_liabilities_ratio": 0,
    "tangible_assets_debt_ratio": 0,
    "equity_to_liabilities": 0,
    "tangible_assets_to_liabilities": 0,
    "operating_cash_flow_to_liabilities": 0,
    "ebitda_to_liabilities": 0,
    "asset_liability_ratio": 0,
    "current_assets_ratio": 0,
    "cash_ratio_to_assets": 0,
    "inventory_ratio": 0,
    "liability_structure_ratio": 0,
    "interest_bearing_debt_ratio": 0,
    "revenue_growth": 0,
    "investment_income_growth": 0,
    "operating_profit_growth": 0,
    "adjusted_eps_growth": 0,
    "adjusted_net_profit_growth": 0,
    "operating_cash_flow_to_revenue": 0,
    "sales_cash_to_revenue": 0,
    "revenue_cash_content": 0,
    "operating_cash_flow_to_profit": 0,
    "capital_expenditure_to_depreciation": 0,
    "net_cash_flow_per_share": 0,
    "operating_cash_flow_to_short_term_debt": 0,
    "operating_cash_flow_to_total_debt": 0,
    "operating_cash_flow_to_net_profit": 0,
    "total_assets_cash_recovery": 0,
    "audit_opinion": 0,
    "financial_total_score": 0
  }
]
```

### 资产负债表

- **函数**: `get_ch_stock_balance_sheet`
- **说明**: 获取指定个股资产负债表历史数据
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `announce_time` | string | 公告日期 |
| `tag_time` | string | 报告期 |
| `cash` | number | 货币资金 |
| `trading_financial_assets` | number | 交易性金融资产 |
| `notes_receivable` | number | 应收票据 |
| `accounts_receivable` | number | 应收账款 |
| `prepayments` | number | 预付款项 |
| `other_receivables` | number | 其他应收款 |
| `intercompany_receivables` | number | 应收关联公司款 |
| `interest_receivable` | number | 应收利息 |
| `dividends_receivable` | number | 应收股利 |
| `inventory` | number | 存货 |
| `consumable_biological_assets` | number | 消耗性生物资产 |
| `non_current_assets_due_within_one_year` | number | 一年内到期的非流动资产 |
| `other_current_assets` | number | 其他流动资产 |
| `total_current_assets` | number | 流动资产合计 |
| `available_for_sale_financial_assets` | number | 可供出售金融资产 |
| `held_to_maturity_investments` | number | 持有至到期投资 |
| `long_term_receivables` | number | 长期应收款 |
| `long_term_equity_investment` | number | 长期股权投资 |
| `investment_property` | number | 投资性房地产 |
| `fixed_assets` | number | 固定资产 |
| `construction_in_progress` | number | 在建工程 |
| `construction_materials` | number | 工程物资 |
| `fixed_assets_for_disposal` | number | 固定资产清理 |
| `productive_biological_assets` | number | 生产性生物资产 |
| `oil_gas_assets` | number | 油气资产 |
| `intangible_assets` | number | 无形资产 |
| `development_expenditure` | number | 开发支出 |
| `goodwill` | number | 商誉 |
| `long_term_prepaid_expenses` | number | 长期待摊费用 |
| `deferred_tax_assets` | number | 递延所得税资产 |
| `other_non_current_assets` | number | 其他非流动资产 |
| `total_non_current_assets` | number | 非流动资产合计 |
| `total_assets` | number | 资产总计 |
| `short_term_loans` | number | 短期借款 |
| `trading_financial_liabilities` | number | 交易性金融负债 |
| `notes_payable` | number | 应付票据 |
| `accounts_payable` | number | 应付账款 |
| `advance_receipts` | number | 预收款项 |
| `employee_compensation_payable` | number | 应付职工薪酬 |
| `taxes_payable` | number | 应交税费 |
| `interest_payable` | number | 应付利息 |
| `dividends_payable` | number | 应付股利 |
| `other_payables` | number | 其他应付款 |
| `intercompany_payables` | number | 应付关联公司款 |
| `non_current_liabilities_due_within_one_year` | number | 一年内到期的非流动负债 |
| `other_current_liabilities` | number | 其他流动负债 |
| `total_current_liabilities` | number | 流动负债合计 |
| `long_term_loans` | number | 长期借款 |
| `bonds_payable` | number | 应付债券 |
| `long_term_payables` | number | 长期应付款 |
| `special_payables` | number | 专项应付款 |
| `provisions` | number | 预计负债(非流动负债) |
| `deferred_tax_liabilities` | number | 递延所得税负债 |
| `other_non_current_liabilities` | number | 其他非流动负债 |
| `total_non_current_liabilities` | number | 非流动负债合计 |
| `total_liabilities` | number | 负债合计 |
| `share_capital` | number | 实收资本（或股本） |
| `capital_reserve` | number | 资本公积 |
| `surplus_reserve` | number | 盈余公积 |
| `treasury_shares` | number | 减：库存股 |
| `undistributed_profit` | number | 未分配利润 |
| `minority_interest` | number | 少数股东权益 |
| `foreign_currency_translation_difference` | number | 外币报表折算价差 |
| `abnormal_operation_adjustment` | number | 非正常经营项目收益调整 |
| `total_owners_equity` | number | 所有者权益（或股东权益）合计 |
| `total_liabilities_and_equity` | number | 负债和所有者（或股东权益）合计 |
| `notes_and_accounts_payable` | number | 应付票据及应付账款 |
| `notes_and_accounts_receivable` | number | 应收票据及应收账款 |
| `deferred_income_non_current` | number | 递延收益(资产负债表-非流动负债) |
| `other_comprehensive_income_bs` | number | 其他综合收益(资产负债表) |
| `other_equity_instruments` | number | 其他权益工具(资产负债表) |
| `special_reserve` | number | 专项储备 |
| `right_of_use_assets` | number | 使用权资产 |
| `lease_liabilities` | number | 租赁负债 |
| `contract_liabilities` | number | 合同负债 |
| `contract_assets` | number | 合同资产 |
| `other_assets` | number | 其他资产 |
| `financing_receivables` | number | 应收款项融资 |

- **示例数据**:

```json
[
  {
    "announce_time": "19901231",
    "tag_time": "19901231",
    "cash": 804200000,
    "other_current_assets": 2004470000,
    "available_for_sale_financial_assets": 34040000,
    "fixed_assets": 23740000,
    "construction_in_progress": 9190000,
    "other_non_current_assets": 43550000,
    "total_non_current_assets": 76480000,
    "total_assets": 2919190000,
    "other_current_liabilities": 2682680000,
    "share_capital": 90040000,
    "surplus_reserve": 45180000,
    "undistributed_profit": 101290000,
    "total_owners_equity": 2919190000,
    "total_liabilities_and_equity": 2919190000,
    "trading_financial_assets": 0,
    "notes_receivable": 0,
    "accounts_receivable": 0,
    "prepayments": 0,
    "other_receivables": 0,
    "intercompany_receivables": 0,
    "interest_receivable": 0,
    "dividends_receivable": 0,
    "inventory": 0,
    "consumable_biological_assets": 0,
    "non_current_assets_due_within_one_year": 0,
    "total_current_assets": 0,
    "held_to_maturity_investments": 0,
    "long_term_receivables": 0,
    "long_term_equity_investment": 0,
    "investment_property": 0,
    "construction_materials": 0,
    "fixed_assets_for_disposal": 0,
    "productive_biological_assets": 0,
    "oil_gas_assets": 0,
    "intangible_assets": 0,
    "development_expenditure": 0,
    "goodwill": 0,
    "long_term_prepaid_expenses": 0,
    "deferred_tax_assets": 0,
    "short_term_loans": 0,
    "trading_financial_liabilities": 0,
    "notes_payable": 0,
    "accounts_payable": 0,
    "advance_receipts": 0,
    "employee_compensation_payable": 0,
    "taxes_payable": 0,
    "interest_payable": 0,
    "dividends_payable": 0,
    "other_payables": 0,
    "intercompany_payables": 0,
    "non_current_liabilities_due_within_one_year": 0,
    "total_current_liabilities": 0,
    "long_term_loans": 0,
    "bonds_payable": 0,
    "long_term_payables": 0,
    "special_payables": 0,
    "provisions": 0,
    "deferred_tax_liabilities": 0,
    "other_non_current_liabilities": 0,
    "total_non_current_liabilities": 0,
    "total_liabilities": 0,
    "capital_reserve": 0,
    "treasury_shares": 0,
    "minority_interest": 0,
    "foreign_currency_translation_difference": 0,
    "abnormal_operation_adjustment": 0,
    "notes_and_accounts_payable": 0,
    "notes_and_accounts_receivable": 0,
    "deferred_income_non_current": 0,
    "other_comprehensive_income_bs": 0,
    "other_equity_instruments": 0,
    "special_reserve": 0,
    "right_of_use_assets": 0,
    "lease_liabilities": 0,
    "contract_liabilities": 0,
    "contract_assets": 0,
    "other_assets": 0,
    "financing_receivables": 0
  }
]
```

### 财务辅助表

- **函数**: `get_ch_stock_auxiliary_data`
- **说明**: 获取指定个股资历史财务信息辅助表
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `announce_time` | string | 公告日期 |
| `tag_time` | string | 报告期 |
| `net_profit_last_year` | number | 近一年净利润(元) |
| `revenue_last_year` | number | 最近一年营业收入(万元) |
| `net_profit_parent_last_year` | number | 近一年归母净利润(万元) |
| `adjusted_net_profit_last_year` | number | 近一年扣非净利润(万元) |
| `operating_profit_last_year` | number | 近一年营业利润(万元) |
| `operating_cash_flow_last_year` | number | 近一年经营活动现金流净额 |
| `investing_cash_flow_last_year` | number | 近一年投资活动现金流净额(万元) |
| `net_cash_flow_last_year` | number | 近一年现金净流量(万元) |
| `revenue_ttm` | number | 营业总收入TTM(万元) |
| `operating_costs_non_financial_last_year` | number | 近一年营业成本-非金融类(万元) |
| `operating_costs_financial_last_year` | number | 近一年营业成本-金融类(万元) |
| `eps_single_quarter` | number | 基本每股收益（单季度） |
| `adjusted_eps_single_quarter` | number | 扣非每股收益(单季度) |
| `revenue_single_quarter` | number | 营业总收入(单季度)(万元) |
| `net_profit_single_quarter` | number | 净利润（单季度）(万元) |
| `operating_costs_single_quarter` | number | 营业成本（单季度）(万元) |
| `domestic_sales_revenue` | number | 主营业务收入(内销)(万元) |
| `export_sales_revenue` | number | 主营业务收入(外销)(万元) |
| `preferred_shares_liabilities` | number | 其中:优先股(非流动负债科目) |
| `perpetual_bonds_liabilities` | number | 永续债(非流动负债科目) |
| `long_term_employee_payables` | number | 长期应付职工薪酬 |
| `preferred_shares_equity` | number | 其中:优先股(所有者权益科目) |
| `perpetual_bonds_equity` | number | 永续债(所有者权益科目) |
| `interest_expense_detail` | number | 其中:利息费用 |
| `interest_income_detail` | number | 其中:利息收入 |
| `general_risk_reserve` | number | 一般风险准备(金融类) |
| `other_causes_cash_effect` | number | 加:其他原因对现金的影响2(万元) |
| `debt_to_equity` | number | 债务转为资本 |
| `convertible_bonds_due` | number | 一年内到期的可转换公司债券 |
| `finance_lease_assets` | number | 融资租入固定资产 |
| `continuing_operations_profit` | number | 持续经营净利润 |
| `discontinued_operations_profit` | number | 终止经营净利润 |

- **示例数据**:

```json
[
  {
    "announce_time": "19901231",
    "tag_time": "19901231",
    "net_profit_last_year": 70875000,
    "net_profit_parent_last_year": 7087.5,
    "revenue_last_year": 0,
    "adjusted_net_profit_last_year": 0,
    "operating_profit_last_year": 0,
    "operating_cash_flow_last_year": 0,
    "investing_cash_flow_last_year": 0,
    "net_cash_flow_last_year": 0,
    "revenue_ttm": 0,
    "operating_costs_non_financial_last_year": 0,
    "operating_costs_financial_last_year": 0,
    "eps_single_quarter": 0,
    "adjusted_eps_single_quarter": 0,
    "revenue_single_quarter": 0,
    "net_profit_single_quarter": 0,
    "operating_costs_single_quarter": 0,
    "domestic_sales_revenue": 0,
    "export_sales_revenue": 0,
    "preferred_shares_liabilities": 0,
    "perpetual_bonds_liabilities": 0,
    "long_term_employee_payables": 0,
    "preferred_shares_equity": 0,
    "perpetual_bonds_equity": 0,
    "interest_expense_detail": 0,
    "interest_income_detail": 0,
    "general_risk_reserve": 0,
    "other_causes_cash_effect": 0,
    "debt_to_equity": 0,
    "convertible_bonds_due": 0,
    "finance_lease_assets": 0,
    "continuing_operations_profit": 0,
    "discontinued_operations_profit": 0
  }
]
```

### 股东表

- **函数**: `get_ch_stock_share_capital_and_shareholders`
- **说明**: 获取指定个股历史股本股东表
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `announce_time` | string | 公告日期 |
| `tag_time` | string | 报告期 |
| `total_shares` | number | 总股本 |
| `circulating_a_shares` | number | 已上市流通A股 |
| `circulating_b_shares` | number | 已上市流通B股 |
| `circulating_h_shares` | number | 已上市流通H股 |
| `free_float_shares` | number | 自由流通股 |
| `restricted_a_shares` | number | 受限流通A股 |
| `shareholder_count` | integer | 股东人数(户) |
| `largest_shareholder_holding` | number | 第一大股东的持股数量 |
| `top_10_circulating_shareholders` | number | 十大流通股东持股数量合计 |
| `top_10_shareholders` | number | 十大股东持股数量合计 |
| `largest_circulating_shareholder` | number | 第一大流通股东持股量 |
| `top_10_circulating_a_shares` | number | 十大流通股东持有的流通A股合计 |
| `total_institutions` | integer | 机构总量（家） |
| `total_institution_holdings` | number | 机构持股总量(股) |
| `qfii_institutions` | integer | QFII机构数 |
| `qfii_holdings` | number | QFII持股量 |
| `broker_institutions` | integer | 券商机构数 |
| `broker_holdings` | number | 券商持股量 |
| `insurance_institutions` | integer | 保险机构数 |
| `insurance_holdings` | number | 保险持股量 |
| `fund_institutions` | integer | 基金机构数 |
| `fund_holdings` | number | 基金持股量 |
| `social_security_institutions` | integer | 社保机构数 |
| `social_security_holdings` | number | 社保持股量 |
| `private_equity_institutions` | integer | 私募机构数 |
| `private_equity_holdings` | number | 私募持股量 |
| `finance_company_institutions` | integer | 财务公司机构数 |
| `finance_company_holdings` | number | 财务公司持股量 |
| `annuity_institutions` | integer | 年金机构数 |
| `annuity_holdings` | number | 年金持股量 |
| `bank_institutions` | integer | 银行机构数 |
| `bank_holdings` | number | 银行持股量 |
| `general_corporate_institutions` | integer | 一般法人机构数 |
| `general_corporate_holdings` | number | 一般法人持股量 |
| `trust_institutions` | integer | 信托机构数 |
| `trust_holdings` | number | 信托持股量 |
| `special_corporate_institutions` | integer | 特殊法人机构数 |
| `special_corporate_holdings` | number | 特殊法人持股量 |
| `asset_management_institutions` | integer | 资管计划机构数 |
| `asset_management_holdings` | number | 资管计划持股量 |
| `northbound_institutions` | integer | 北上资金数（家） |
| `northbound_holdings` | number | 北上资金持股量 |
| `national_team_holdings` | number | 国家队持股数量（万股） |
| `employee_count` | integer | 员工总数(人) |

- **示例数据**:

```json
{
  "announce_time": "19901231",
  "tag_time": "19901231",
  "total_shares": 0,
  "circulating_a_shares": 0,
  "circulating_b_shares": 0,
  "circulating_h_shares": 0,
  "free_float_shares": 0,
  "restricted_a_shares": 0,
  "shareholder_count": 0,
  "largest_shareholder_holding": 0,
  "top_10_circulating_shareholders": 0,
  "top_10_shareholders": 0,
  "largest_circulating_shareholder": 0,
  "top_10_circulating_a_shares": 0,
  "total_institutions": 0,
  "total_institution_holdings": 0,
  "qfii_institutions": 0,
  "qfii_holdings": 0,
  "broker_institutions": 0,
  "broker_holdings": 0,
  "insurance_institutions": 0,
  "insurance_holdings": 0,
  "fund_institutions": 0,
  "fund_holdings": 0,
  "social_security_institutions": 0,
  "social_security_holdings": 0,
  "private_equity_institutions": 0,
  "private_equity_holdings": 0,
  "finance_company_institutions": 0,
  "finance_company_holdings": 0,
  "annuity_institutions": 0,
  "annuity_holdings": 0,
  "bank_institutions": 0,
  "bank_holdings": 0,
  "general_corporate_institutions": 0,
  "general_corporate_holdings": 0,
  "trust_institutions": 0,
  "trust_holdings": 0,
  "special_corporate_institutions": 0,
  "special_corporate_holdings": 0,
  "asset_management_institutions": 0,
  "asset_management_holdings": 0,
  "northbound_institutions": 0,
  "northbound_holdings": 0,
  "national_team_holdings": 0,
  "employee_count": 0
}
```

### 业绩预告

- **函数**: `get_ch_stock_net_profit`
- **说明**: 获取全市场个股预告，预盈预亏信息

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `name` | string | 股票名称 |
| `tag_date` | string | 公告日期 |
| `report_type` | string | 预告类型 |
| `report_name` | string | 预告名称 |
| `report_msg` | string | 预告摘要 |
| `net_profit` | number | 净利润预告值(万元) |
| `net_profit_inc_per` | number | 净利润增长率 |
| `pre_net_profit` | number | 上年同期净利润(万元) |
| `code` | string | 个股代码 |

- **示例数据**:

```json
{
  "code": "603580",
  "name": "*ST艾艾",
  "tag_date": "2026-04-30",
  "report_type": "预盈",
  "report_name": "2025年年报",
  "report_msg": "归属于母公司所有者的净利润4383.99万元",
  "net_profit": 4383.99,
  "net_profit_inc_per": 595.5844,
  "pre_net_profit": -884.61
}
```

### 财务核心指标(数据源SI)

- **函数**: `get_ch_si_stock_fin_key_indicators`
- **说明**: 从SI数据源获取个股财务核心指标（含盈利能力、成长能力、财务风险、营运能力等88项指标全量历史数据）
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001.SZ |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `report_period` | string | 报告期, YYYY-MM-DD |
| `report_name` | string | 报告名称 |
| `announcement_date` | string | 公告日期, YYYY-MM-DD |
| `currency` | string | 货币 |
| `report_type` | string | 报表类型 |
| `data_source` | string | 数据来源 |
| `is_audit` | string | 是否审计 |
| `accpayrt` | number | 应付账款周转率 |
| `accpaytdays` | number | 应付账款周转天数 |
| `accrecgturndays` | number | 应收账款周转天数 |
| `accrecgturnrt` | number | 应收账款周转率 |
| `assliabrt` | number | 资产负债率 |
| `biztotcost` | number | 营业成本 |
| `biztotinco` | number | 营业总收入 |
| `cashrt` | number | 现金比率 |
| `consvatquickrt` | number | 保守速动比率 |
| `crps` | number | 每股资本公积金 |
| `curassturndays` | number | 流动资产周转天数 |
| `curassturnrt` | number | 流动资产周转率 |
| `currentrt` | number | 流动比率 |
| `ebitmargin` | number | 息税前利润率 |
| `ebitps` | number | 每股息税前利润 |
| `em` | number | 权益乘数 |
| `emconms` | number | 权益乘数(含少数股权的净资产) |
| `epsbasic` | number | 基本每股收益 |
| `epsdilutednewp` | number | 摊薄每股收益_最新股数 |
| `epsfulldiluted` | number | 稀释每股收益 |
| `equrt` | number | 产权比率 |
| `fcfeps` | number | 每股股东自由现金流量 |
| `fcffps` | number | 每股企业自由现金流量 |
| `goodwill` | number | 商誉 |
| `incotaxtotp` | number | 所得税/利润总额 |
| `invturndays` | number | 存货周转天数 |
| `invturnrt` | number | 存货周转率 |
| `mananetr` | number | 经营现金流量净额 |
| `naps` | number | 每股净资产 |
| `napsadj` | number | 调整每股净资产_期末股数 |
| `napsnewp` | number | 每股净资产_最新股数 |
| `ncfps` | number | 每股现金流量净额 |
| `netprofit` | number | 净利润 |
| `npconmstoavgta` | number | 总资产净利率_平均(含少数股东损益) |
| `npcut` | number | 扣非净利润 |
| `npgrt` | number | 归属母公司净利润增长率 |
| `nptoavgta` | number | 总资产净利率_平均 |
| `opncfps` | number | 每股现金流 |
| `opncftonp` | number | 经营活动净现金/归属母公司的净利润 |
| `opncftoopti` | number | 经营性现金净流量/营业总收入 |
| `opncftosi` | number | 经营活动净现金/销售收入 |
| `opprort` | number | 营业利润率 |
| `oprevps` | number | 每股营业收入 |
| `parenetp` | number | 归母净利润 |
| `prototcrt` | number | 成本费用利润率 |
| `quickrt` | number | 速动比率 |
| `reps` | number | 每股留存收益 |
| `righaggr` | number | 股东权益合计(净资产) |
| `roa` | number | 总资产报酬率(ROA) |
| `roanopatconms` | number | 息前税后总资产报酬率_平均 |
| `roeavg` | number | 净资产收益率_平均 |
| `roeavgcut` | number | 净资产收益率_平均_扣除非经常损益 |
| `roediluted` | number | 摊薄净资产收益率 |
| `roedilutedcut` | number | 摊薄净资产收益率_扣除非经常损益 |
| `roeweighted` | number | 净资产收益率(ROE) |
| `roic` | number | 投入资本回报率 |
| `rota` | number | 总资本回报率 |
| `scostrt` | number | 销售成本率 |
| `sgpmargin` | number | 毛利率 |
| `snpmarginconms` | number | 销售净利率 |
| `srps` | number | 每股盈余公积金 |
| `tagrt` | number | 营业总收入增长率 |
| `taturndays` | number | 总资产周转天数 |
| `taturnrt` | number | 总资产周转率 |
| `tcexprt` | number | 成本费用率 |
| `toprevps` | number | 每股营业总收入 |
| `triexprt` | number | 期间费用率 |
| `upps` | number | 每股未分配利润 |
| `accpayrt_tongbi` | number | accpayrt 同比 |
| `accpaytdays_tongbi` | number | accpaytdays 同比 |
| `accrecgturndays_tongbi` | number | accrecgturndays 同比 |
| `accrecgturnrt_tongbi` | number | accrecgturnrt 同比 |
| `assliabrt_tongbi` | number | assliabrt 同比 |
| `biztotcost_tongbi` | number | biztotcost 同比 |
| `biztotinco_tongbi` | number | biztotinco 同比 |
| `cashrt_tongbi` | number | cashrt 同比 |
| `consvatquickrt_tongbi` | number | consvatquickrt 同比 |
| `crps_tongbi` | number | crps 同比 |
| `curassturndays_tongbi` | number | curassturndays 同比 |
| `curassturnrt_tongbi` | number | curassturnrt 同比 |
| `currentrt_tongbi` | number | currentrt 同比 |
| `ebitmargin_tongbi` | number | ebitmargin 同比 |
| `ebitps_tongbi` | number | ebitps 同比 |
| `em_tongbi` | number | em 同比 |
| `emconms_tongbi` | number | emconms 同比 |
| `epsbasic_tongbi` | number | epsbasic 同比 |
| `epsdilutednewp_tongbi` | number | epsdilutednewp 同比 |
| `epsfulldiluted_tongbi` | number | epsfulldiluted 同比 |
| `equrt_tongbi` | number | equrt 同比 |
| `fcfeps_tongbi` | number | fcfeps 同比 |
| `fcffps_tongbi` | number | fcffps 同比 |
| `goodwill_tongbi` | number | goodwill 同比 |
| `incotaxtotp_tongbi` | number | incotaxtotp 同比 |
| `invturndays_tongbi` | number | invturndays 同比 |
| `invturnrt_tongbi` | number | invturnrt 同比 |
| `mananetr_tongbi` | number | mananetr 同比 |
| `naps_tongbi` | number | naps 同比 |
| `napsadj_tongbi` | number | napsadj 同比 |
| `napsnewp_tongbi` | number | napsnewp 同比 |
| `ncfps_tongbi` | number | ncfps 同比 |
| `netprofit_tongbi` | number | netprofit 同比 |
| `npconmstoavgta_tongbi` | number | npconmstoavgta 同比 |
| `npcut_tongbi` | number | npcut 同比 |
| `npgrt_tongbi` | number | npgrt 同比 |
| `nptoavgta_tongbi` | number | nptoavgta 同比 |
| `opncfps_tongbi` | number | opncfps 同比 |
| `opncftonp_tongbi` | number | opncftonp 同比 |
| `opncftoopti_tongbi` | number | opncftoopti 同比 |
| `opncftosi_tongbi` | number | opncftosi 同比 |
| `opprort_tongbi` | number | opprort 同比 |
| `oprevps_tongbi` | number | oprevps 同比 |
| `parenetp_tongbi` | number | parenetp 同比 |
| `prototcrt_tongbi` | number | prototcrt 同比 |
| `quickrt_tongbi` | number | quickrt 同比 |
| `reps_tongbi` | number | reps 同比 |
| `righaggr_tongbi` | number | righaggr 同比 |
| `roa_tongbi` | number | roa 同比 |
| `roanopatconms_tongbi` | number | roanopatconms 同比 |
| `roeavg_tongbi` | number | roeavg 同比 |
| `roeavgcut_tongbi` | number | roeavgcut 同比 |
| `roediluted_tongbi` | number | roediluted 同比 |
| `roedilutedcut_tongbi` | number | roedilutedcut 同比 |
| `roeweighted_tongbi` | number | roeweighted 同比 |
| `roic_tongbi` | number | roic 同比 |
| `rota_tongbi` | number | rota 同比 |
| `scostrt_tongbi` | number | scostrt 同比 |
| `sgpmargin_tongbi` | number | sgpmargin 同比 |
| `snpmarginconms_tongbi` | number | snpmarginconms 同比 |
| `srps_tongbi` | number | srps 同比 |
| `tagrt_tongbi` | number | tagrt 同比 |
| `taturndays_tongbi` | number | taturndays 同比 |
| `taturnrt_tongbi` | number | taturnrt 同比 |
| `tcexprt_tongbi` | number | tcexprt 同比 |
| `toprevps_tongbi` | number | toprevps 同比 |
| `triexprt_tongbi` | number | triexprt 同比 |
| `upps_tongbi` | number | upps 同比 |

- **示例数据**:

```json
[
  {
    "report_period": "2026-03-31",
    "report_name": "2026一季报",
    "announcement_date": "2026-04-25",
    "currency": "CNY",
    "report_type": "合并期末",
    "data_source": "其他",
    "is_audit": "未审计",
    "assliabrt": 0.90982989,
    "crps": 4.153251,
    "em": 13.066269,
    "emconms": 11.090149,
    "epsbasic": 0.67,
    "epsdilutednewp": 0.748379,
    "epsfulldiluted": 0.67,
    "equrt": 11.82951971,
    "goodwill": 7568000000,
    "incotaxtotp": 0.16529685000000002,
    "mananetr": 37802000000,
    "naps": 23.914407,
    "napsadj": 20.67376,
    "napsnewp": 23.914508,
    "ncfps": -2.689632,
    "netprofit": 14523000000,
    "npconmstoavgta": 0.00242864,
    "npcut": 14488000000,
    "npgrt": 0.030292279999999998,
    "nptoavgta": 0.00242864,
    "opncfps": 1.947954,
    "opncftonp": 2.602905,
    "opncftoopti": 1.071576,
    "opncftosi": 1.071576,
    "opprort": 0.4929274,
    "oprevps": 1.817839,
    "reps": 15.175461,
    "roanopatconms": 0.00242864,
    "roeavg": 0.031733370000000004,
    "roeavgcut": 0.03165689,
    "roediluted": 0.03129397,
    "roedilutedcut": 0.03121855,
    "roeweighted": 0.028300000000000002,
    "scostrt": 0.28089123,
    "sgpmargin": 0.71910876,
    "snpmarginconms": 0.41168466000000004,
    "srps": 0.555549,
    "tagrt": 0.04651576,
    "taturndays": 15256.066417,
    "taturnrt": 0.005899,
    "toprevps": 1.817839,
    "upps": 14.619911,
    "assliabrt_tongbi": -0.28200000000000003,
    "crps_tongbi": -0.13799999999999998,
    "em_tongbi": -2.5669999999999997,
    "emconms_tongbi": -2.856,
    "epsbasic_tongbi": 8.065,
    "epsdilutednewp_tongbi": 3.029,
    "epsfulldiluted_tongbi": 8.065,
    "equrt_tongbi": -2.128,
    "incotaxtotp_tongbi": 0.133,
    "mananetr_tongbi": -76.801,
    "naps_tongbi": 6.401999999999999,
    "napsadj_tongbi": 8.204,
    "napsnewp_tongbi": 6.401999999999999,
    "ncfps_tongbi": -277.77,
    "netprofit_tongbi": 3.029,
    "npconmstoavgta_tongbi": -0.526,
    "npcut_tongbi": 3.1690000000000005,
    "npgrt_tongbi": 154.10600000000002,
    "nptoavgta_tongbi": -0.526,
    "opncfps_tongbi": -76.801,
    "opncftonp_tongbi": -77.483,
    "opncftoopti_tongbi": -77.83200000000001,
    "opncftosi_tongbi": -77.83200000000001,
    "opprort_tongbi": -1.738,
    "oprevps_tongbi": 4.652,
    "reps_tongbi": 10.545,
    "roanopatconms_tongbi": -0.526,
    "roeavg_tongbi": -3.078,
    "roeavgcut_tongbi": -2.947,
    "roediluted_tongbi": -3.17,
    "roedilutedcut_tongbi": -3.039,
    "roeweighted_tongbi": 1.0710000000000002,
    "scostrt_tongbi": 1.0630000000000002,
    "sgpmargin_tongbi": -0.409,
    "snpmarginconms_tongbi": -1.55,
    "tagrt_tongbi": 135.63400000000001,
    "taturndays_tongbi": -1.03,
    "taturnrt_tongbi": 1.045,
    "toprevps_tongbi": 4.652,
    "upps_tongbi": 10.99,
    "accpayrt": 0,
    "accpaytdays": 0,
    "accrecgturndays": 0,
    "accrecgturnrt": 0,
    "biztotcost": 0,
    "biztotinco": 0,
    "cashrt": 0,
    "consvatquickrt": 0,
    "curassturndays": 0,
    "curassturnrt": 0,
    "currentrt": 0,
    "ebitmargin": 0,
    "ebitps": 0,
    "fcfeps": 0,
    "fcffps": 0,
    "invturndays": 0,
    "invturnrt": 0,
    "parenetp": 0,
    "prototcrt": 0,
    "quickrt": 0,
    "righaggr": 0,
    "roa": 0,
    "roic": 0,
    "rota": 0,
    "tcexprt": 0,
    "triexprt": 0,
    "accpayrt_tongbi": 0,
    "accpaytdays_tongbi": 0,
    "accrecgturndays_tongbi": 0,
    "accrecgturnrt_tongbi": 0,
    "biztotcost_tongbi": 0,
    "biztotinco_tongbi": 0,
    "cashrt_tongbi": 0,
    "consvatquickrt_tongbi": 0,
    "curassturndays_tongbi": 0,
    "curassturnrt_tongbi": 0,
    "currentrt_tongbi": 0,
    "ebitmargin_tongbi": 0,
    "ebitps_tongbi": 0,
    "fcfeps_tongbi": 0,
    "fcffps_tongbi": 0,
    "goodwill_tongbi": 0,
    "invturndays_tongbi": 0,
    "invturnrt_tongbi": 0,
    "parenetp_tongbi": 0,
    "prototcrt_tongbi": 0,
    "quickrt_tongbi": 0,
    "righaggr_tongbi": 0,
    "roa_tongbi": 0,
    "roic_tongbi": 0,
    "rota_tongbi": 0,
    "srps_tongbi": 0,
    "tcexprt_tongbi": 0,
    "triexprt_tongbi": 0
  }
]
```

### 利润表(数据源SI)

- **函数**: `get_ch_si_stock_fin_income_statements`
- **说明**: 从SI数据源获取个股利润表全量历史数据，含营业总收入、营业总成本、各项费用、利润、每股收益等77项科目
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001.SZ |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `report_period` | string | 报告期, YYYY-MM-DD |
| `report_name` | string | 报告名称 |
| `announcement_date` | string | 公告日期, YYYY-MM-DD |
| `currency` | string | 货币 |
| `report_type` | string | 报表类型 |
| `data_source` | string | 数据来源 |
| `is_audit` | string | 是否审计 |
| `amortizcostassetssapi` | number | 以摊余成本计量的金融资产终止确认产生的收益 |
| `asseimpalossprofit` | number | 资产减值损失 |
| `assetsdislinco` | number | 资产处置收益 |
| `assoinveprof` | number | 对联营企业和合营企业的投资收益 |
| `basiceps` | number | 基本每股收益 |
| `bizcost` | number | 营业成本 |
| `bizinco` | number | 营业收入 |
| `biztax` | number | 营业税金及附加 |
| `biztotcost` | number | 营业总成本 |
| `biztotinco` | number | 营业总收入 |
| `cinaforsfv` | number | 可供出售金融资产公允价值变动损益 |
| `cinalibofrbp` | number | 重新计量设定受益计划变动额 |
| `compcreditfaval` | number | 企业自身信用风险公允价值变动 |
| `compincoamt` | number | 综合收益总额 |
| `compnetexpe` | number | 赔付支出净额 |
| `conopernprofit` | number | 持续经营净利润 |
| `contress` | number | 提取保险合同准备金净额 |
| `cpltohinco` | number | （二）以后将重分类进损益的其他综合收益 |
| `creditimplosseprofit` | number | 信用减值损失 |
| `custinco` | number | 托管收益 |
| `deveexpe` | number | 研发费用 |
| `dilutedeps` | number | 稀释每股收益 |
| `earnprem` | number | 已赚保费 |
| `epocfhgl` | number | 现金流量套期损益的有效部分 |
| `equmcpothinco` | number | 权益法下不能转损益的其他综合收益 |
| `euqmicolothinco` | number | 权益法下可转损益的其他综合收益 |
| `exchggain` | number | 汇兑收益 |
| `finassintoothinco` | number | 金融资产重分类计入其他综合收益的金额 |
| `finexpe` | number | 财务费用 |
| `futuloss` | number | 期货损益 |
| `hedcashflow` | number | 现金流量套期储备 |
| `htmccinaforsfv` | number | 持有至到期投资重分类为可供出售金融资产损益 |
| `incotaxexpe` | number | 所得税费用 |
| `inteexpe` | number | 利息支出 |
| `inteinco` | number | 利息收入 |
| `inteincoopcost` | number | 利息收入 |
| `interestexpense` | number | 利息费用 |
| `inveinco` | number | 投资收益 |
| `manaexpe` | number | 管理费用 |
| `mergeformnetprof` | number | 被合并方在合并前实现净利润 |
| `minysharinco` | number | 归属于少数股东的其他综合收益 |
| `minysharincoamt` | number | 归属于少数股东的综合收益总额 |
| `minysharrigh` | number | 少数股东损益 |
| `ncpothinco` | number | （一）以后不能重分类进损益的其他综合收益 |
| `netexpohedinc` | number | 净敞口套期收益 |
| `netprofit` | number | 净利润 |
| `noncassetsdisi` | number | 非流动资产处置利得 |
| `noncassetsdisl` | number | 非流动资产处置损失 |
| `nonoexpe` | number | 营业外支出 |
| `nonoreve` | number | 营业外收入 |
| `othdebtinvcredimpr` | number | 其他债权投资信用减值准备 |
| `othdebtinvfaval` | number | 其他债权投资公允价值变动 |
| `othequinfaval` | number | 其他权益工具投资公允价值变动 |
| `otherbizcost` | number | 其他业务成本 |
| `otherbizinco` | number | 其他业务收入 |
| `otherbizprof` | number | 其他业务利润 |
| `othercompinco` | number | 其他综合收益 |
| `othercpltohinco` | number | 其他 |
| `otherinco` | number | 其他收益 |
| `parecompinco` | number | 归属于母公司所有者的其他综合收益 |
| `parecompincoamt` | number | 归属于母公司所有者的综合收益总额 |
| `parenetp` | number | 归属于母公司所有者的净利润 |
| `perprofit` | number | 营业利润 |
| `polidiviexpe` | number | 保单红利支出 |
| `pounexpe` | number | 手续费及佣金支出 |
| `pouninco` | number | 手续费及佣金收入 |
| `realsale` | number | 房地产销售收入 |
| `realsalecost` | number | 房地产销售成本 |
| `reinexpe` | number | 分保费用 |
| `salesexpe` | number | 销售费用 |
| `subsidyincome` | number | 补贴收入 |
| `surrgold` | number | 退保金 |
| `tdiffforcur` | number | 外币财务报表折算差额 |
| `teropernprofit` | number | 终止经营净利润 |
| `totprofit` | number | 利润总额 |
| `unreinveloss` | number | 未确认投资损失 |
| `valuechgloss` | number | 公允价值变动收益 |
| `amortizcostassetssapi_tongbi` | number | amortizcostassetssapi 同比 |
| `asseimpalossprofit_tongbi` | number | asseimpalossprofit 同比 |
| `assetsdislinco_tongbi` | number | assetsdislinco 同比 |
| `assoinveprof_tongbi` | number | assoinveprof 同比 |
| `basiceps_tongbi` | number | basiceps 同比 |
| `bizcost_tongbi` | number | bizcost 同比 |
| `bizinco_tongbi` | number | bizinco 同比 |
| `biztax_tongbi` | number | biztax 同比 |
| `biztotcost_tongbi` | number | biztotcost 同比 |
| `biztotinco_tongbi` | number | biztotinco 同比 |
| `cinaforsfv_tongbi` | number | cinaforsfv 同比 |
| `cinalibofrbp_tongbi` | number | cinalibofrbp 同比 |
| `compcreditfaval_tongbi` | number | compcreditfaval 同比 |
| `compincoamt_tongbi` | number | compincoamt 同比 |
| `compnetexpe_tongbi` | number | compnetexpe 同比 |
| `conopernprofit_tongbi` | number | conopernprofit 同比 |
| `contress_tongbi` | number | contress 同比 |
| `cpltohinco_tongbi` | number | cpltohinco 同比 |
| `creditimplosseprofit_tongbi` | number | creditimplosseprofit 同比 |
| `custinco_tongbi` | number | custinco 同比 |
| `deveexpe_tongbi` | number | deveexpe 同比 |
| `dilutedeps_tongbi` | number | dilutedeps 同比 |
| `earnprem_tongbi` | number | earnprem 同比 |
| `epocfhgl_tongbi` | number | epocfhgl 同比 |
| `equmcpothinco_tongbi` | number | equmcpothinco 同比 |
| `euqmicolothinco_tongbi` | number | euqmicolothinco 同比 |
| `exchggain_tongbi` | number | exchggain 同比 |
| `finassintoothinco_tongbi` | number | finassintoothinco 同比 |
| `finexpe_tongbi` | number | finexpe 同比 |
| `futuloss_tongbi` | number | futuloss 同比 |
| `hedcashflow_tongbi` | number | hedcashflow 同比 |
| `htmccinaforsfv_tongbi` | number | htmccinaforsfv 同比 |
| `incotaxexpe_tongbi` | number | incotaxexpe 同比 |
| `inteexpe_tongbi` | number | inteexpe 同比 |
| `inteinco_tongbi` | number | inteinco 同比 |
| `inteincoopcost_tongbi` | number | inteincoopcost 同比 |
| `interestexpense_tongbi` | number | interestexpense 同比 |
| `inveinco_tongbi` | number | inveinco 同比 |
| `manaexpe_tongbi` | number | manaexpe 同比 |
| `mergeformnetprof_tongbi` | number | mergeformnetprof 同比 |
| `minysharinco_tongbi` | number | minysharinco 同比 |
| `minysharincoamt_tongbi` | number | minysharincoamt 同比 |
| `minysharrigh_tongbi` | number | minysharrigh 同比 |
| `ncpothinco_tongbi` | number | ncpothinco 同比 |
| `netexpohedinc_tongbi` | number | netexpohedinc 同比 |
| `netprofit_tongbi` | number | netprofit 同比 |
| `noncassetsdisi_tongbi` | number | noncassetsdisi 同比 |
| `noncassetsdisl_tongbi` | number | noncassetsdisl 同比 |
| `nonoexpe_tongbi` | number | nonoexpe 同比 |
| `nonoreve_tongbi` | number | nonoreve 同比 |
| `othdebtinvcredimpr_tongbi` | number | othdebtinvcredimpr 同比 |
| `othdebtinvfaval_tongbi` | number | othdebtinvfaval 同比 |
| `othequinfaval_tongbi` | number | othequinfaval 同比 |
| `otherbizcost_tongbi` | number | otherbizcost 同比 |
| `otherbizinco_tongbi` | number | otherbizinco 同比 |
| `otherbizprof_tongbi` | number | otherbizprof 同比 |
| `othercompinco_tongbi` | number | othercompinco 同比 |
| `othercpltohinco_tongbi` | number | othercpltohinco 同比 |
| `otherinco_tongbi` | number | otherinco 同比 |
| `parecompinco_tongbi` | number | parecompinco 同比 |
| `parecompincoamt_tongbi` | number | parecompincoamt 同比 |
| `parenetp_tongbi` | number | parenetp 同比 |
| `perprofit_tongbi` | number | perprofit 同比 |
| `polidiviexpe_tongbi` | number | polidiviexpe 同比 |
| `pounexpe_tongbi` | number | pounexpe 同比 |
| `pouninco_tongbi` | number | pouninco 同比 |
| `realsale_tongbi` | number | realsale 同比 |
| `realsalecost_tongbi` | number | realsalecost 同比 |
| `reinexpe_tongbi` | number | reinexpe 同比 |
| `salesexpe_tongbi` | number | salesexpe 同比 |
| `subsidyincome_tongbi` | number | subsidyincome 同比 |
| `surrgold_tongbi` | number | surrgold 同比 |
| `tdiffforcur_tongbi` | number | tdiffforcur 同比 |
| `teropernprofit_tongbi` | number | teropernprofit 同比 |
| `totprofit_tongbi` | number | totprofit 同比 |
| `unreinveloss_tongbi` | number | unreinveloss 同比 |
| `valuechgloss_tongbi` | number | valuechgloss 同比 |

- **示例数据**:

```json
{
  "report_period": "2026-03-31",
  "report_name": "2026一季报",
  "announcement_date": "2026-04-25",
  "currency": "CNY",
  "report_type": "合并期末",
  "data_source": "定期报告",
  "is_audit": "未审计",
  "amortizcostassetssapi": 564000000,
  "basiceps": 0.67,
  "bizinco": 35277000000,
  "biztax": 397000000,
  "compincoamt": 14451000000,
  "conopernprofit": 14523000000,
  "cpltohinco": -46000000,
  "dilutedeps": 0.67,
  "exchggain": 57000000,
  "inteexpe": 17814000000,
  "inteinco": 39895000000,
  "ncpothinco": -26000000,
  "netprofit": 14523000000,
  "nonoexpe": 2000000,
  "othdebtinvcredimpr": -164000000,
  "othdebtinvfaval": 137000000,
  "othequinfaval": -26000000,
  "otherbizinco": 62000000,
  "othercompinco": -72000000,
  "otherinco": 36000000,
  "parecompinco": -72000000,
  "pounexpe": 799000000,
  "pouninco": 8161000000,
  "tdiffforcur": -19000000,
  "totprofit": 17399000000,
  "valuechgloss": 1168000000,
  "basiceps_tongbi": 8.065,
  "bizinco_tongbi": 4.652,
  "biztax_tongbi": 26.433,
  "compincoamt_tongbi": 8.67,
  "conopernprofit_tongbi": 3.029,
  "cpltohinco_tongbi": 93.16499999999999,
  "dilutedeps_tongbi": 8.065,
  "exchggain_tongbi": -85.89099999999999,
  "inteexpe_tongbi": -19.576,
  "inteinco_tongbi": -11.222,
  "ncpothinco_tongbi": 79.2,
  "netprofit_tongbi": 3.029,
  "nonoexpe_tongbi": -95.745,
  "othdebtinvcredimpr_tongbi": -1193.333,
  "othdebtinvfaval_tongbi": 120,
  "othequinfaval_tongbi": 79.2,
  "otherbizinco_tongbi": -50.794,
  "othercompinco_tongbi": 90.977,
  "otherinco_tongbi": -16.279,
  "parecompinco_tongbi": 90.977,
  "pounexpe_tongbi": -6.768000000000001,
  "pouninco_tongbi": 9.544,
  "tdiffforcur_tongbi": -533.333,
  "totprofit_tongbi": 3.056,
  "valuechgloss_tongbi": 137.922,
  "asseimpalossprofit": 0,
  "assetsdislinco": 0,
  "assoinveprof": 0,
  "bizcost": 0,
  "biztotcost": 0,
  "biztotinco": 0,
  "cinaforsfv": 0,
  "cinalibofrbp": 0,
  "compcreditfaval": 0,
  "compnetexpe": 0,
  "contress": 0,
  "creditimplosseprofit": 0,
  "custinco": 0,
  "deveexpe": 0,
  "earnprem": 0,
  "epocfhgl": 0,
  "equmcpothinco": 0,
  "euqmicolothinco": 0,
  "finassintoothinco": 0,
  "finexpe": 0,
  "futuloss": 0,
  "hedcashflow": 0,
  "htmccinaforsfv": 0,
  "incotaxexpe": 0,
  "inteincoopcost": 0,
  "interestexpense": 0,
  "inveinco": 0,
  "manaexpe": 0,
  "mergeformnetprof": 0,
  "minysharinco": 0,
  "minysharincoamt": 0,
  "minysharrigh": 0,
  "netexpohedinc": 0,
  "noncassetsdisi": 0,
  "noncassetsdisl": 0,
  "nonoreve": 0,
  "otherbizcost": 0,
  "otherbizprof": 0,
  "othercpltohinco": 0,
  "parecompincoamt": 0,
  "parenetp": 0,
  "perprofit": 0,
  "polidiviexpe": 0,
  "realsale": 0,
  "realsalecost": 0,
  "reinexpe": 0,
  "salesexpe": 0,
  "subsidyincome": 0,
  "surrgold": 0,
  "teropernprofit": 0,
  "unreinveloss": 0,
  "amortizcostassetssapi_tongbi": 0,
  "asseimpalossprofit_tongbi": 0,
  "assetsdislinco_tongbi": 0,
  "assoinveprof_tongbi": 0,
  "bizcost_tongbi": 0,
  "biztotcost_tongbi": 0,
  "biztotinco_tongbi": 0,
  "cinaforsfv_tongbi": 0,
  "cinalibofrbp_tongbi": 0,
  "compcreditfaval_tongbi": 0,
  "compnetexpe_tongbi": 0,
  "contress_tongbi": 0,
  "creditimplosseprofit_tongbi": 0,
  "custinco_tongbi": 0,
  "deveexpe_tongbi": 0,
  "earnprem_tongbi": 0,
  "epocfhgl_tongbi": 0,
  "equmcpothinco_tongbi": 0,
  "euqmicolothinco_tongbi": 0,
  "finassintoothinco_tongbi": 0,
  "finexpe_tongbi": 0,
  "futuloss_tongbi": 0,
  "hedcashflow_tongbi": 0,
  "htmccinaforsfv_tongbi": 0,
  "incotaxexpe_tongbi": 0,
  "inteincoopcost_tongbi": 0,
  "interestexpense_tongbi": 0,
  "inveinco_tongbi": 0,
  "manaexpe_tongbi": 0,
  "mergeformnetprof_tongbi": 0,
  "minysharinco_tongbi": 0,
  "minysharincoamt_tongbi": 0,
  "minysharrigh_tongbi": 0,
  "netexpohedinc_tongbi": 0,
  "noncassetsdisi_tongbi": 0,
  "noncassetsdisl_tongbi": 0,
  "nonoreve_tongbi": 0,
  "otherbizcost_tongbi": 0,
  "otherbizprof_tongbi": 0,
  "othercpltohinco_tongbi": 0,
  "parecompincoamt_tongbi": 0,
  "parenetp_tongbi": 0,
  "perprofit_tongbi": 0,
  "polidiviexpe_tongbi": 0,
  "realsale_tongbi": 0,
  "realsalecost_tongbi": 0,
  "reinexpe_tongbi": 0,
  "salesexpe_tongbi": 0,
  "subsidyincome_tongbi": 0,
  "surrgold_tongbi": 0,
  "teropernprofit_tongbi": 0,
  "unreinveloss_tongbi": 0
}
```

### 资产负债表(数据源SI)

- **函数**: `get_ch_si_stock_fin_balance_sheet`
- **说明**: 从SI数据源获取个股资产负债表全量历史数据，含流动资产、非流动资产、流动负债、非流动负债、所有者权益等140项科目
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001.SZ |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `report_period` | string | 报告期, YYYY-MM-DD |
| `report_name` | string | 报告名称 |
| `announcement_date` | string | 公告日期, YYYY-MM-DD |
| `currency` | string | 货币 |
| `report_type` | string | 报表类型 |
| `data_source` | string | 数据来源 |
| `is_audit` | string | 是否审计 |
| `accheldfors` | number | 划分为持有待售的资产 |
| `accopaya` | number | 应付账款 |
| `accorece` | number | 应收账款 |
| `accrexpe` | number | 预提费用 |
| `accudepr` | number | 累计折旧 |
| `actitradsecu` | number | 代理买卖证券款 |
| `actiundesecu` | number | 代理承销证券款 |
| `advapaym` | number | 预收款项 |
| `amortizcostassets` | number | 以摊余成本计量的金融资产 |
| `avaisellasse` | number | 可供出售金融资产 |
| `bdspaya` | number | 应付债券 |
| `bdspayaperbond` | number | 应付债券：永续债 |
| `bdspayaprest` | number | 应付债券：优先股 |
| `capisurp` | number | 资本公积 |
| `cenbankborr` | number | 向中央银行借款 |
| `comasse` | number | 公益性生物资产 |
| `consprog` | number | 在建工程 |
| `consprogtot` | number | 在建工程合计 |
| `contractasset` | number | 合同资产 |
| `contractliab` | number | 合同负债 |
| `copepoun` | number | 应付手续费及佣金 |
| `copewithreinrece` | number | 应付分保账款 |
| `copeworkersal` | number | 应付职工薪酬 |
| `curfds` | number | 货币资金 |
| `curtrandiff` | number | 外币报表折算差额 |
| `defeincotaxliab` | number | 递延所得税负债 |
| `defereve` | number | 一年内的递延收益 |
| `defetaxasset` | number | 递延所得税资产 |
| `deposit` | number | 吸收存款及同业存放 |
| `derifinaasset` | number | 衍生金融资产 |
| `deriliab` | number | 衍生金融负债 |
| `deveexpe` | number | 开发支出 |
| `dividrece` | number | 应收股利 |
| `divipaya` | number | 应付股利 |
| `dometicksett` | number | 国内票证结算 |
| `duenoncliab` | number | 一年内到期的非流动负债 |
| `engimate` | number | 工程物资 |
| `equiinve` | number | 长期股权投资 |
| `expecurrliab` | number | 预计流动负债 |
| `expenoncliab` | number | 预计非流动负债 |
| `expinoncurrasset` | number | 一年内到期的非流动资产 |
| `expotaxrebarece` | number | 应收出口退税 |
| `fairvalueassets` | number | 以公允价值计量且其变动计入其他综合收益的金融资产 |
| `fdsborr` | number | 拆入资金 |
| `fixedasseclea` | number | 固定资产清理 |
| `fixedassecleatot` | number | 固定资产及清理合计 |
| `fixedasseimmo` | number | 固定资产原值 |
| `fixedasseimpa` | number | 固定资产减值准备 |
| `fixedassenet` | number | 固定资产净额 |
| `fixedassenetw` | number | 固定资产净值 |
| `generiskrese` | number | 一般风险准备 |
| `goodwill` | number | 商誉 |
| `holdinvedue` | number | 债权投资 |
| `hydrasset` | number | 油气资产 |
| `insucontrese` | number | 保险合同准备金 |
| `intaasset` | number | 无形资产 |
| `intelpay` | number | 内部应付款 |
| `intelrece` | number | 内部应收款 |
| `intepaya` | number | 应付利息 |
| `interece` | number | 应收利息 |
| `inteticksett` | number | 国际票证结算 |
| `inve` | number | 存货 |
| `inveprop` | number | 投资性房地产 |
| `lcopeworkersal` | number | 长期应付职工薪酬 |
| `leaseliab` | number | 租赁负债 |
| `lendandloan` | number | 发放贷款及垫款 |
| `liabheldfors` | number | 划分为持有待售的负债 |
| `logprepexpe` | number | 长期待摊费用 |
| `longborr` | number | 长期借款 |
| `longdefeinco` | number | 长期递延收益 |
| `longpaya` | number | 长期应付款 |
| `longpayatot` | number | 长期应付款合计 |
| `longrece` | number | 长期应收款 |
| `margrece` | number | 应收保证金 |
| `margrequ` | number | 应付保证金 |
| `minysharrigh` | number | 少数股东权益 |
| `notesaccopaya` | number | 应付票据及应付账款 |
| `notesaccorece` | number | 应收票据及应收账款 |
| `notespaya` | number | 应付票据 |
| `notesrece` | number | 应收票据 |
| `ocl` | number | 其他综合收益 |
| `othdebtinvest` | number | 其他债权投资 |
| `othequin` | number | 其他权益工具 |
| `othequininvest` | number | 其他权益工具投资 |
| `othercurrasse` | number | 其他流动资产 |
| `othercurreliabi` | number | 其他流动负债 |
| `otherfeepaya` | number | 其他应交款 |
| `otherlonginve` | number | 其他长期投资 |
| `othernoncasse` | number | 其他非流动资产 |
| `othernoncfinasse` | number | 其他非流动金融资产 |
| `othernoncliabi` | number | 其他非流动负债 |
| `otherpay` | number | 其他应付款 |
| `otherpaytot` | number | 其他应付款合计 |
| `otherrece` | number | 其他应收款 |
| `otherrecetot` | number | 其他应收款(合计) |
| `paidincapi` | number | 实收资本(或股本) |
| `paresharrigh` | number | 归属于母公司股东权益合计 |
| `perbond` | number | 永续债 |
| `plac` | number | 拆出资金 |
| `premrece` | number | 应收保费 |
| `prep` | number | 预付款项 |
| `prepexpe` | number | 待摊费用 |
| `prest` | number | 优先股 |
| `prodasse` | number | 生产性生物资产 |
| `purcresaasset` | number | 买入返售金融资产 |
| `recfinanc` | number | 应收款项融资 |
| `reincontrese` | number | 应收分保合同准备金 |
| `reinrece` | number | 应收分保账款 |
| `rese` | number | 盈余公积 |
| `righaggr` | number | 所有者权益(或股东权益)合计 |
| `ruseassets` | number | 使用权资产 |
| `sellrepasse` | number | 卖出回购金融资产款 |
| `settresedepo` | number | 结算备付金 |
| `shorttermbdspaya` | number | 应付短期债券 |
| `shorttermborr` | number | 短期借款 |
| `specpaya` | number | 专项应付款 |
| `specrese` | number | 专项储备 |
| `subsrece` | number | 应收补贴款 |
| `taxespaya` | number | 应交税费 |
| `topaycashdivi` | number | 拟分配现金股利 |
| `totalcurrliab` | number | 流动负债合计 |
| `totalnoncassets` | number | 非流动资产合计 |
| `totalnoncliab` | number | 非流动负债合计 |
| `totasset` | number | 资产总计 |
| `totcurrasset` | number | 流动资产合计 |
| `totliab` | number | 负债合计 |
| `totliabsharequi` | number | 负债和所有者权益(或股东权益)总计 |
| `tradfinasset` | number | 交易性金融资产 |
| `tradfinliab` | number | 交易性金融负债 |
| `tradshartrad` | number | 股权分置流通权 |
| `treastk` | number | 减:库存股 |
| `undiprof` | number | 未分配利润 |
| `unreinveloss` | number | 未确定的投资损失 |
| `unseg` | number | 待处理流动资产损益 |
| `warliabrese` | number | 担保责任赔偿准备金 |
| `accheldfors_tongbi` | number | accheldfors 同比 |
| `accopaya_tongbi` | number | accopaya 同比 |
| `accorece_tongbi` | number | accorece 同比 |
| `accrexpe_tongbi` | number | accrexpe 同比 |
| `accudepr_tongbi` | number | accudepr 同比 |
| `actitradsecu_tongbi` | number | actitradsecu 同比 |
| `actiundesecu_tongbi` | number | actiundesecu 同比 |
| `advapaym_tongbi` | number | advapaym 同比 |
| `amortizcostassets_tongbi` | number | amortizcostassets 同比 |
| `avaisellasse_tongbi` | number | avaisellasse 同比 |
| `bdspaya_tongbi` | number | bdspaya 同比 |
| `bdspayaperbond_tongbi` | number | bdspayaperbond 同比 |
| `bdspayaprest_tongbi` | number | bdspayaprest 同比 |
| `capisurp_tongbi` | number | capisurp 同比 |
| `cenbankborr_tongbi` | number | cenbankborr 同比 |
| `comasse_tongbi` | number | comasse 同比 |
| `consprog_tongbi` | number | consprog 同比 |
| `consprogtot_tongbi` | number | consprogtot 同比 |
| `contractasset_tongbi` | number | contractasset 同比 |
| `contractliab_tongbi` | number | contractliab 同比 |
| `copepoun_tongbi` | number | copepoun 同比 |
| `copewithreinrece_tongbi` | number | copewithreinrece 同比 |
| `copeworkersal_tongbi` | number | copeworkersal 同比 |
| `curfds_tongbi` | number | curfds 同比 |
| `curtrandiff_tongbi` | number | curtrandiff 同比 |
| `defeincotaxliab_tongbi` | number | defeincotaxliab 同比 |
| `defereve_tongbi` | number | defereve 同比 |
| `defetaxasset_tongbi` | number | defetaxasset 同比 |
| `deposit_tongbi` | number | deposit 同比 |
| `derifinaasset_tongbi` | number | derifinaasset 同比 |
| `deriliab_tongbi` | number | deriliab 同比 |
| `deveexpe_tongbi` | number | deveexpe 同比 |
| `dividrece_tongbi` | number | dividrece 同比 |
| `divipaya_tongbi` | number | divipaya 同比 |
| `dometicksett_tongbi` | number | dometicksett 同比 |
| `duenoncliab_tongbi` | number | duenoncliab 同比 |
| `engimate_tongbi` | number | engimate 同比 |
| `equiinve_tongbi` | number | equiinve 同比 |
| `expecurrliab_tongbi` | number | expecurrliab 同比 |
| `expenoncliab_tongbi` | number | expenoncliab 同比 |
| `expinoncurrasset_tongbi` | number | expinoncurrasset 同比 |
| `expotaxrebarece_tongbi` | number | expotaxrebarece 同比 |
| `fairvalueassets_tongbi` | number | fairvalueassets 同比 |
| `fdsborr_tongbi` | number | fdsborr 同比 |
| `fixedasseclea_tongbi` | number | fixedasseclea 同比 |
| `fixedassecleatot_tongbi` | number | fixedassecleatot 同比 |
| `fixedasseimmo_tongbi` | number | fixedasseimmo 同比 |
| `fixedasseimpa_tongbi` | number | fixedasseimpa 同比 |
| `fixedassenet_tongbi` | number | fixedassenet 同比 |
| `fixedassenetw_tongbi` | number | fixedassenetw 同比 |
| `generiskrese_tongbi` | number | generiskrese 同比 |
| `goodwill_tongbi` | number | goodwill 同比 |
| `holdinvedue_tongbi` | number | holdinvedue 同比 |
| `hydrasset_tongbi` | number | hydrasset 同比 |
| `insucontrese_tongbi` | number | insucontrese 同比 |
| `intaasset_tongbi` | number | intaasset 同比 |
| `intelpay_tongbi` | number | intelpay 同比 |
| `intelrece_tongbi` | number | intelrece 同比 |
| `intepaya_tongbi` | number | intepaya 同比 |
| `interece_tongbi` | number | interece 同比 |
| `inteticksett_tongbi` | number | inteticksett 同比 |
| `inve_tongbi` | number | inve 同比 |
| `inveprop_tongbi` | number | inveprop 同比 |
| `lcopeworkersal_tongbi` | number | lcopeworkersal 同比 |
| `leaseliab_tongbi` | number | leaseliab 同比 |
| `lendandloan_tongbi` | number | lendandloan 同比 |
| `liabheldfors_tongbi` | number | liabheldfors 同比 |
| `logprepexpe_tongbi` | number | logprepexpe 同比 |
| `longborr_tongbi` | number | longborr 同比 |
| `longdefeinco_tongbi` | number | longdefeinco 同比 |
| `longpaya_tongbi` | number | longpaya 同比 |
| `longpayatot_tongbi` | number | longpayatot 同比 |
| `longrece_tongbi` | number | longrece 同比 |
| `margrece_tongbi` | number | margrece 同比 |
| `margrequ_tongbi` | number | margrequ 同比 |
| `minysharrigh_tongbi` | number | minysharrigh 同比 |
| `notesaccopaya_tongbi` | number | notesaccopaya 同比 |
| `notesaccorece_tongbi` | number | notesaccorece 同比 |
| `notespaya_tongbi` | number | notespaya 同比 |
| `notesrece_tongbi` | number | notesrece 同比 |
| `ocl_tongbi` | number | ocl 同比 |
| `othdebtinvest_tongbi` | number | othdebtinvest 同比 |
| `othequin_tongbi` | number | othequin 同比 |
| `othequininvest_tongbi` | number | othequininvest 同比 |
| `othercurrasse_tongbi` | number | othercurrasse 同比 |
| `othercurreliabi_tongbi` | number | othercurreliabi 同比 |
| `otherfeepaya_tongbi` | number | otherfeepaya 同比 |
| `otherlonginve_tongbi` | number | otherlonginve 同比 |
| `othernoncasse_tongbi` | number | othernoncasse 同比 |
| `othernoncfinasse_tongbi` | number | othernoncfinasse 同比 |
| `othernoncliabi_tongbi` | number | othernoncliabi 同比 |
| `otherpay_tongbi` | number | otherpay 同比 |
| `otherpaytot_tongbi` | number | otherpaytot 同比 |
| `otherrece_tongbi` | number | otherrece 同比 |
| `otherrecetot_tongbi` | number | otherrecetot 同比 |
| `paidincapi_tongbi` | number | paidincapi 同比 |
| `paresharrigh_tongbi` | number | paresharrigh 同比 |
| `perbond_tongbi` | number | perbond 同比 |
| `plac_tongbi` | number | plac 同比 |
| `premrece_tongbi` | number | premrece 同比 |
| `prep_tongbi` | number | prep 同比 |
| `prepexpe_tongbi` | number | prepexpe 同比 |
| `prest_tongbi` | number | prest 同比 |
| `prodasse_tongbi` | number | prodasse 同比 |
| `purcresaasset_tongbi` | number | purcresaasset 同比 |
| `recfinanc_tongbi` | number | recfinanc 同比 |
| `reincontrese_tongbi` | number | reincontrese 同比 |
| `reinrece_tongbi` | number | reinrece 同比 |
| `rese_tongbi` | number | rese 同比 |
| `righaggr_tongbi` | number | righaggr 同比 |
| `ruseassets_tongbi` | number | ruseassets 同比 |
| `sellrepasse_tongbi` | number | sellrepasse 同比 |
| `settresedepo_tongbi` | number | settresedepo 同比 |
| `shorttermbdspaya_tongbi` | number | shorttermbdspaya 同比 |
| `shorttermborr_tongbi` | number | shorttermborr 同比 |
| `specpaya_tongbi` | number | specpaya 同比 |
| `specrese_tongbi` | number | specrese 同比 |
| `subsrece_tongbi` | number | subsrece 同比 |
| `taxespaya_tongbi` | number | taxespaya 同比 |
| `topaycashdivi_tongbi` | number | topaycashdivi 同比 |
| `totalcurrliab_tongbi` | number | totalcurrliab 同比 |
| `totalnoncassets_tongbi` | number | totalnoncassets 同比 |
| `totalnoncliab_tongbi` | number | totalnoncliab 同比 |
| `totasset_tongbi` | number | totasset 同比 |
| `totcurrasset_tongbi` | number | totcurrasset 同比 |
| `totliab_tongbi` | number | totliab 同比 |
| `totliabsharequi_tongbi` | number | totliabsharequi 同比 |
| `tradfinasset_tongbi` | number | tradfinasset 同比 |
| `tradfinliab_tongbi` | number | tradfinliab 同比 |
| `tradshartrad_tongbi` | number | tradshartrad 同比 |
| `treastk_tongbi` | number | treastk 同比 |
| `undiprof_tongbi` | number | undiprof 同比 |
| `unreinveloss_tongbi` | number | unreinveloss 同比 |
| `unseg_tongbi` | number | unseg 同比 |
| `warliabrese_tongbi` | number | warliabrese 同比 |

- **示例数据**:

```json
[
  {
    "report_period": "2026-03-31",
    "report_name": "2026一季报",
    "announcement_date": "2026-04-25",
    "currency": "CNY",
    "report_type": "合并期末",
    "data_source": "定期报告",
    "is_audit": "未审计",
    "bdspaya": 533429000000,
    "capisurp": 80598000000,
    "cenbankborr": 91774000000,
    "copeworkersal": 12235000000,
    "fdsborr": 69183000000,
    "fixedassenet": 10879000000,
    "generiskrese": 69520000000,
    "goodwill": 7568000000,
    "holdinvedue": 799583000000,
    "intaasset": 5556000000,
    "inveprop": 285000000,
    "leaseliab": 4075000000,
    "ocl": 64000000,
    "othdebtinvest": 151872000000,
    "othequin": 80000000000,
    "othequininvest": 4693000000,
    "perbond": 80000000000,
    "plac": 258285000000,
    "purcresaasset": 26530000000,
    "rese": 10781000000,
    "ruseassets": 3816000000,
    "sellrepasse": 111823000000,
    "taxespaya": 7970000000,
    "totasset": 6033962000000,
    "totliab": 5489879000000,
    "tradfinasset": 850131000000,
    "tradfinliab": 206427000000,
    "undiprof": 283714000000,
    "bdspaya_tongbi": -1.6889999999999998,
    "capisurp_tongbi": -0.13799999999999998,
    "cenbankborr_tongbi": -38.165,
    "copeworkersal_tongbi": -5.242999999999999,
    "fdsborr_tongbi": 43.419999999999995,
    "fixedassenet_tongbi": 29.526999999999997,
    "generiskrese_tongbi": 1.7670000000000001,
    "holdinvedue_tongbi": 2.823,
    "intaasset_tongbi": -7.922,
    "inveprop_tongbi": 7.142999999999999,
    "leaseliab_tongbi": -12.384,
    "ocl_tongbi": -95.184,
    "othdebtinvest_tongbi": -12.442,
    "othequin_tongbi": 14.363000000000001,
    "othequininvest_tongbi": -16.569,
    "perbond_tongbi": 60,
    "plac_tongbi": -4.199,
    "purcresaasset_tongbi": -1.295,
    "ruseassets_tongbi": -13.489,
    "sellrepasse_tongbi": 58.011,
    "taxespaya_tongbi": -42.146,
    "totasset_tongbi": 4.433,
    "totliab_tongbi": 4.138,
    "tradfinasset_tongbi": 59.663999999999994,
    "tradfinliab_tongbi": 87.03999999999999,
    "undiprof_tongbi": 10.99,
    "accheldfors": 0,
    "accopaya": 0,
    "accorece": 0,
    "accrexpe": 0,
    "accudepr": 0,
    "actitradsecu": 0,
    "actiundesecu": 0,
    "advapaym": 0,
    "amortizcostassets": 0,
    "avaisellasse": 0,
    "bdspayaperbond": 0,
    "bdspayaprest": 0,
    "comasse": 0,
    "consprog": 0,
    "consprogtot": 0,
    "contractasset": 0,
    "contractliab": 0,
    "copepoun": 0,
    "copewithreinrece": 0,
    "curfds": 0,
    "curtrandiff": 0,
    "defeincotaxliab": 0,
    "defereve": 0,
    "defetaxasset": 0,
    "deposit": 0,
    "derifinaasset": 0,
    "deriliab": 0,
    "deveexpe": 0,
    "dividrece": 0,
    "divipaya": 0,
    "dometicksett": 0,
    "duenoncliab": 0,
    "engimate": 0,
    "equiinve": 0,
    "expecurrliab": 0,
    "expenoncliab": 0,
    "expinoncurrasset": 0,
    "expotaxrebarece": 0,
    "fairvalueassets": 0,
    "fixedasseclea": 0,
    "fixedassecleatot": 0,
    "fixedasseimmo": 0,
    "fixedasseimpa": 0,
    "fixedassenetw": 0,
    "hydrasset": 0,
    "insucontrese": 0,
    "intelpay": 0,
    "intelrece": 0,
    "intepaya": 0,
    "interece": 0,
    "inteticksett": 0,
    "inve": 0,
    "lcopeworkersal": 0,
    "lendandloan": 0,
    "liabheldfors": 0,
    "logprepexpe": 0,
    "longborr": 0,
    "longdefeinco": 0,
    "longpaya": 0,
    "longpayatot": 0,
    "longrece": 0,
    "margrece": 0,
    "margrequ": 0,
    "minysharrigh": 0,
    "notesaccopaya": 0,
    "notesaccorece": 0,
    "notespaya": 0,
    "notesrece": 0,
    "othercurrasse": 0,
    "othercurreliabi": 0,
    "otherfeepaya": 0,
    "otherlonginve": 0,
    "othernoncasse": 0,
    "othernoncfinasse": 0,
    "othernoncliabi": 0,
    "otherpay": 0,
    "otherpaytot": 0,
    "otherrece": 0,
    "otherrecetot": 0,
    "paidincapi": 0,
    "paresharrigh": 0,
    "premrece": 0,
    "prep": 0,
    "prepexpe": 0,
    "prest": 0,
    "prodasse": 0,
    "recfinanc": 0,
    "reincontrese": 0,
    "reinrece": 0,
    "righaggr": 0,
    "settresedepo": 0,
    "shorttermbdspaya": 0,
    "shorttermborr": 0,
    "specpaya": 0,
    "specrese": 0,
    "subsrece": 0,
    "topaycashdivi": 0,
    "totalcurrliab": 0,
    "totalnoncassets": 0,
    "totalnoncliab": 0,
    "totcurrasset": 0,
    "totliabsharequi": 0,
    "tradshartrad": 0,
    "treastk": 0,
    "unreinveloss": 0,
    "unseg": 0,
    "warliabrese": 0,
    "accheldfors_tongbi": 0,
    "accopaya_tongbi": 0,
    "accorece_tongbi": 0,
    "accrexpe_tongbi": 0,
    "accudepr_tongbi": 0,
    "actitradsecu_tongbi": 0,
    "actiundesecu_tongbi": 0,
    "advapaym_tongbi": 0,
    "amortizcostassets_tongbi": 0,
    "avaisellasse_tongbi": 0,
    "bdspayaperbond_tongbi": 0,
    "bdspayaprest_tongbi": 0,
    "comasse_tongbi": 0,
    "consprog_tongbi": 0,
    "consprogtot_tongbi": 0,
    "contractasset_tongbi": 0,
    "contractliab_tongbi": 0,
    "copepoun_tongbi": 0,
    "copewithreinrece_tongbi": 0,
    "curfds_tongbi": 0,
    "curtrandiff_tongbi": 0,
    "defeincotaxliab_tongbi": 0,
    "defereve_tongbi": 0,
    "defetaxasset_tongbi": 0,
    "deposit_tongbi": 0,
    "derifinaasset_tongbi": 0,
    "deriliab_tongbi": 0,
    "deveexpe_tongbi": 0,
    "dividrece_tongbi": 0,
    "divipaya_tongbi": 0,
    "dometicksett_tongbi": 0,
    "duenoncliab_tongbi": 0,
    "engimate_tongbi": 0,
    "equiinve_tongbi": 0,
    "expecurrliab_tongbi": 0,
    "expenoncliab_tongbi": 0,
    "expinoncurrasset_tongbi": 0,
    "expotaxrebarece_tongbi": 0,
    "fairvalueassets_tongbi": 0,
    "fixedasseclea_tongbi": 0,
    "fixedassecleatot_tongbi": 0,
    "fixedasseimmo_tongbi": 0,
    "fixedasseimpa_tongbi": 0,
    "fixedassenetw_tongbi": 0,
    "goodwill_tongbi": 0,
    "hydrasset_tongbi": 0,
    "insucontrese_tongbi": 0,
    "intelpay_tongbi": 0,
    "intelrece_tongbi": 0,
    "intepaya_tongbi": 0,
    "interece_tongbi": 0,
    "inteticksett_tongbi": 0,
    "inve_tongbi": 0,
    "lcopeworkersal_tongbi": 0,
    "lendandloan_tongbi": 0,
    "liabheldfors_tongbi": 0,
    "logprepexpe_tongbi": 0,
    "longborr_tongbi": 0,
    "longdefeinco_tongbi": 0,
    "longpaya_tongbi": 0,
    "longpayatot_tongbi": 0,
    "longrece_tongbi": 0,
    "margrece_tongbi": 0,
    "margrequ_tongbi": 0,
    "minysharrigh_tongbi": 0,
    "notesaccopaya_tongbi": 0,
    "notesaccorece_tongbi": 0,
    "notespaya_tongbi": 0,
    "notesrece_tongbi": 0,
    "othercurrasse_tongbi": 0,
    "othercurreliabi_tongbi": 0,
    "otherfeepaya_tongbi": 0,
    "otherlonginve_tongbi": 0,
    "othernoncasse_tongbi": 0,
    "othernoncfinasse_tongbi": 0,
    "othernoncliabi_tongbi": 0,
    "otherpay_tongbi": 0,
    "otherpaytot_tongbi": 0,
    "otherrece_tongbi": 0,
    "otherrecetot_tongbi": 0,
    "paidincapi_tongbi": 0,
    "paresharrigh_tongbi": 0,
    "premrece_tongbi": 0,
    "prep_tongbi": 0,
    "prepexpe_tongbi": 0,
    "prest_tongbi": 0,
    "prodasse_tongbi": 0,
    "recfinanc_tongbi": 0,
    "reincontrese_tongbi": 0,
    "reinrece_tongbi": 0,
    "rese_tongbi": 0,
    "righaggr_tongbi": 0,
    "settresedepo_tongbi": 0,
    "shorttermbdspaya_tongbi": 0,
    "shorttermborr_tongbi": 0,
    "specpaya_tongbi": 0,
    "specrese_tongbi": 0,
    "subsrece_tongbi": 0,
    "topaycashdivi_tongbi": 0,
    "totalcurrliab_tongbi": 0,
    "totalnoncassets_tongbi": 0,
    "totalnoncliab_tongbi": 0,
    "totcurrasset_tongbi": 0,
    "totliabsharequi_tongbi": 0,
    "tradshartrad_tongbi": 0,
    "treastk_tongbi": 0,
    "unreinveloss_tongbi": 0,
    "unseg_tongbi": 0,
    "warliabrese_tongbi": 0
  }
]
```

### 现金流表(数据源SI)

- **函数**: `get_ch_si_stock_fin_cash_flow`
- **说明**: 从SI数据源获取个股现金流量表全量历史数据，含经营活动、投资活动、筹资活动三大现金流共61项科目
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001.SZ |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `report_period` | string | 报告期, YYYY-MM-DD |
| `report_name` | string | 报告名称 |
| `announcement_date` | string | 公告日期, YYYY-MM-DD |
| `currency` | string | 货币 |
| `report_type` | string | 报表类型 |
| `data_source` | string | 数据来源 |
| `is_audit` | string | 是否审计 |
| `acquassetcash` | number | 购建固定资产、无形资产和其他长期资产所支付的现金 |
| `bankloannetincr` | number | 向中央银行借款净增加额 |
| `bizcashinfl` | number | 经营活动现金流入小计 |
| `bizcashoutf` | number | 经营活动现金流出小计 |
| `cashfinalbala` | number | 现金的期末余额 |
| `cashnetr` | number | 现金及现金等价物净增加额 |
| `cashopenbala` | number | 现金的期初余额 |
| `charintecash` | number | 收取利息、手续费及佣金的现金 |
| `chgexchgchgs` | number | 汇率变动对现金及现金等价物的影响 |
| `debtpaycash` | number | 偿还债务支付的现金 |
| `deponetr` | number | 客户存款和同业存放款项净增加额 |
| `dispfinanetincrinve` | number | 处置可供出售金融资产净增加额 |
| `disptradnetincr` | number | 处置交易性金融资产净增加额 |
| `diviprofpaycash` | number | 分配股利、利润或偿付利息所支付的现金 |
| `equfinalbala` | number | 现金等价物的期末余额 |
| `equopenbala` | number | 现金等价物的期初余额 |
| `fdsborrnetr` | number | 拆入资金净增加额 |
| `finalcashbala` | number | 期末现金及现金等价物余额 |
| `fincashinfl` | number | 筹资活动现金流入小计 |
| `fincashoutf` | number | 筹资活动现金流出小计 |
| `fininstnetr` | number | 向其他金融机构拆入资金净增加额 |
| `finnetcflow` | number | 筹资活动产生的现金流量净额 |
| `finrelacash` | number | 支付其他与筹资活动有关的现金 |
| `fixedassetnetc` | number | 处置固定资产、无形资产和其他长期资产所收回的现金净额 |
| `incrcashpled` | number | 增加质押和定期存款所支付的现金 |
| `inicashbala` | number | 期初现金及现金等价物余额 |
| `insnetc` | number | 收到再保险业务现金净额 |
| `inspremcash` | number | 收到原保险合同保费取得的现金 |
| `invcashinfl` | number | 投资活动现金流入小计 |
| `invcashoutf` | number | 投资活动现金流出小计 |
| `inveretugetcash` | number | 取得投资收益收到的现金 |
| `invnetcashflow` | number | 投资活动产生的现金流量净额 |
| `invpayc` | number | 投资所支付的现金 |
| `invrececash` | number | 吸收投资收到的现金 |
| `issbdrececash` | number | 发行债券收到的现金 |
| `labopayc` | number | 购买商品、接受劳务支付的现金 |
| `laborgetcash` | number | 销售商品、提供劳务收到的现金 |
| `loannetr` | number | 质押贷款净增加额 |
| `loansnetr` | number | 客户贷款及垫款净增加额 |
| `mananetr` | number | 经营活动产生的现金流量净额 |
| `payacticash` | number | 支付的其他与经营活动有关的现金 |
| `paycompgold` | number | 支付原保险合同赔付款项的现金 |
| `paydivicash` | number | 支付保单红利的现金 |
| `payintecash` | number | 支付利息、手续费及佣金的现金 |
| `payinvecash` | number | 支付的其他与投资活动有关的现金 |
| `paytax` | number | 支付的各项税费 |
| `payworkcash` | number | 支付给职工以及为职工支付的现金 |
| `recefincash` | number | 收到其他与筹资活动有关的现金 |
| `recefromloan` | number | 取得借款收到的现金 |
| `receinvcash` | number | 收到的其他与投资活动有关的现金 |
| `receotherbizcash` | number | 收到的其他与经营活动有关的现金 |
| `reducashpled` | number | 减少质押和定期存款所收到的现金 |
| `repnetincr` | number | 回购业务资金净增加额 |
| `savinetr` | number | 保户储金及投资款净增加额 |
| `subsnetc` | number | 处置子公司及其他营业单位收到的现金净额 |
| `subspaydivid` | number | 子公司支付给少数股东的股利、利润 |
| `subspaynetcash` | number | 取得子公司及其他营业单位支付的现金净额 |
| `subsrececash` | number | 子公司吸收少数股东投资收到的现金 |
| `taxrefd` | number | 收到的税费返还 |
| `tradepaymnetr` | number | 存放中央银行和同业款项净增加额 |
| `withinvgetcash` | number | 收回投资所收到的现金 |
| `acquassetcash_tongbi` | number | acquassetcash 同比 |
| `bankloannetincr_tongbi` | number | bankloannetincr 同比 |
| `bizcashinfl_tongbi` | number | bizcashinfl 同比 |
| `bizcashoutf_tongbi` | number | bizcashoutf 同比 |
| `cashfinalbala_tongbi` | number | cashfinalbala 同比 |
| `cashnetr_tongbi` | number | cashnetr 同比 |
| `cashopenbala_tongbi` | number | cashopenbala 同比 |
| `charintecash_tongbi` | number | charintecash 同比 |
| `chgexchgchgs_tongbi` | number | chgexchgchgs 同比 |
| `debtpaycash_tongbi` | number | debtpaycash 同比 |
| `deponetr_tongbi` | number | deponetr 同比 |
| `dispfinanetincrinve_tongbi` | number | dispfinanetincrinve 同比 |
| `disptradnetincr_tongbi` | number | disptradnetincr 同比 |
| `diviprofpaycash_tongbi` | number | diviprofpaycash 同比 |
| `equfinalbala_tongbi` | number | equfinalbala 同比 |
| `equopenbala_tongbi` | number | equopenbala 同比 |
| `fdsborrnetr_tongbi` | number | fdsborrnetr 同比 |
| `finalcashbala_tongbi` | number | finalcashbala 同比 |
| `fincashinfl_tongbi` | number | fincashinfl 同比 |
| `fincashoutf_tongbi` | number | fincashoutf 同比 |
| `fininstnetr_tongbi` | number | fininstnetr 同比 |
| `finnetcflow_tongbi` | number | finnetcflow 同比 |
| `finrelacash_tongbi` | number | finrelacash 同比 |
| `fixedassetnetc_tongbi` | number | fixedassetnetc 同比 |
| `incrcashpled_tongbi` | number | incrcashpled 同比 |
| `inicashbala_tongbi` | number | inicashbala 同比 |
| `insnetc_tongbi` | number | insnetc 同比 |
| `inspremcash_tongbi` | number | inspremcash 同比 |
| `invcashinfl_tongbi` | number | invcashinfl 同比 |
| `invcashoutf_tongbi` | number | invcashoutf 同比 |
| `inveretugetcash_tongbi` | number | inveretugetcash 同比 |
| `invnetcashflow_tongbi` | number | invnetcashflow 同比 |
| `invpayc_tongbi` | number | invpayc 同比 |
| `invrececash_tongbi` | number | invrececash 同比 |
| `issbdrececash_tongbi` | number | issbdrececash 同比 |
| `labopayc_tongbi` | number | labopayc 同比 |
| `laborgetcash_tongbi` | number | laborgetcash 同比 |
| `loannetr_tongbi` | number | loannetr 同比 |
| `loansnetr_tongbi` | number | loansnetr 同比 |
| `mananetr_tongbi` | number | mananetr 同比 |
| `payacticash_tongbi` | number | payacticash 同比 |
| `paycompgold_tongbi` | number | paycompgold 同比 |
| `paydivicash_tongbi` | number | paydivicash 同比 |
| `payintecash_tongbi` | number | payintecash 同比 |
| `payinvecash_tongbi` | number | payinvecash 同比 |
| `paytax_tongbi` | number | paytax 同比 |
| `payworkcash_tongbi` | number | payworkcash 同比 |
| `recefincash_tongbi` | number | recefincash 同比 |
| `recefromloan_tongbi` | number | recefromloan 同比 |
| `receinvcash_tongbi` | number | receinvcash 同比 |
| `receotherbizcash_tongbi` | number | receotherbizcash 同比 |
| `reducashpled_tongbi` | number | reducashpled 同比 |
| `repnetincr_tongbi` | number | repnetincr 同比 |
| `savinetr_tongbi` | number | savinetr 同比 |
| `subsnetc_tongbi` | number | subsnetc 同比 |
| `subspaydivid_tongbi` | number | subspaydivid 同比 |
| `subspaynetcash_tongbi` | number | subspaynetcash 同比 |
| `subsrececash_tongbi` | number | subsrececash 同比 |
| `taxrefd_tongbi` | number | taxrefd 同比 |
| `tradepaymnetr_tongbi` | number | tradepaymnetr 同比 |
| `withinvgetcash_tongbi` | number | withinvgetcash 同比 |

- **示例数据**:

```json
{
  "report_period": "2026-03-31",
  "report_name": "2026一季报",
  "announcement_date": "2026-04-25",
  "currency": "CNY",
  "report_type": "合并期末",
  "data_source": "定期报告",
  "is_audit": "未审计",
  "acquassetcash": 172000000,
  "bizcashinfl": 330351000000,
  "bizcashoutf": 292549000000,
  "charintecash": 45519000000,
  "debtpaycash": 152000000000,
  "deponetr": 204605000000,
  "diviprofpaycash": 2077000000,
  "fincashinfl": 118970000000,
  "fincashoutf": 154604000000,
  "finnetcflow": -35634000000,
  "finrelacash": 30000000,
  "invcashinfl": 180885000000,
  "invcashoutf": 234402000000,
  "inveretugetcash": 6158000000,
  "invnetcashflow": -53517000000,
  "issbdrececash": 118970000000,
  "loansnetr": 86560000000,
  "mananetr": 37802000000,
  "payintecash": 19252000000,
  "paytax": 2865000000,
  "payworkcash": 8115000000,
  "withinvgetcash": 174703000000,
  "acquassetcash_tongbi": -49.112,
  "bizcashinfl_tongbi": -20.599,
  "bizcashoutf_tongbi": 15.581999999999999,
  "charintecash_tongbi": -6.173,
  "debtpaycash_tongbi": -35.313,
  "deponetr_tongbi": -0.8619999999999999,
  "diviprofpaycash_tongbi": -18.163999999999998,
  "fincashinfl_tongbi": 49.334,
  "fincashoutf_tongbi": -35.058,
  "finnetcflow_tongbi": 77.50399999999999,
  "finrelacash_tongbi": 328.57099999999997,
  "invcashinfl_tongbi": -28.560000000000002,
  "invcashoutf_tongbi": 2.693,
  "inveretugetcash_tongbi": -36.796,
  "invnetcashflow_tongbi": -314.557,
  "issbdrececash_tongbi": 49.334,
  "loansnetr_tongbi": 46.799,
  "mananetr_tongbi": -76.801,
  "payintecash_tongbi": -11.979,
  "paytax_tongbi": -44.206,
  "payworkcash_tongbi": 0.8829999999999999,
  "withinvgetcash_tongbi": -28.232000000000003,
  "bankloannetincr": 0,
  "cashfinalbala": 0,
  "cashnetr": 0,
  "cashopenbala": 0,
  "chgexchgchgs": 0,
  "dispfinanetincrinve": 0,
  "disptradnetincr": 0,
  "equfinalbala": 0,
  "equopenbala": 0,
  "fdsborrnetr": 0,
  "finalcashbala": 0,
  "fininstnetr": 0,
  "fixedassetnetc": 0,
  "incrcashpled": 0,
  "inicashbala": 0,
  "insnetc": 0,
  "inspremcash": 0,
  "invpayc": 0,
  "invrececash": 0,
  "labopayc": 0,
  "laborgetcash": 0,
  "loannetr": 0,
  "payacticash": 0,
  "paycompgold": 0,
  "paydivicash": 0,
  "payinvecash": 0,
  "recefincash": 0,
  "recefromloan": 0,
  "receinvcash": 0,
  "receotherbizcash": 0,
  "reducashpled": 0,
  "repnetincr": 0,
  "savinetr": 0,
  "subsnetc": 0,
  "subspaydivid": 0,
  "subspaynetcash": 0,
  "subsrececash": 0,
  "taxrefd": 0,
  "tradepaymnetr": 0,
  "bankloannetincr_tongbi": 0,
  "cashfinalbala_tongbi": 0,
  "cashnetr_tongbi": 0,
  "cashopenbala_tongbi": 0,
  "chgexchgchgs_tongbi": 0,
  "dispfinanetincrinve_tongbi": 0,
  "disptradnetincr_tongbi": 0,
  "equfinalbala_tongbi": 0,
  "equopenbala_tongbi": 0,
  "fdsborrnetr_tongbi": 0,
  "finalcashbala_tongbi": 0,
  "fininstnetr_tongbi": 0,
  "fixedassetnetc_tongbi": 0,
  "incrcashpled_tongbi": 0,
  "inicashbala_tongbi": 0,
  "insnetc_tongbi": 0,
  "inspremcash_tongbi": 0,
  "invpayc_tongbi": 0,
  "invrececash_tongbi": 0,
  "labopayc_tongbi": 0,
  "laborgetcash_tongbi": 0,
  "loannetr_tongbi": 0,
  "payacticash_tongbi": 0,
  "paycompgold_tongbi": 0,
  "paydivicash_tongbi": 0,
  "payinvecash_tongbi": 0,
  "recefincash_tongbi": 0,
  "recefromloan_tongbi": 0,
  "receinvcash_tongbi": 0,
  "receotherbizcash_tongbi": 0,
  "reducashpled_tongbi": 0,
  "repnetincr_tongbi": 0,
  "savinetr_tongbi": 0,
  "subsnetc_tongbi": 0,
  "subspaydivid_tongbi": 0,
  "subspaynetcash_tongbi": 0,
  "subsrececash_tongbi": 0,
  "taxrefd_tongbi": 0,
  "tradepaymnetr_tongbi": 0
}
```

### 个股财务核心指标(数据源Ea)

- **函数**: `get_ch_ea_stock_fin_key_indicators`
- **说明**: 获取指定个股财务核心指标数据（数据源Ea），包含每股指标、盈利能力、增长能力、偿债能力、营运能力、员工与研发等指标，数据从上市至今
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `basic_eps` | number | 基本每股收益(元) BASIC_EPS |
| `diluted_eps` | number | 稀释每股收益(元) DILUTED_EPS |
| `ttm_eps` | number | TTM每股收益(元) EPS_TTM |
| `bvps` | number | 每股净资产(元) BPS |
| `ops_cash_per_share` | number | 每股经营现金流(元) PER_NETCASH_OPERATE |
| `ops_rev_per_share` | number | 每股营业收入(元) PER_OI |
| `total_revenue` | number | 营业总收入(元) OPERATE_INCOME |
| `revenue_yoy` | number | 营业总收入同比增长(%) OPERATE_INCOME_YOY |
| `revenue_qoq` | number | 营业总收入滚动环比增长(%) OPERATE_INCOME_QOQ |
| `gross_profit` | number | 毛利润(元) GROSS_PROFIT |
| `gp_yoy` | number | 毛利润同比增长(%) GROSS_PROFIT_YOY |
| `gp_qoq` | number | 毛利润滚动环比增长(%) GROSS_PROFIT_QOQ |
| `net_profit` | number | 归母净利润(元) HOLDER_PROFIT |
| `np_yoy` | number | 归母净利润同比增长(%) HOLDER_PROFIT_YOY |
| `np_qoq` | number | 归母净利润滚动环比增长(%) HOLDER_PROFIT_QOQ |
| `tax_to_profit` | number | 所得税/利润总额(%) TAX_EBT |
| `ops_cf_to_rev` | number | 经营现金流/营业收入(%) OCF_SALES |
| `avg_roe` | number | 平均净资产收益率(%) ROE_AVG |
| `ann_roe` | number | 年化净资产收益率(%) ROE_YEARLY |
| `roa` | number | 总资产净利率(%) ROA |
| `gross_margin` | number | 毛利率(%) GROSS_PROFIT_RATIO |
| `net_margin` | number | 净利率(%) NET_PROFIT_RATIO |
| `ann_roi` | number | 年化投资回报率(%) ROIC_YEARLY |
| `ar_turnover` | number | 应收账款周转率(次) 注意：原始数据中是周转天数 |
| `inv_turnover` | number | 存货周转率(次) 注意：原始数据中是周转天数 |
| `ca_turnover` | number | 流动资产周转率(次) 注意：原始数据中是周转天数 |
| `ta_turnover` | number | 总资产周转率(次) 注意：原始数据中是周转天数 |
| `current_ratio` | number | 流动比率(倍) CURRENT_RATIO |
| `curr_liab_ratio` | number | 流动负债/总负债(%) CURRENTDEBT_DEBT |
| `debt_ratio` | number | 资产负债率(%) DEBT_ASSET_RATIO |
| `equity_multi` | number | 权益乘数 EQUITY_MULTIPLIER |
| `equity_ratio` | number | 产权比率 EQUITY_RATIO |
| `tag_date` | string | 报告日期 |
| `report_type` | string | 报告类型 |

- **示例数据**:

```json
[
  {
    "secucode": "000001.SZ",
    "security_code": "000001",
    "security_name_abbr": "平安银行",
    "report_date": "2026-03-31 00:00:00",
    "report_type": "一季报",
    "notice_date": "2026-04-25 00:00:00",
    "epsjb": 0.67,
    "epsxs": 0.67,
    "bps": 23.91,
    "mgzbgj": 4.153251571679,
    "mgwfplr": 14.619911367618,
    "mgjyxjje": 1.947954240956,
    "totaloperatereve": 35277000000,
    "parentnetprofit": 14523000000,
    "kcfjcxsyjlr": 14488000000,
    "roejq": 2.83,
    "roekcjq": 2.83,
    "xsjll": 41.1684667064,
    "zzcjll": 0.2428648317,
    "taxrate": 16.5296856141,
    "totaloperaterevetz": 4.65157673025,
    "parentnetprofittz": 3.02922814983,
    "kcfjcxsyjlrtz": 3.168838567258,
    "epsjbtz": 8.064516129032,
    "jyxjlyysr": 1.071576381212,
    "zcfzl": 90.9829892863,
    "qycs": 11.090149848449,
    "zzczzts": 15256.0664180975,
    "toazzl": 0.005899292618,
    "epsskcjb": 0,
    "mlr": 0,
    "roic": 0,
    "xsmll": 0,
    "xsjxlyysr": 0,
    "xjllb": 0,
    "ld": 0,
    "sd": 0,
    "cash_ratio": 0,
    "chzzts": 0,
    "yszkzzts": 0,
    "operate_cycle": 0,
    "chzzl": 0,
    "yszkzzl": 0,
    "staff_num": 0,
    "avg_toi": 0,
    "avg_net_profit": 0,
    "rdp_personnel": 0,
    "pratio": 0,
    "rdexpend": 0
  }
]
```

### 个股资产负债表(数据源Ea)

- **函数**: `get_ch_ea_stock_fin_balance_sheet`
- **说明**: 获取指定个股资产负债表数据（数据源Ea），包含总资产、固定资产、货币资金、应收账款、存货、总负债、应付账款、股东权益等，数据从上市至今
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `secucode` | string | 股票代码(带市场) |
| `report_date` | string | 报告日期 |
| `report_type` | string | 报告类型 |
| `total_assets` | number | 总资产(元) |
| `fixed_asset` | number | 固定资产(元) |
| `monetaryfunds` | number | 货币资金(元) |
| `accounts_rece` | number | 应收账款(元) |
| `inventory` | number | 存货(元) |
| `total_liabilities` | number | 总负债(元) |
| `accounts_payable` | number | 应付账款(元) |
| `total_equity` | number | 股东权益合计(元) |
| `current_ratio` | number | 流动比率(%) |
| `debt_asset_ratio` | number | 资产负债率(%) |

- **示例数据**:

```json
[
  {
    "secucode": "000001.SZ",
    "security_code": "000001",
    "security_name_abbr": "平安银行",
    "report_date": "1992-12-31 00:00:00",
    "total_assets": 7522847373.55,
    "monetaryfunds": 63204110.61,
    "total_liabilities": 195893209.32,
    "total_equity": 545662197.55,
    "current_ratio": 32.2645745758,
    "debt_asset_ratio": 2.6039769198,
    "report_type": "",
    "notice_date": "",
    "fixed_asset": 0,
    "accounts_rece": 0,
    "inventory": 0,
    "accounts_payable": 0,
    "short_loan": 0
  }
]
```

### 个股利润表(数据源Ea)

- **函数**: `get_ch_ea_stock_fin_income_statements`
- **说明**: 获取指定个股利润表数据（数据源Ea），包含营业总收入、营业总成本、销售费用、管理费用、财务费用、营业利润、净利润等，数据从上市至今
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `secucode` | string | 股票代码(带市场) |
| `report_date` | string | 报告日期 |
| `report_type` | string | 报告类型 |
| `total_operate_income` | number | 营业总收入(元) |
| `total_operate_cost` | number | 营业总成本(元) |
| `operate_cost` | number | 营业成本(元) |
| `sale_expense` | number | 销售费用(元) |
| `manage_expense` | number | 管理费用(元) |
| `finance_expense` | number | 财务费用(元) |
| `operate_profit` | number | 营业利润(元) |
| `total_profit` | number | 利润总额(元) |
| `income_tax` | number | 所得税(元) |
| `parent_netprofit` | number | 归母净利润(元) |
| `deduct_parent_netprofit` | number | 扣非归母净利润(元) |

- **示例数据**:

```json
[
  {
    "secucode": "000001.SZ",
    "security_code": "000001",
    "security_name_abbr": "平安银行",
    "report_date": "1991-12-31 00:00:00",
    "total_operate_income": 334690000,
    "total_operate_cost": 188230000,
    "operate_profit": 150180000,
    "total_profit": 150180000,
    "parent_netprofit": 112650000,
    "report_type": "",
    "notice_date": "",
    "operate_cost": 0,
    "sale_expense": 0,
    "manage_expense": 0,
    "finance_expense": 0,
    "operate_tax_add": 0,
    "invest_income": 0,
    "income_tax": 0,
    "deduct_parent_netprofit": 0
  }
]
```

### 个股现金流量表(数据源Ea)

- **函数**: `get_ch_ea_stock_fin_cash_flow`
- **说明**: 获取指定个股现金流量表数据（数据源Ea），包含经营活动、投资活动、筹资活动现金流净额等，数据从上市至今
- **请求参数**:

| 参数名 | 类型 | 必填 | 说明 |
|--------|------|------|------|
| `code` | string | 是 | 个股代码，如 000001 |

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `secucode` | string | 股票代码(带市场) |
| `report_date` | string | 报告日期 |
| `report_type` | string | 报告类型 |
| `netcash_operate` | number | 经营活动现金流净额(元) |
| `sales_services` | number | 销售商品收到现金(元) |
| `netcash_invest` | number | 投资活动现金流净额(元) |
| `construct_long_asset` | number | 购建固定资产支付(元) |
| `netcash_finance` | number | 筹资活动现金流净额(元) |
| `cce_add` | number | 现金净增加额(元) |

- **示例数据**:

```json
[
  {
    "secucode": "000001.SZ",
    "security_code": "000001",
    "security_name_abbr": "平安银行",
    "report_date": "2025-03-31 00:00:00",
    "notice_date": "2026-04-25 00:00:00",
    "netcash_operate": 162946000000,
    "pay_staff_cash": 8044000000,
    "netcash_invest": 24943000000,
    "construct_long_asset": 338000000,
    "netcash_finance": -158398000000,
    "cce_add": 29361000000,
    "report_type": "",
    "sales_services": 0
  }
]
```

---

## 可转债

### 订阅可转债实时行情通道

- **函数**: `subscribe_ch_kzz_stock_real`
- **说明**: 订阅可转债实时行情通道，采用增量发送模式，数据包含五档盘口、Level2成交数据、主力资金流向等高级指标。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 数据时间 |
| `close` | number | 当前价 |
| `last_close` | number | 昨日收盘价 |
| `open` | number | 今日开盘价 |
| `high` | number | 今日最高价 |
| `low` | number | 今日最低价 |
| `pre_volume` | number | 前成交量 |
| `volume` | number | 成交量 |
| `amount` | number | 成交额（元） |
| `buy_five` | list | 买五档价 |
| `buy_five_vol` | list | 买五档量 |
| `sell_five` | list | 卖五档价 |
| `sell_five_vol` | list | 卖五档量 |
| `turnover` | number | 换手率（%） |
| `volume_ratio` | number | 量比 |
| `bid_ask_ratio` | number | 委比（%） |
| `inst_aggressive_buy_amount` | number | 主力主动净买额（万元） |
| `inst_net_amount` | number | 主力净流入（万元） |
| `l2_total_buy_vol` | number | 总买量 |
| `l2_total_sell_vol` | number | 总卖量 |
| `l2_deal_tick_num` | integer | L2逐笔成交数 |
| `l2_order_tick_num` | integer | L2逐笔委托数 |

- **示例数据**:

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "113647": {
      "time": "2026-05-26 15:00:02",
      "close": 125.097,
      "open": 124.88,
      "high": 125.806,
      "low": 124.801,
      "last_close": 124.953,
      "amount": 26031500,
      "volume": 20781,
      "pre_volume": 207810,
      "buy_five": [
        124.929,
        124.924,
        124.92,
        124.88,
        124.843
      ],
      "buy_five_vol": [
        1,
        1,
        2,
        2,
        2
      ],
      "sell_five": [
        125.164,
        125.167,
        125.198,
        125.214,
        125.25
      ],
      "sell_five_vol": [
        13,
        1,
        12,
        15,
        1
      ],
      "turnover": 1.42,
      "volume_ratio": 1.05,
      "bid_ask_ratio": -5.2,
      "inst_aggressive_buy_amount": 125.8,
      "inst_net_amount": -380.5,
      "l2_total_buy_vol": 350,
      "l2_total_sell_vol": 820,
      "l2_deal_tick_num": 456,
      "l2_order_tick_num": 890
    }
  }
}
```

### 获取可转债实时行情

- **函数**: `get_ch_kzz_cur_real`
- **说明**: 随时获取可转债全量实时行情数据，包括五档盘口、Level2资金流向、主力净买额、换手率等高级指标。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `time` | string | 数据时间 |
| `close` | number | 当前价 |
| `last_close` | number | 昨日收盘价 |
| `open` | number | 今日开盘价 |
| `high` | number | 今日最高价 |
| `low` | number | 今日最低价 |
| `pre_volume` | number | 前成交量 |
| `volume` | number | 成交量 |
| `amount` | number | 成交额（元） |
| `buy_five` | list | 买五档价 |
| `buy_five_vol` | list | 买五档量 |
| `sell_five` | list | 卖五档价 |
| `sell_five_vol` | list | 卖五档量 |
| `turnover` | number | 换手率（%） |
| `volume_ratio` | number | 量比 |
| `bid_ask_ratio` | number | 委比（%） |
| `inst_aggressive_buy_amount` | number | 主力主动净买额（万元） |
| `inst_net_amount` | number | 主力净流入（万元） |
| `l2_total_buy_vol` | number | 总买量 |
| `l2_total_sell_vol` | number | 总卖量 |
| `l2_deal_tick_num` | integer | L2逐笔成交数 |
| `l2_order_tick_num` | integer | L2逐笔委托数 |

- **示例数据**:

```json
{
  "code": 0,
  "message": "success",
  "data": {
    "113647": {
      "time": "2026-05-26 15:00:02",
      "close": 125.097,
      "open": 124.88,
      "high": 125.806,
      "low": 124.801,
      "last_close": 124.953,
      "amount": 26031500,
      "volume": 20781,
      "pre_volume": 207810,
      "buy_five": [
        124.929,
        124.924,
        124.92,
        124.88,
        124.843
      ],
      "buy_five_vol": [
        1,
        1,
        2,
        2,
        2
      ],
      "sell_five": [
        125.164,
        125.167,
        125.198,
        125.214,
        125.25
      ],
      "sell_five_vol": [
        13,
        1,
        12,
        15,
        1
      ],
      "turnover": 1.42,
      "volume_ratio": 1.05,
      "bid_ask_ratio": -5.2,
      "inst_aggressive_buy_amount": 125.8,
      "inst_net_amount": -380.5,
      "l2_total_buy_vol": 350,
      "l2_total_sell_vol": 820,
      "l2_deal_tick_num": 456,
      "l2_order_tick_num": 890
    }
  }
}
```

### 获取可转债列表

- **函数**: `get_ch_kzz_stock`
- **说明**: 获取所有可转债的基本信息列表，包括代码、名称、正股、转股价、溢价率、到期日等核心参数。

- **响应字段**:

| 字段名 | 类型 | 说明 |
|--------|------|------|
| `code` | string | 可转债代码 |
| `name` | string | 可转债名称 |
| `underlying_stock` | string | 正股代码 |
| `price` | number | 可转债现价（元） |
| `underlying_stock_price` | number | 正股价（元） |
| `convert_price` | number | 最新转股价（元） |
| `convert_value` | number | 转股价值（元） |
| `conversion_premium` | number | 转股溢价率（%） |
| `convert_rate` | number | 转股价值 |
| `outstanding_volume` | number | 未转股余额（万元） |
| `cur_rate` | number | 当期利率（%） |
| `time_to_market` | string | 上市日期 |
| `end_date` | string | 到期日期 |
| `end_price` | number | 到期赎回价（元） |
| `convert_date` | string | 转股起始日 |
| `put_back_price` | number | 回售价（元） |
| `redeem_date` | string | 赎回日期 |
| `redeem_price` | number | 赎回价格（元） |
| `force_redeem_price` | number | 强赎触发价（元） |
| `score` | number | 评分 |
| `main_score` | number | 主力评分 |
| `convert_code` | string | 转股代码 |

- **示例数据**:

```json
[
  {
    "code": "123061",
    "name": "航新转债",
    "outstanding_volume": 1154100,
    "time_to_market": "2020-08-18",
    "underlying_stock": "300424",
    "convert_price": 14.82,
    "cur_rate": 3,
    "put_back_price": 10.37,
    "convert_date": "2021-01-28",
    "end_price": 118,
    "end_date": "2026-07-22",
    "convert_rate": 53.836,
    "score": "BBB",
    "redeem_date": "2026-07-07",
    "redeem_price": 102.885,
    "convert_code": "123061",
    "underlying_stock_price": 18.49,
    "price": 129,
    "conversion_premium": 3.4,
    "convert_value": 124.764,
    "force_redeem_price": 19.27,
    "main_score": "BBB",
    "real_value": 0,
    "expire_yield": 0,
    "put_price": 0,
    "put_date": ""
  }
]
```

---


