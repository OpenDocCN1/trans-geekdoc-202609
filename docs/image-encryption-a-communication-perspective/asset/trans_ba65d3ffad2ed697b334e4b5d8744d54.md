
% 绘制 Daubechies 2 尺度函数
% [x,phi] = wavelet('D2','phi');
% plot(x,phi);
%
% 参考文献：
% [1] M. Adams 和 F. Kossentini. “可逆整数-
% 到-整数小波变换用于图像压缩。”
% IEEE 图像处理汇刊, 第 9 卷, 第 6 期, 2000 年 6 月.
%
% [2] M. Antonini, M. Barlaud, P. Mathieu, 和
% I. Daubechies. “使用小波变换的图像编码
% 变换。” IEEE 图像处理汇刊, 第 1 卷,
% 第 205-220 页, 1992 年.
%
% [3] R. Calderbank, I. Daubechies, W. Sweldens, 和
% Boon-Lock Yeo. “使用整数到整数小波变换的无损图像压缩
% 整数到整数小波变换。” ICIP IEEE
% 出版社, 第 1 卷, 第 596-599 页, 1997 年.
%
% [4] I. Daubechies 和 W. Sweldens. “将小波
% 变换分解为提升步骤。” 1996 年.
%
% [5] D. Le Gall 和 A. Tabatabai. “子带编码
% 数字图像使用对称短核滤波器
% 和算术编码技术。” ICASSP'88,
% 第 761-765 页, 1988 年.
%
% [6] S. Mallat. “信号处理的 小波之旅。”
% Academic Press, 1999 年.
%
% [7] M. Unser 和 T. Blu. “JPEG2000 小波滤波器的数学特性
% 的” IEEE 图像处理汇刊
% 第 12 卷, 第 9 期, 2003 年 9 月.
%
% [8] Qinghai Wang 和 Yulong Mo. “JPEG2000 中小波基的选择
% ” 计算机工程, 第 30 卷,
% 第 23 期, 2004 年 12 月.
% Pascal Getreuer 2005-2006

if nargin < 1, error('Not enough input arguments.'); end
if ~ischar(WaveletName), error('Invalid wavelet name.'); end

% 获取指定小波的提升方案序列
% 小波

Flag1D = isempty(findstr(lower(WaveletName),'2d'));
[Seq,ScalesS,ScaleD,Family] = getwavelet(WaveletName);

if isempty(Seq)
    error(['Unknown wavelet, ''',WaveletName,''' .']);
end
if nargin < 2, Level = ''; end
if ischar(Level)
    [h1,g1] = seq2hg(Seq,ScalesS,ScaleD,0);
    [h2,g2] = seq2hg(Seq,ScalesS,ScaleD,1);

    if strcmpi(Level,'filters')
        varargout = {h1,g1,h2,g2};
    else
    if nargin < 3, X = 6; end

    switch lower(Level)
    case {'phi1','phi'}
    [x1,phi] = cascade(h1,g1,pow2(-X));
    varargout = {x1,phi};
    case {'psi1','psi'}
    [x1,phi,x2,psi] = cascade(h1,g1,pow2(-X));
    varargout = {x2,psi};
    case 'phi2'
    [x1,phi] = cascade(h2,g2,pow2(-X));
    varargout = {x1,phi};
    case 'psi2'
    [x1,phi,x2,psi] = cascade(h2,g2,pow2(-X));
    varargout = {x2,psi};
    case ''
    fprintf('\n%s wavelet ''%s''\n',Family,WaveletName);
    if all(abs([norm(h1{1}),norm(h2{1})] - 1) < 1e-11)
    fprintf('(orthogonal)\n');
    else
    fprintf('(biorthogonal)\n');
    end

    fprintf('Vanishing moments: %d analysis,%d reconstruction\n',...
    numvanish(g1{1}),numvanish(g2{1}));
    fprintf('Filter lengths: %d/%d-tap\n',...
    length(h1{1}),length(g1{1}));
    fprintf('Implementation lifting steps: %d\n\n',...
    size(Seq,1)-all([Seq{1,:}] == 0));

fprintf('h1(z) = %s\n', filterstr(h1,ScaleS));
fprintf('g1(z) = %s\n', filterstr(g1,ScaleS));
fprintf('h2(z) = %s\n', filterstr(h2,1/ScaleS));
fprintf('g2(z) = %s\n\n', filterstr(g2,1/ScaleD));

[x1,phi,x2,psi] = cascade(h1,g1,pow2(-X));
subplot(2,2,1);
plot(x1,phi,'b-');
if diff(x1([1,end])) > 0, xlim(x1([1,end])); end
title('\\phi_1');
subplot(2,2,3);
plot(x2,psi,'b-');
if diff(x2([1,end])) > 0, xlim(x2([1,end])); end
title('\\psi_1');
[x1,phi,x2,psi] = cascade(h2,g2,pow2(-X));
subplot(2,2,2);
plot(x1,phi,'b-');
if diff(x1([1,end])) > 0, xlim(x1([1,end])); end
title('\\phi_2');
subplot(2,2,4);
plot(x2,psi,'b-');
if diff(x2([1,end])) > 0, xlim(x2([1,end])); end
title('\\psi_2');
set(gcf,'NextPlot','replacechildren');
otherwise
error(['Invalid parameter, ''',Level,''' ]);
end
end

return;
elseif nargin < 5
    % 默认使用反对称扩展
    if nargin < 4
        if nargin < 3, error('Not enough input arguments.'); end
            Ext = 'asym';
        end

        Dim = min(find(size(X) ~= 1));
        if isempty(Dim), Dim = 1; end
    end

    if any(size(Level) ~= 1), error('Invalid decomposition level.'); end

NumStages = size(Seq,1);
EvenStages = ~rem(NumStages,2);

if Flag1D % 1D 变换
%%% 将 N 维数组转换为 2 维数组，维度
沿列的维度%%%
XSize = size(X); % 保存原始维度
N = XSize(Dim);
M = prod(XSize)/N;
Perm = [Dim: max(length(XSize),Dim),1: Dim-1];
X = double(reshape(permute(X,Perm),N,M));
if M == 1 & nargout == 0 & Level > 0
% 创建小波分解图
set(gcf,'NextPlot','replace');
subplot(Level+2,1,1);
plot(X);
title('Wavelet Decomposition');
axis tight; axis off;

X = feval(mfilename,WaveletName,Level,X,Ext,1);

for i = 1: Level
N2 = N;
N = 0.5*N;
subplot(Level+2,1,i+1);
a = max(abs(X(N+1: N2)))*1.1;
plot(N+1: N2,X(N+1: N2),'b-');
ylabel(['d',sprintf('_ %c',num2str(i))]);
axis([N+1,N2,-a,a]);
end

subplot(Level+2,1,Level+2);
plot(X(1: N),'-');
xlabel('Coefficient Index');
ylabel('s_1');
axis tight;
set(gcf,'NextPlot','replacechildren');
varargout = {X};
return;
end

if rem(N,pow2(abs(Level))) , error('Signal length must be divisible by 2^L.'); end

if N < pow2(abs(Level)), error('Signal length too small for transform level.'); end

if Level >= 0    % 正向变换
for i = 1: Level
    Xo = X(2: 2: N, : );
    Xe = X(1: 2: N, : ) +
    xfir(Seq{1,1},Seq{1,2},Xo,Ext);

    for k = 3: 2: NumStages
    Xo = Xo + xfir(Seq{k-1,1},Seq{k-1,2},Xe,Ext);
    Xe = Xe + xfir(Seq{k,1},Seq{k,2},Xo,Ext);
    end

if EvenStages
Xo = Xo + xfir(Seq{NumStages,1},Seq{NumStages,2},Xe,Ext);
end

X(1: N, : ) = [Xe*ScaleS; Xo*ScaleD];
N = 0.5*N;
end
else  % 逆变换
N = N * pow2(Level);

for i = 1: -Level
    N2 = 2*N;
    Xe = X(1: N, : )/ScaleS;
    Xo = X(N+1: N2, : )/ScaleD;
    if EvenStages

    Xo = Xo - xfir(Seq{NumStages,1},Seq{NumStages,2},Xe,Ext);
    end

    for k = NumStages - EvenStages: -2: 3
    Xe = Xe - xfir(Seq{k,1},Seq{k,2},Xo,Ext);
    Xo = Xo - xfir(Seq{k-1,1},Seq{k-1,2},Xe,Ext);
    end
    X([1: 2: N2,2: 2: N2],: ) = [Xe - xfir(Seq{1,1},Seq{1,2},Xo,Ext); Xo];
    N = N2;
end

end

X = ipermute(reshape(X,XSize(Perm)),Perm);
% 恢复原始数组维度

else % 2D 变换
N = size(X);
if length(N) > 3 | any(rem(N([1,2]),pow2(abs(Level))))
error('Input size must be either MxN or MxNxP where M and N are divisible by 2^L.');
end

if Level >= 0 % 2D 正向变换
    for i = 1: Level
        Xo = X(2: 2: N(1),1: N(2),: );
        Xe = X(1: 2: N(1),1: N(2),: ) +
        xfir(Seq{1,1},Seq{1,2},Xo,Ext);

for k = 3: 2: NumStages
    Xo = Xo + xfir(Seq{k-1,1},Seq{k-1,2},Xe,Ext);
    Xe = Xe + xfir(Seq{k,1},Seq{k,2},Xo,Ext);
end

if EvenStages
    Xo = Xo + xfir(Seq{NumStages,1},Seq{NumStages,2},Xe,Ext);
end

X(1: N(1),1: N(2),: ) = [Xe*ScaleS; Xo*ScaleD];

Xo = permute(X(1: N(1),2: 2: N(2),: ),[2,1,3]);
Xe = permute(X(1: N(1),1: 2: N(2),: ),[2,1,3])...
+ xfir(Seq{1,1},Seq{1,2},Xo,Ext);
    for k = 3: 2: NumStages
    Xo = Xo + xfir(Seq{k-1,1},Seq{k-1,2},Xe,Ext);
    Xe = Xe + xfir(Seq{k,1},Seq{k,2},Xo,Ext);
end
if EvenStages
    Xo = Xo + xfir(Seq{NumStages,1},Seq{NumStages,2},Xe,Ext);
end

    X(1: N(1),1: N(2),: ) =
    [permute(Xe,[2,1,3])*ScaleS,...
    permute(Xo,[2,1,3])*ScaleD];
N = 0.5*N;
end

else % 2D 逆变换
N = N*pow2(Level);

for i = 1: -Level
    N2 = 2*N;
    Xe = permute(X(1: N2(1),1: N(2),: ),[2,1,3])/ScaleS;
    Xo = permute(X(1: N2(1),N(2)+1: N2(2),: ),[2,1,3])/ScaleD;

if EvenStages
Xo = Xo - xfir(Seq{NumStages,1},Seq{NumStages,2},Xe,Ext);
end

for k = NumStages - EvenStages: -2: 3
Xe = Xe - xfir(Seq{k,1},Seq{k,2},Xo,Ext);
Xo = Xo - xfir(Seq{k-1,1},Seq{k-1,2},Xe,Ext);
end
X(1: N2(1),[1: 2: N2(2),2: 2: N2(2)],: ) = ...
[permute(Xe - xfir(Seq{1,1},Seq{1,2},Xo,Ext),[2,1,3]),...
permute(Xo,[2,1,3])];
Xe = X(1: N(1),1: N2(2),: )/ScaleS;
Xo = X(N(1)+1: N2(1),1: N2(2),: )/ScaleD;

if EvenStages
Xo = Xo - xfir(Seq{NumStages,1},Seq{NumStages,2},Xe,Ext);
end

for k = NumStages - EvenStages: -2: 3
Xe = Xe - xfir(Seq{k,1},Seq{k,2},Xo,Ext);
Xo = Xo - xfir(Seq{k-1,1},Seq{k-1,2},Xe,Ext);
end
X([1: 2: N2(1),2: 2: N2(1)],1: N2(2),: ) = ...
[Xe - xfir(Seq{1,1},Seq{1,2},Xo,Ext); Xo];
N = N2;
end

end

varargout{1} = X;
return;

