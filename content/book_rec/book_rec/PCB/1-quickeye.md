eyesource属性设置为：
3.2G

- trise=50 ps。
- tfall = 50 ps。
- UIorPBS 到 UnitInterval
- UIorBPSValue 为 UI，值为 1/3.2 G。
- 单击“BitPattern”按钮，打开“位模式数据”对话框

- 在位模式数据对话框中设置：
- 输入 PRBS 数据单选按钮
- PRBS 长度为 15
- PRBS 种子为 1
- 单击“确定”关闭“位模式数据”对话框

- DC取一點，1Hz~100MHz "by Decade"取20~30點，剩下取"Linear Step"。這樣的設定方法可以加強低頻取樣，避免後面抽出來的S-parameter模擬遇到不收斂的問題。

  10.1 Add Nport Model

  10.2 Add Eye Source and Probe

  10.3 Set Quick Eye Analysis

  10.4 Run Simulation

  10.5 Plot Eye Report
