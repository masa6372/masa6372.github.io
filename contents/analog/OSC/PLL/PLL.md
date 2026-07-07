# PLL 学習ログ

## 📊 進捗リスト

| STEP | ステータス | 学習テーマ |
| :--- | :---: | :--- |
| **STEP 1** | 🏃 進行中  | PLLの全体像と位相領域の考え方 |
| **STEP 2** | ⬜ 未着手 |  |
| **STEP 3** | ⬜ 未着手 |  |
| **STEP 4** | ⬜ 未着手 | |
| **STEP 5** | ⬜ 未着手  | |
| **STEP 6** | ⬜ 未着手 | |
| **STEP 7** | ⬜ 未着手 | |
| **STEP 8** | ⬜ 未着手 | |
| **STEP 9** | ⬜ 未着手 | |
| **STEP 10** | ⬜ 未着手 | |
| **STEP 11** | ⬜ 未着手 | |
| **STEP 12** | ⬜ 未着手 | |

## 📝 学習詳細ノート

<details>
<summary><b>STEP 1. PLLの全体像と位相領域の考え方</b></summary>

<details>
<summary><b>Day 1：PLLの用途を整理する  </b></summary>

* Day 1：PLLの用途を整理する  
	* RF synthesizer、clock generator、SerDes clock、jitter cleaner の違いを調べる
	* PLLは入力に対してLPF
     * PLLはVCOに対してHPF   
        * VCOがノイズ源か入力がノイズ源かでPLLを広帯域にするのか狭帯域にするのかが変わる
            - RF synthesizer
    			- 隣接する通信チャネルへ干渉したくないので特定のオフセット周波数における位相雑音を下げたい
    	  		- 入力ノイズとVCOノイズのバランスを重視
  			- Clock generator
    			- 入力を複数のクロックに分配
  			- SerDes Clock
    			- 高速通信用の信号で入力は水晶のようなクリーンな信号
    			- ジッタを極限まで下げたいので広帯域にする
  			- Jitter Cleaner
    			- 汚れた入力信号のジッタを低減したい
    			- 狭帯域にして外部から来る高ジッタ信号を低減

	* 出力周波数が Fout = N × Fref になる理由を説明できるようにする
		- Fout/N = Frefになるようにフィードバックがかけられるため
</details>
<details>
<summary><b>Day 2：基本ブロックを理解する</b></summary>

* Day 2：基本ブロックを理解する
	* PFD、CP、Loop Filter、VCO、Divider の役割を1枚の図にまとめる
	* 各ブロックの入力/出力信号を整理する
	* 位相、周波数、電圧、電流のどれを扱うブロックかを明確にする

	* PFD (Phase Frequency Detector)
    	* 帰還した信号とリファレンス信号を比較
        	* 周波数がロックするまでは周波数比較器として動作
        	* ロック後は位相比較器
      	* 位相差を進み、遅れに応じてデジタルパルスΔtで出力
			* リファレンスが早い→Upパルス
			* Feedbackが早い→Downパルス
  	* CP (Charge Pump)
		* デジタルパルスΔtの時間に応じて定電流源から電流を出力して容量を充放電
		* 時間情報を電荷に変換 $ Q = I_{CP}\delta t$
	* LF (Loop Filter)
		* チャージポンプからの電流を平滑化
		* 抵抗と容量のフィルタにより電流を電圧へ変換
	* VCO (Voltage Controlled Oscillator)
		* LFの出力に応じた出力周波数を発生
    * Divider
        * VCOの出力を1/N倍して入力へ帰還
</details>

<details>
<summary><b>Day 3：位相と周波数の関係を復習</b></summary>

* Day 3 位相と周波数の関係を復習
    * 周波数は位相の時間微分であることを確認
	* VCOを”入力電圧で位相の傾きが変わる積分器"として理解
	* VCO=integratorという視点を身に着ける
* 位相と周波数の関係
	* $\omega = \frac{d\phi}{dt}$
	* $\phi = \int \omega dt $
	* $\omega = 2\pi f$より
	* $\phi = 2\pi \int f dt$となるので、位相は周波数の時間積分
	* 反対に周波数は位相の時間微分

* VCOの伝達関数を考える
    * $\omega_{out}=K_{VCO}V_{CTRL}+\omega_{0}$で出力周波数が変動
    * $K_{VCO}$の単位は$rad/s/V$で表せる
	* $\omega_{out}=K_{VCO}V_{CTRL}+\omega_{0}$より
	* $\frac{d\phi}{dt} = \omega_{0}+K_{VCO}V_{CTRL}$が得られる
	* $\phi = K_{VCO}\int V_{CTRL}dt+\omega_{0} t$tに関して積分すると
	* 周波数領域に変換すると、伝達関数は
	* $\Phi = K_{VCO} V_{CTRL}/s$となる
	* $\frac{\Phi}{V_{CTRL}}(s) = \frac{K_{VCO}}{s} $が伝達関数として得られる
	* VCOは制御電圧を周波数に変換し、その周波数を積分して位相を出力するブロック

</details>
</details>