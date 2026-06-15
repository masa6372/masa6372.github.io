---
tags:
    - 無線工学B
---

# 無線工学B

## アンテナ理論
- **電界強度の指向関数**  
<br>
電解強度の指向性関数 $ D(\theta) $
<br>
微小ダイポール　    $ D(\theta) = sin(\theta) $
<br>
半波長ダイポール    $ D(\theta) = \frac{cos(\frac{\pi}{2}cos\theta)}{sin(\theta)} $
<br>

- **電界強度**
<br>
微小ダイポールの電界強度   &thinsp;&nbsp;&nbsp;&nbsp;&nbsp; $ E = \frac{\sqrt{45p}}{d}$  [V/m]
<br>
半波長ダイポールの電界強度&nbsp;&nbsp;&nbsp;$ E = \frac{7\sqrt{p}}{d}$  [V/m]
<br>
アンテナの電解強度  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$E = \frac{30G \sqrt{p}}{d}$  [V/m] (Gはアンテナの絶対利得)
<br>
- **アンテナの実効長**  
<br>
電流分布が一様でないアンテナに対して、電流が一様分布したと確定したときの長さ
<br>
*半波長ダイポールアンテナの実効長*
<br>
$l_e= \frac{\lambda}{\pi}$
<br>
二線式折り返し半波長ダイポールの実効長は半波長ダイポールの二倍
<br>

- **アンテナの特性インピーダンス**
長さ$l_0$,直径$d$の素子の特性インピーダンス$Z_0$は
<br>
$ Z_0 = 138log_{10}\frac{2l_0}{d} \quad (l_0 = \frac{\lambda}{4}) $
<br>
短縮率$\varDelta$は
<br>
$ \varDelta = \frac{42.55}{\pi Z_0}$
<br>
短縮率を考慮したアンテナの長さ
<br>
$ l = \frac{\lambda}{4}(1 - \varDelta) $
<br>

- **開放線路のインピーダンス**
<br>
特性インピーダンス$Z_0$,長さ$l$の開放線路のインピーダンス$Z_F$
<br>
$ Z_F = -jZ_0 cot\beta l \quad(cot\theta = 1/tan\theta)$
<br>

- **微小ダイポールの絶対利得**
<br>
$1.76dB 1.5倍$
<br>

- **微小ダイポールの実効面積**
<br>
$ S_S = \frac{3\lambda^2}{8\pi}$
<br>

- **絶対利得Gのアンテナの実効面積**
<br>
$ S_S = \frac{G\lambda^2}{4\pi}$
<br>

- **アンテナの絶対利得**
<br>
開口面積$A$, 開口径$D$, 開口効率$\eta$のアンテナの絶対利得$G_I$
<br>
$ G_I = \eta \frac{4\pi A}{\lambda ^2} = \eta \frac{4\pi }{\lambda ^2} \times \pi (\frac{D}{2})^2 =(\frac{\pi D}{\lambda})^2 $
<br>

## 給電線
- **電圧反射係数**
電圧反射係数$\Gamma$の導出　給電線の特性インピーダンス$Z_0$負荷インピーダンスを$Z_R$とすると
<br>
$\Gamma = \frac{Z_R - Z_0}{Z_R + Z_0} $
<br>
- **電圧定在波比**
電圧定在波比$S$
<br>
$ S = \frac{1+|\Gamma|}{1-|\Gamma|} $


<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [無線工学B](#無線工学b)
  - [アンテナ理論](#アンテナ理論)
  - [給電線](#給電線)

<!-- /code_chunk_output -->
