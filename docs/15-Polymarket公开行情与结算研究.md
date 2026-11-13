# Polymarket 公开行情与结算研究

| 研究任务 | 公开数据来源 | 记录内容 |
|---|---|---|
| 识别合约 | Gamma 的事件与市场元数据 | 市场标识、结果标签、规则、截止时间和各结果的 token |
| 观察可成交价格 | CLOB 盘口与行情流 | 双边价格和数量、市场时间、接收时间 |
| 查看历史 | CLOB 历史价格 | 区间、采样粒度和缺失段 |
| 核对结果 | 平台结算结果、规则指定的参考行情 | 最终结算标签、参考品种、时区和对比窗口 |

每日 BTC 涨跌合约应逐场读取 Rules。用规则指定的参考来源和取价时间解释结果，再将平台公布的结算用作研究标签。盘口两个结果独立更新，比较报价时保留各自时间戳。流式连接断开后重新获取完整快照，再继续应用后续消息。

研究成交假设时要把可成交报价、盘口深度、费用和延迟计入成本。历史中间价或末笔成交价可描述价格路径，可成交量需要盘口数据支持。

参考 [Polymarket API](https://docs.polymarket.com/api-reference/predictions/overview)、[实时行情](https://docs.polymarket.com/market-data/realtime-data) 和 [Binance 公开行情数据](https://developers.binance.com/docs/binance-spot-api-docs/faqs/market_data_only)。
