
i = i([rem(pl*(Ns-1): pl*Ns-1,Ns)+1,1:
    N(1),rem(N(1): N(1)+pr-1,Ns)+1]);
end
case 'wshs' % Symmetric extension, WSHS
if all([pl,pr] < N(1))
    i = [pl+1: -1: 2,1: N(1),N(1): -1:
        N(1)-pr+1];
else
    i = [1: N(1),N(1): -1: 2];
    Ns = 2*N(1) - 1;
    i = i([rem(pl*(Ns-1): pl*Ns-1,Ns)+1,1:
        N(1),rem(N(1): N(1)+pr-1,Ns)+1]);
end
case 'hsws' % Symmetric extension, HSWS
    if all([pl,pr] < N(1))
        i = [pl: -1: 1,1: N(1),N(1)-1: -1:
        N(1)-pr];
    else
        i = [1: N(1),N(1)-1: -1: 1];
        Ns = 2*N(1) - 1;
        i = i([rem(pl*(Ns-1): pl*Ns-1,Ns)+1,1:
            N(1),rem(N(1): N(1)+pr-1,Ns)+1]);
    end
case 'zpd'
    M1 = N; M1(1) = pl;
    Mr = N; Mr(1) = pr;
    X = filter(B,1,[zeros(M1);X;zeros(Mr)],[],1);
    X = X(Z+pl+1: Z+pl+N(1),:,:);
    return;
case 'per'  % Periodic
    i = [rem(pl*(N(1)-1): pl*N(1)-1,N(1))+1,1:
        N(1),rem(0: pr-1,N(1))+1];
case 'sp0' % Constant extrapolation
    i = [ones(1,pl),1: N(1),N(1)+zeros(1,pr)];
case 'asym' % Asymmetric extension
    i1 = [ones(1,pl),1: N(1),N(1)+zeros(1,pr)];

    if all([pl,pr] < N(1))
        i2 = [pl+1: -1: 2,1: N(1),N(1)-1: -1:
            N(1)-pr];
    else
        i2 = [1: N(1),N(1)-1: -1: 2];
        Ns = 2*N(1) - 2 + (N(1) == 1);
        i2 = i2([rem(pl*(Ns-1): pl*Ns-1,Ns)+1,1:
            N(1),rem(N(1): N(1)+pr-1,Ns)+1]);

```matlab
else
        phi = phi/(norm(phi)*sqrt(dx)); % Rescale result
end

if nargin > 2
        phi2 = phi(1: 2: end); % phi2 is approximately
                phi(2x)
        if length(c) == 2
                L = length(phi2);
        else
                L = ceil(0.5/dx);
        end

        % Construct psi from translates of phi2
        c = g{1};
        psi = zeros(length(phi2)+L*(length(c)-1),1);
        x2 = (0: length(psi)-1)*dx - g{2} - 0*h{2}/2;

        for k = 1: length(c)
                i = (1: length(phi2)) + L*(k-1);
                psi(i) = psi(i) + c(k)*phi2;
        end
end
return;

function s = filterstr(a,K)
% Convert a filter to a string
[n,d] = rat(K/sqrt(2));
if d < 50
        a{1} = a{1}/sqrt(2); % Scale filter by sqrt(2)
        s = '{';
else
        s = '';
end

Scale = [pow2(1: 15),10,20,160,280,inf];

for i = 1: length(Scale)
        if norm(round(a{1}*Scale(i))/Scale(i) -
                a{1},inf) < 1e-9
                a{1} = a{1}*Scale(i); % Scale filter by a
                        power of 2 or 160
                s = '[';
                break;
        end
end
```

z = a{2};
LineOff = 0;

for k = 1: length(a{1})
    v = a{1}(k);
    if v ~= 0 % Only display nonzero coefficients
        if k > 1
            s2 = [' ',char(44-sign(v)),' '];
            v = abs(v);
        else
            s2 = '';
        end
        s2 = sprintf('%s%g',s2,v);
        if z == 1
            s2 = sprintf('%s z',s2);
        elseif z ~= 0
            s2 = sprintf('%s z^%d',s2,z);
        end
        if length(s) + length(s2) > 72 + LineOff % Wrap long lines
            s2 = [char(10),'  ',s2];
            LineOff = length(s);
        end
        s = [s,s2];
    end
z = z - 1;
end

if s(1) == '('
    s = [s,')'];
    if d < 50, s = [s,' sqrt(2)']; end

    if i < length(Scale)
        s = sprintf('%s/%d',s,Scale(i));
    end
end

return;

function N = numvanish(g)
% Determine the number of vanishing moments from
highpass filter g(z)

for N = 0: length(g)-1 % Count the number of roots at
z = 1

[g,r] = deconv(g,[1,-1]);
if norm(r,inf) > 1e-7, break; end
end
return;

function [iout,qout] = delay(idata,qdata,nsamp,idel)
iout = zeros(1,nsamp);
qout = zeros(1,nsamp);
if idel ~= 0
    iout(1: idel) = zeros(1,idel);
    qout(1: idel) = zeros(1,idel);
end
iout(idel+1: nsamp) = idata(1: nsamp-idel);
qout(idel+1: nsamp) = qdata(1: nsamp-idel);

function [iout,qout] = comb(idata,qdata,attn)
iout = randn(1,length(idata)).*attn;
qout = randn(1,length(qdata)).*attn;
iout = iout+idata(1: length(idata));
qout = qout+qdata(1: length(qdata));

function [iout,qout] = giins(idata,qdata,fftlen,gilen,nd);
idata1 = reshape(idata,fftlen,nd);
qdata1 = reshape(qdata,fftlen,nd);
idata2 = [idata1(fftlen-gilen+1: fftlen,: );idata1];
qdata2 = [qdata1(fftlen-gilen+1: fftlen,: );qdata1];
iout = reshape(idata2,1,(fftlen+gilen)*nd);
qout = reshape(qdata2,1,(fftlen+gilen)*nd);

function [iout,qout] = girem(idata,qdata,fftlen2,gilen,nd);
idata2 = reshape(idata,fftlen2,nd);
qdata2 = reshape(qdata,fftlen2,nd);
iout = idata2(gilen+1: fftlen2,: );
qout = qdata2(gilen+1: fftlen2,: );

function [iout,qout] = giins1(idata,qdata,fftlen,gilen,nd);
idata1 = reshape(idata,fftlen,nd);
qdata1 = reshape(qdata,fftlen,nd);
gg = gilen/2;
idata2 = [zeros(gg,nd);idata1(fftlen-gg+1: fftlen,: );idata1];

## 索引
### A
- ACI，见相邻信道干扰
- A/D转换器，见模数转换器
- 加性高斯白噪声（AWGN），54, 60, 104
  - 仿真参数，133
  - 正交频分复用，100
- 相邻信道干扰（ACI），115
- 高级加密标准（AES），1，21–24, 77, 134
  - AddRoundKey步骤，23
  - 密钥，22
  - 伽罗瓦域，22
  - MixColumns步骤，23
  - Rijndael算法，21
  - 轮数，22
  - S盒，22
  - ShiftRows步骤，22
  - 状态，21
  - 子密钥，23, 24
- 敌手，4, 6
- AES，见高级加密标准
- 混叠消除，97
- AM，见幅度调制
- 幅度调制（AM），91
- 幅移键控（ASK），91
- 模数（A/D）转换器，115
- ASDL，见非对称数字用户线
- ASK，见幅移键控
- 非对称数字用户线（ASDL），129
- 非对称加密，7
- 攻击
  - 暴力破解，9, 29, 49
  - 选择密文，10
  - 选择明文，9–10
  - 仅密文，9, 43
  - 已知明文，9
  - 中间相遇，14
  - 场景，3
- 认证方法，5
- 雪崩效应，37, 74, 81
- AWGN，见加性高斯白噪声

### B
- Baker映射，31–32
  - 混沌置换，31
  - 缺点，32
  - 示例，32
  - 像素图像，31
- 带通滤波器，96
- 比特循环图像加密（BRIE），30
- 黑盒，9
- 分组密码的特点，6
- 分组独立性问题，71
- Blowfish，16
- BRIE，见比特循环图像加密
- 暴力攻击，9, 29, 49
- 蝴蝶效应，28
- 基于混沌密钥的算法，30
- 混沌特性，28
- 确定性，29
- 混沌映射的遍历性，29
- 基于Kolmogorov流的图像加密技术，30
- 混沌系统的特性，29
- 伪随机性，28
- 研究领域，28
- SCAN语言，30
- 子密钥，31
- 对称分组密码算法，30
- 拓扑传递性，29
- 混沌密码学，1
- 不同工作模式下的混沌图像加密，57–69
  - 工作模式下的混沌加密，57–58
    - 框图，59
    - 主要目标，57
    - 工作模式，58
    - 实现问题，58–60
      - Baker映射，58
      - 分组大小，58–59
      - 辅助密钥，58
    - 安全性，59
    - 异或运算，58
  - 概述，57
    - 灰度图像，57
    - 安全性，57
    - 香农要求，57
  - 仿真示例与讨论，60–68
    - 加性高斯白噪声，60
    - Baker映射密码系统，64
    - 测试的分组大小，60
    - 解密图像，62
    - 直方图以及原始图像和加密图像，66
    - 抗噪性，60, 64

### C
- 凯撒密码，38, 39
- 载波频偏（CFOs），103
  - 补偿，108–109, 170
  - DCT-OFDM系统
    - 模型，107–108
  - DWT-OFDM系统
    - 模型，108
  - FFT-OFDM系统
    - 模型，105–106
  - 仿真参数，133
- CBC，见密码分组链接
- CCDF，见互补累积分布函数
- CDF，见累积分布函数
- CFB，见密码反馈
- CFOs，见载波频偏
- 混沌与密码学，28–31
  - 比特循环图像加密，30
  - 暴力攻击，29
  - 蝴蝶效应，28
