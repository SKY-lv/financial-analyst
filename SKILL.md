# Financial Analysis Agent Skill

> AI-powered financial data analysis and investment insights

## 功能

- **财务报表分析** - 自动解析资产负债表、利润表、现金流量表
- **估值模型** - DCF、PE/PB比较、相对估值
- **风险评估** - 财务风险指标计算
- **趋势预测** - 基于历史数据的预测分析
- **投资建议** - 综合分析给出投资评级

## 使用场景

```
用户: 分析一下苹果公司的财务状况
Agent: [调用financial-analyst skill获取财务数据，生成分析报告]
```

## 工具函数

### `analyze_financial_statements(ticker, period='annual')`

分析上市公司财务报表。

**参数:**
- `ticker` (str): 股票代码 (如 AAPL, TSLA)
- `period` (str): 'annual' 或 'quarterly'

**返回:**
```python
{
    "company": "Apple Inc.",
    "metrics": {
        "revenue_growth": 0.08,
        "gross_margin": 0.44,
        "net_margin": 0.25,
        "roe": 0.147,
        "current_ratio": 0.98,
        "debt_to_equity": 1.87
    },
    "highlights": [
        "收入同比增长8%",
        "毛利率稳定在44%",
        "ROE高于行业平均"
    ],
    "risks": [
        "流动比率低于1，短期偿债能力需关注"
    ]
}
```

### `calculate_valuation(ticker, method='dcf')`

计算公司估值。

**参数:**
- `ticker` (str): 股票代码
- `method` (str): 'dcf', 'pe', 'pb', 'ev_ebitda'

**返回:**
```python
{
    "method": "DCF",
    "fair_value": 185.50,
    "current_price": 175.20,
    "upside": 0.059,
    "assumptions": {
        "wacc": 0.09,
        "growth_rate": 0.05,
        "terminal_growth": 0.025
    }
}
```

### `compare_peers(ticker)`

同行业对比分析。

### `risk_assessment(ticker)`

财务风险评估。

## 配置

```json
{
    "data_sources": {
        "primary": "yahoo_finance",
        "secondary": "alpha_vantage"
    },
    "cache_ttl": 3600,
    "default_currency": "USD"
}
```

## 示例

```python
# 分析苹果财务
report = analyze_financial_statements('AAPL')
print(f"收入增长: {report['metrics']['revenue_growth']*100:.1f}%")

# DCF估值
valuation = calculate_valuation('AAPL', 'dcf')
print(f"合理估值: ${valuation['fair_value']}")
```

## 安装

```bash
clawhub install SKY-lv/financial-analyst
```

## License

MIT
