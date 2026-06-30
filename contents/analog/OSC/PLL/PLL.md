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