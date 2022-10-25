---
tags:
    - 無線工学B
---

# 無線工学B

## アンテナ理論
- **電界強度の指向関数**
電解強度の指向性関数 $ D(\theta) $  
&nbsp;
微小ダイポール　    $ D(\theta) = sin(\theta) $  
&nbsp;
半波長ダイポール    $ D(\theta) = \frac{cos(\frac{\pi}{2}cos\theta)}{sin(\theta)} $  

&nbsp;
- **電界強度**
&nbsp;
微小ダイポールの電界強度   &thinsp;&nbsp;&nbsp;&nbsp;&nbsp; $ E = \frac{\sqrt{45p}}{d}$  [V/m] 
&nbsp;
半波長ダイポールの電界強度&nbsp;&nbsp;&nbsp;$ E = \frac{7\sqrt{p}}{d}$  [V/m] 
&nbsp;
アンテナの電解強度  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$E = \frac{30G \sqrt{p}}{d}$  [V/m] (Gはアンテナの絶対利得)

&nbsp;
- **アンテナの実効長**
_電流分布が一様でないアンテナに対して、電流が一様分布したと確定したときの長さ_
&nbsp;
半波長ダイポールアンテナの実効長&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$l_e= \frac{\lambda}{\pi}$
&nbsp;
二線式折り返し半波長ダイポールの実効長は半波長ダイポールの二倍
&nbsp;

- **アンテナの特性インピーダンス**
長さ$l_0$,直径$d$の素子の特性インピーダンス$Z_0$は
$ Z_0 = 138log_{10}\frac{2l_0}{d} \quad (l_0 = \frac{\lambda}{4}) $
&nbsp;
短縮率$\varDelta$は
$ \varDelta = \frac{42.55}{\pi Z_0}$
&nbsp;
短縮率を考慮したアンテナの長さ
$ l = \frac{\lambda}{4}(1 - \varDelta) $
&nbsp;

- **開放線路のインピーダンス**
特性インピーダンス$Z_0$,長さ$l$の開放線路のインピーダンス$Z_F$
$ Z_F = -jZ_0 cot\beta l \quad(cot\theta = 1/tan\theta)$
&nbsp;

- **微小ダイポールの絶対利得**
$1.76dB 1.5倍$
&nbsp;

- **微小ダイポールの実効面積**
$ S_S = \frac{3\lambda^2}{8\pi}$
&nbsp;

- **絶対利得Gのアンテナの実効面積**
$ S_S = \frac{G\lambda^2}{4\pi}$
&nbsp;

- **アンテナの絶対利得**
$開口面積A, 開口径D, 開口効率\etaのアンテナの絶対利得G_I$
$ G_I = \eta \frac{4\pi A}{\lambda ^2} = \eta \frac{4\pi }{\lambda ^2} \times \pi (\frac{D}{2})^2 =(\frac{\pi D}{\lambda})^2 $
&nbsp;