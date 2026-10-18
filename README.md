```mermaid
flowchart TD
    ROOT["<b>scutquant 量化工具箱</b><br/>华南理工大学量化投资协会<br/>全流程本地可跑 · 约 7000 行"]
 
    subgraph S1["① 数据获取板块"]
        A1["data.py<br/>基于 tushare 抓取行情"]
        A2["get_index_cons<br/>获取指数成分股"]
        A3["get_stock_data<br/>下载个股行情并复权"]
        A4["scutquant.py<br/>clean / join_data 数据清洗"]
        A5["data_tutorial.ipynb<br/>数据处理教程"]
    end
 
    subgraph S2["② 因子与模型板块"]
        B1["operators.py<br/>底层算子 ts_mean / ts_std"]
        B2["alpha.py<br/>因子工厂 qlib158 / qlib360"]
        B3["models.py<br/>神经网络 MLP / CNN / LSTM"]
        B4["econometrics.py<br/>GARCH / EGARCH / HAR"]
        B5["auto_process<br/>自动拆分与标准化"]
    end
 
    subgraph S3["③ 策略编写板块"]
        C1["strategy.py<br/>BaseStrategy 策略基类"]
        C2["QlibTopKStrategy<br/>现成的 TopK 换仓策略"]
        C3["raw_prediction_to_signal<br/>预测值转下单信号"]
        C4["get_trade_volume<br/>计算下单数量"]
        C5["account.py<br/>虚拟账户与风险控制"]
    end
 
    subgraph S4["④ 回测引擎板块"]
        D1["executor.py<br/>Executor 回测执行器"]
        D2["prepare<br/>整理成回测所需格式"]
        D3["execute<br/>逐日仿真交易并更新账户"]
        D4["report.py<br/>夏普 / 回撤 / 年化收益"]
        D5["report_all<br/>一键输出完整绩效报告"]
        D6["group_return_ana<br/>分层收益检验选股能力"]
    end
 
    subgraph S5["⑤ 实践案例与学习资料"]
        E1["tutorial.ipynb<br/>主教程 全流程演示"]
        E2["实践案例 / README.md<br/>5 条练手任务"]
        E3["技术因子测试<br/>149 个因子实测成绩单"]
        E4["文件 / 教材与技术沙龙<br/>因子投资 · bank_demo"]
    end
 
    ROOT --> S1
    S1 -->|加工后的干净数据| S2
    S2 -->|模型预测值| S3
    S3 -->|买卖指令| S4
    S5 -.->|照着手把手跑| S2
    S5 -.->|作业与验证| S4


