```
{
  "dataset_id": "outpatient_depression_v1",
  "patient_id": "P10086", 
  "demographics": {
    "age": 34,
    "gender": "female",
    "occupation": "teacher"  // 如果Excel里有就填，没有就null
  },
  "longitudinal_data": [  // 纵向数据的核心：列表里放多次就诊记录
    {
      "session_id": "P10086_visit_1",
      "visit_type": "initial",  // 初诊
      "date": "2023-10-01",     // 如果文件名或Excel里有日期
      "phq9_assessment": {      // 来自 Excel 的数据
        "total_score": 18,
        "severity": "Moderately severe", // 可以写逻辑自动根据分数生成
        "items": [3, 2, 1, 3, ...]       // 如果Excel里有细项分
      },
      "dialogue": [             // 参考 OpenAI 格式，方便未来训练
        {
          "turn_id": 1,
          "role": "doctor",
          "content": "最近睡眠情况怎么样？"
        },
        {
          "turn_id": 2,
          "role": "patient",
          "content": "非常糟糕，入睡很困难。"
        }
      ]
    },
    {
      "session_id": "P10086_visit_2",
      "visit_type": "follow_up", // 复诊
      "phq9_assessment": {
        "total_score": 12        // 分数下降，体现疗效
      },
      "dialogue": [ ... ]
    }
  ]
}
```
