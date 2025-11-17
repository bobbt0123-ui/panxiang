# panxiang
基于六壬、六爻、奇门的事物规律推理项目

已建立写入连接。

panxiang/
├─ README.md
├─ pyproject.toml / setup.cfg        # 包管理 & 依赖声明
├─ src/
│  └─ panxiang/
│     ├─ __init__.py
│     ├─ config.py                   # 全局配置 & 策略开关（例如队伍五行策略）
│     ├─ types.py                    # 通用 dataclass / Enum 定义（Element, GoalRange 等）
│     │
│     ├─ core/                       # 核心“术数引擎”
│     │  ├─ __init__.py
│     │  ├─ time_layer.py            # 时间层：北京时间解析、Time1/Time2、昼夜标记
│     │  ├─ calendar_ganzhi.py       # 干支、月令、节气等（调用外部历法库）
│     │  ├─ wuxing.py                # 五行生克、关系函数 rel_to_me 等
│     │  ├─ team_element.py          # 队伍 → 五行 映射逻辑（哈希/人工表/混合）
│     │  ├─ yao_layer.py             # 六爻生成、动静、波动度计算
│     │  ├─ qi_layer.py              # 旺衰合成、气势 Q、波动度总评
│     │  ├─ patterns.py              # 模式识别：大胜/闷平/高比分平局等
│     │  └─ engine.py                # 把上面这些串成  I → T → E → S → Y → Q → P → R 的流水线
│     │
│     ├─ data/                       # 规则数据 & 配置数据
│     │  ├─ __init__.py
│     │  ├─ team_aliases.py          # 队伍别名表（规范化队名）
│     │  ├─ team_element_table.py    # 人工指定的队伍五行表（可选）
│     │  └─ league_meta.py           # 联赛统计特征（后期用，不参与当前环境五行）
│     │
│     ├─ ui/
│     │  ├─ __init__.py
│     │  ├─ cli.py                   # 命令行：读取批量比赛 → 输出结果 & 日志
│     │  └─ web_demo.py              # 预留 Web UI（例如 Streamlit/FastAPI）
│     │
│     ├─ logging_utils/
│     │  ├─ __init__.py
│     │  └─ tags_logger.py           # “过程标签化”日志输出（每一步的 I_*/T_*/M_*/Q_*）
│     │
│     └─ examples/
│        ├─ __init__.py
│        └─ sample_matches.py        # 你给的那些样例比赛，作为单元测试/演示
│
└─ tests/
   ├─ test_time_layer.py
   ├─ test_calendar_ganzhi.py
   ├─ test_team_element.py
   └─ test_engine_pipeline.py

