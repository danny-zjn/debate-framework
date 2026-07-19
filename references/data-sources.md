# 辩论数据源指南

本文档记录股票/公司类辩题的数据获取方式。

## 港股数据获取

### Python（akshare）

```python
import akshare as ak

# 核心财务指标（5年快照）
result = ak.stock_financial_hk_analysis_indicator_em(symbol="09660")
# 返回列包含：营收、营收增速、毛利、毛利率、净利润、EPS、BPS、
# 经营现金流/股、ROE、ROA 等

# 实时行情
result = ak.stock_hk_spot_em()

# 公司档案
result = ak.stock_hk_company_profile_em(symbol="09660")
```

### 腾讯行情 API

```bash
curl -s 'http://qt.gtimg.cn/q=hk09660'
```

## A股数据获取

### 实时行情

```bash
curl -s 'http://qt.gtimg.cn/q=sz300308'  # 深交所
curl -s 'http://qt.gtimg.cn/q=sh600519'  # 上交所
```

### 财务数据

```python
import akshare as ak

# 财务摘要（同花顺口径）
df = ak.stock_financial_abstract_ths(symbol='300308')

# 财务分析指标（含ROE等）
df2 = ak.stock_financial_analysis_indicator(symbol='300308', start_year='2021')
```

## 数据简报模板

股票类辩题的数据简报应包含：

| 指标 | 建议数据源 |
|------|-----------|
| 现价/市值/PE/PB | 腾讯行情 API |
| 营收+增速（3-5年） | akshare financial indicator |
| 毛利+毛利率趋势 | akshare financial indicator |
| 净利润+净利率 | akshare financial indicator |
| EPS/BPS | akshare financial indicator |
| 经营现金流/股 | akshare financial indicator |
| ROE | akshare financial indicator |
| 行业对比 | akshare 或 Wind（如有） |

## 已知坑

1. **代理冲突**：如果本机设置了 HTTP_PROXY 指向海外代理，akshare 访问东方财富等国内数据源会超时。调用前先 `unset HTTP_PROXY HTTPS_PROXY http_proxy https_proxy`
2. **港股数据可用性**：akshare 的港股财务指标覆盖不如 A 股完整，部分早期数据可能缺失
