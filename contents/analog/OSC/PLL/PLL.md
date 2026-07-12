# PLL 学習ログ

## 📊 進捗リスト

| STEP | ステータス | 学習テーマ |
| :--- | :---: | :--- |
| **STEP 1** | ✅ 完了 | PLLの全体像と位相領域の考え方 |
| **STEP 2** | 🏃 進行中 |  |
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


<details>
<summary><b>Day 4：Integer-N PLLのロック条件を理解する</b></summary>

* Day4：Integer-N PLLロック条件を理解する
	* ロック時の Fout / N = Fref を導出する
	* 位相誤差がゼロまたは一定値になる意味を整理する
	* 周波数ロックと位相ロックの違いを説明する
* Integer-N PLLは$f_{ref}=f_{div}$となるようにフィードバックをかける
	* $f_{div}=f_{out}/N$より
	* $f_{out}=N\times f_{ref}$
* $f_{e}=f_{ref}-f_{div}=0$のとき
	* $\omega_{ref}-\omega_{div}=0$となるので
	* $\frac{d}{dt}(\phi_{ref}-\phi_{div})=Const\,or\,0$となる
	* $\phi_{ref}-\phi_{div}=Const\,or\,0$となる
	* 位相ロックしているならば周波数はロックしている
	* 周波数ロックしているとしても位相差は0とは限らず一定値をとるかもしれない
* Type-Ⅰ PLLとType-Ⅱ PLL
  * TypeはPLLのループ内に含まれる積分器の数を表す
  * VCOは積分動作のため必ずType-Ⅰ以上にはなる

</details>
</details>

<details>
<summary><b>STEP 2. 線形モデル、ループ帯域、安定性</b></summary>


<details>
<summary><b>Day 1. PFD/CPのゲインを定義する</b></summary>

* Day1 ：PFD/CPのゲインを定義する
	* PFD/CPを位相差から電流への変換器としてモデル化する
	* KPD の単位を確認する
	* CP電流と位相誤差の関係を理解する
		* CPはPFDの出力パルスが出ているときだけ電流$I_{CP}$を流す
		  * 1周期あたりの平均電流は$I_{CP}\times \frac{(パルスの幅)}{2\pi}$
		  * $I_{avg} = \frac{\phi_e}{2\pi}I_{CP}$
		  * PFD/CPへの入力は位相$\phi_e$で出力は$I_{avg}$より
		    * ゲイン$K_{PD}$は$K_{PD}=\frac{I_{CP}}{2\pi}$で表せる
			* 単位は$A/rad$
</details>

<details>
<summary><b>Day 2:VCOを積分器としてモデル化する</b></summary>

* Day2 :VCOを積分器としてモデル化する
	* $K_{VCO}$の単位を確認する
    	* Hz/V 
		* rad/s/V
	* VCOは2種類の見方が可能
    	* 電圧によって周波数を制御
        	* ゲインはHz/V
			* 角速度を制御していると考えると
              * ゲインはrad/s/V
	* 位相領域でVCOが$K_{VCO}/s$になることを理解する
		* $\omega_{out}=\omega_{0}+K_{VCO}\times V_{CNT}$
		* $\phi_{out}=\phi_{0}+\omega_{0}t+K_{VCO}\int V_{CNT}dt$
		* $\phi_{out}=\frac{K_{VCO}V_{CNT}}{s}$
	* VCOゲインが大きいと何が起きるかを整理する
		* PLLのループゲイン増大
  		* 周波数可変範囲を広げやすい
		* ノイズに敏感になる
</details>

<details>
<summary><b>Day 3:Loop Filterをs領域で表す</b></summary>

* Day 3：Loop Filterをs領域で表す
  * PLLの開ループの伝達関数は
    * $L(s) = \frac{K_{PD}K_{VCO}Z(s)}{Ns}$で表せる  
  	$Z(s)$はLoop Filterのインピーダンス
  * RCフィルタのインピーダンス Z(s) を書く
	* 1次のローパスフィルタの場合CPから見たインピーダンスは
    	* $Z(s) = \frac{sRC+1}{sC}$
	* 開ループ伝達関数に$Z(s)$を代入すると
    	* 原点にpoleを2つもち、zeroを1つもつ
		* 積分器が二つあるのでTypeⅡのPLL
	* 閉ループの伝達関数の分母は$1+L(s)$で決まる
    	* 分母は$s^2+2\zeta \omega n+\omega^2$の形になるためorderは2次になる
* 2次PLLと3次PLLの違いを理解する
  * zeroとpoleの意味を整理する
  * reference spurやVCOの制御電圧のリップルを防ぐためにLPFの次数を増やすことを実際には行うことが多い
    * CPの後にCPと1次LPFの手前に容量を対GNDに1つ追加する
      * poleが高周波に一つ増える
        * 追加のpoleは原点のpoleではないのでtypeⅡ
		* orderが3になる
		* 2つのpole+1つのzeroで-20dB/decでゲインが低下していたのが、2つの原点のpole+1つの高周波のpole+1つのzeroになるので追加のpoleで-40dB/decになる
</details>