

| --- | --- | --- | --- | --- |
| **2** || 55.9370 || 16.4208 || 45.8300 || 1.4018 |
| **3** || 55.7041 || 13.9121 || 40.3855 || 1.4856 |
| **4** || 55.6898 || 18.1791 || 47.2150 || 1.3757 |
| **5** || 55.6537 || 17.8955 || 49.3404 || 1.3982 |

表 7.16b 一个最优设计示例 [⏎](#chapter7.xhtml#b7tbl7_16b)

| 运行 || `apr` || `limit` || `rebate` || `color` || `brand` || `chan` |
| --- | --- | --- | --- | --- | --- | --- |
| 1 || 0 || 0 || 2 || 3 || 0 || 0 |
| --- | --- | --- | --- | --- | --- | --- |
| 2 || 0 || 0 || 3 || 3 || 1 || 1 |
| 3 || 0 || 0 || 2 || 2 || 1 || 0 |
| 4 || 0 || 0 || 3 || 2 || 0 || 1 |
| 5 || 0 || 0 || 3 || 1 || 0 || 0 |
| 6 || 0 || 0 || 1 || 0 || 0 || 1 |
| 7 || 0 || 0 || 3 || 0 || 1 || 0 |
| 8 || 0 || 1 || 0 || 2 || 1 || 1 |
| 9 || 0 || 3 || 0 || 3 || 1 || 0 |
| 10 || 0 || 3 || 2 || 3 || 0 || 1 |
| 11 || 0 || 3 || 0 || 2 || 0 || 0 |
| 12 || 0 || 3 || 0 || 1 || 0 || 1 |
| 13 || 0 || 3 || 2 || 1 || 1 || 0 |
| 14 || 0 || 3 || 0 || 0 || 1 || 1 |
| 15 || 1 || 0 || 0 || 3 || 0 || 1 |
| 16 || 1 || 0 || 0 || 1 || 1 || 0 |
| 17 || 1 || 3 || 0 || 2 || 1 || 0 |
| 18 || 1 || 3 || 3 || 0 || 0 || 1 |
| 19 || 2 || 1 || 3 || 3 || 1 || 0 |
| 20 || 2 || 2 || 0 || 1 || 0 || 0 |
| 21 || 2 || 3 || 3 || 2 || 1 || 1 |
| 22 || 2 || 3 || 2 || 1 || 0 || 1 |
| 23 || 2 || 3 || 0 || 0 || 0 || 0 |
| 24 || 3 || 0 || 0 || 3 || 1 || 0 |
| 25 || 3 || 0 || 0 || 2 || 0 || 0 |
| 26 || 3 || 0 || 2 || 2 || 1 || 1 |
| 27 || 3 || 0 || 0 || 1 || 0 || 1 |
| 28 || 3 || 0 || 0 || 0 || 1 || 1 |
| 29 || 3 || 0 || 2 || 0 || 0 || 0 |
| 30 || 3 || 1 || 3 || 1 || 1 || 1 |
| 31 || 3 || 2 || 3 || 3 || 0 || 1 |
| 32 || 3 || 2 || 2 || 2 || 0 || 0 |
| 33 || 3 || 3 || 0 || 3 || 1 || 1 |
| 34 || 3 || 3 || 1 || 3 || 0 || 0 |
| 35 || 3 || 3 || 0 || 2 || 0 || 1 |
| 36 || 3 || 3 || 3 || 1 || 0 || 0 |
| 37 || 3 || 3 || 3 || 0 || 1 || 0 |

一旦获得设计，下一步就是检查所需的效应是否真正可估计。以下 `SAS` 代码首先将连续属性的编码水平从 0-3 转换为实际值，然后进行中心化以减少相关性，

```
data optdesign; set optdesign;
cell=_n_;
run;
    
data try;
set
optdesign;
    
y=rannor(-1);
    
select (apr);
      when (0) aprn=4.9;
      when (1) aprn=6.9;
      when (2) aprn=9.9;
      otherwise aprn=11.9;
end;
    
/* limitn = actual limit/1000 */
select (limit);
      when (0) limitn=2.5;
      when (1) limitn=5;
      when (2) limitn=8;
      otherwise limitn=12;
end;
    
select (rebate);
      when (0) rebaten=0;
      when (1) rebaten=0.5;
      when (2) rebaten=1;
      otherwise rebaten=1.5;
end;
    
/* For color: color1=platinum, color2=gold, color3=diamond,
base color = green */
select (color);
      when (0) do; color1=0; color2=0; color3=0; end;
      when (1) do; color1=1; color2=0; color3=0; end;
      when (2) do; color1=0; color2=1; color3=0; end;
      otherwise do; color1=0; color2=0; color3=1; end;
end;
    
/* Centering to reduce correlations */
aprn=aprn-mean(4.9,6.9,9.9,11.9);
limitn=limitn-mean(2.5,5,8,12);
rebaten=rebaten-mean(0,0.5,1,1.5);
    
/* Squared terms for testing quadratic effects */
aprnsq=aprn*aprn;
limitnsq=limitn*limitn;
rebatensq=rebaten*rebaten;Page 187
    
/* Two-way interaction terms */
/* Consider all the following interaction terms:
apr*limit apr*color apr*rebate apr*brand apr*chan
limit*color limit*rebate limit*brand limit*chan
color*rebate color*brand color*chan
rebate*brand rebate*chan
brand*chan */
    
aprnlimitn=aprn*limitn;
aprncolor1=aprn*color1; aprncolor2=aprn*color2; aprncolor3=aprn*color3;
aprnrebaten=aprn*rebaten;
aprnbrand=aprn*brand;
aprnchan=aprn*chan;
    
limitncolor1=limitn*color1; limitncolor2=limitn*color2;
limitncolor3=limitn*color3;
limitnrebaten=limitn*rebaten;
limitnbrand=limitn*brand;
limitnchan=limitn*chan;
    
rebatencolor1=rebaten*color1; rebatencolor2=rebaten*color2;
rebatencolor3=rebaten*color3;
brandcolor1=brand*color1; brandcolor2=brand*color2; brandcolor3=brand*color3;
chancolor1=chan*color1; chancolor2=chan*color2; chancolor3=chan*color3;
    
rebatenbrand=rebaten*brand;
rebatenchan=rebaten*chan;
    
brandchan=brand*chan;
    
run;
    
/* Checking correlations of all main and two-way interactions for:
aprn limitn color rebaten brand chan; */
proc corr data=try;
var
aprn limitn color1-color3 rebaten brand chan
aprnsq limitnsq rebatensq
aprnlimitn aprncolor1-aprncolor3 aprnrebaten aprnbrand aprnchan
limitncolor1-limitncolor3 limitnrebaten limitnbrand limitnchan
rebatencolor1-rebatencolor3 brandcolor1-brandcolor3 chancolor1-chancolor3
rebatenbrand rebatenchan
brandchan
;
run;
    
/* Using GLM to check that all required effects are estimable */
proc glm data=try;
model y=
aprn limitn color1-color3 rebaten brand chan
aprnsq limitnsq rebatensq
aprnlimitn aprncolor1-aprncolor3 aprnrebaten aprnbrand aprnchanPage 188
limitncolor1-limitncolor3 limitnrebaten limitnbrand limitnchan
rebatencolor1-rebatencolor3 brandcolor1-brandcolor3 chancolor1-chancolor3
rebatenbrand rebatenchan
brandchan
/ noint e solution;
run;
```

表 7.17 `PROC GLM` 输出（开始部分）用于检查 D-最优设计的估计性（下方缺乏方程表示没有效应关联且所有参数均可估计） [⏎](#chapter7.xhtml#b7tbl7_17)

| 可估计函数的一般形式 |
| --- |
| 效应 || 系数 |
| `aprn` || L1 |
| --- | --- |
| `limitn` || L2 |
| `color1` || L3 |
| `color2` || L4 |
| `color3` || L5 |
| `rebaten` || L6 |
| `brand` || L7 |
| `chan` || L8 |
| `aprnsq` || L9 |
| `limitnsq` || L10 |
| `rebatensq` || L11 |
| `aprnlimitn` || L12 |
| `aprncolor1` || L13 |
| `aprncolor2` || L14 |
| `aprncolor3` || L15 |
| `aprnrebaten` || L16 |
| `aprnbrand` || L17 |
| `aprnchan` || L18 |
| `limitncolor1` || L19 |
| `limitncolor2` || L20 |
| `limitncolor3` || L21 |
| `limitnrebaten` || L22 |
| `limitnbrand` || L23 |
| `limitnchan` || L24 |
| `rebatencolor1` || L25 |
| `rebatencolor2` || L26 |
| `rebatencolor3` || L27 |
| `brandcolor1` || L28 |
| `brandcolor2` || L29 |
| `brandcolor3` || L30 |
| `chancolor1` || L31 |
| `chancolor2` || L32 |
| `chancolor3` || L33 |
| `rebatenbrand` || L34 |
| `rebatenchan` || L35 |
| `brandchan` || L36 |

