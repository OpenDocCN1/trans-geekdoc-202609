
for j = 1: N1
    zn1(i,j) = num2str(yy1(i,j));
end;
end;
hn1 = bin2dec(zn1);
gn1 = col2im(hn1, [M,N], [M,N], 'distinct');
%传输之间的误差 ...............................
output_image = gn1/255;

output_image1 = medfilt2(output_image);

%传输之间的误差 ...............................
MSE1 = sum(sum((double(f)/255-output_image).^2))/prod(size(f));
PSNR = 10*log(1/MSE1)/log(10)

MSE11 = sum(sum((double(f)/255-output_image1).^2))/prod(size(f));
PSNR1 = 10*log(1/MSE11)/log(10);

end

%在 DCT_OFDM 上传输 ...............................
for ebno = [0,2,4,6,8,10];

    demodata1 = zeros(ofdm_length,nloops);
    for jj = 1: nloops % 列循环
        serdata1 = input_data2(:,jj)';
        demodata = dct_channel(serdata1,para,nd,ml,gilen,fftlen,sr,ebno,br);
        demodata1(:,jj) = demodata(:); % ofdm 列的输出
    end

    %接收图像 .......................................
    [Mr,Nr] = size(demodata1);
    % demodata2 = demodata1(:);
    yy = reshape(demodata1,Mr*Nr,1);%
    part1 = yy(1: s1);
    yy11 = part1;
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%解码 ............
    yy11 = vitdec(yy11',trel,1,'term','hard');% 解码.

    yy1 = reshape(yy11,[R1,T1]);

    for i = 1: M1
        for j = 1: N1
            zn1(i,j) = num2str(yy1(i,j));
        end;
    end;
    hn1 = bin2dec(zn1);
    gn1 = col2im(hn1, [M,N], [M,N], 'distinct');
    %传输之间的误差 .........................
    output_image = gn1/255;

    output_image1 = medfilt2(output_image);

    %传输之间的误差 ..............................
    MSE1 = sum(sum((double(f)/255-output_image).^2))/prod(size(f));
    PSNR = 10*log(1/MSE1)/log(10)
    MSE11 = sum(sum((double(f)/255-output_image1).^2))/prod(size(f));
    PSNR1 = 10*log(1/MSE11)/log(10);

end

%在 DWT_OFDM 上传输 ............................
for ebno = [0,2,4,6,8,10];

    demodata1 = zeros(ofdm_length,nloops);
    for jj = 1: nloops % 列循环
        serdata1 = input_data2(:,jj)';
        demodata = dwt_channel(serdata1,para,nd,ml,gilen,fftlen,sr,ebno,br);
        demodata1(:,jj) = demodata(:); % ofdm 列的输出
    end

    %接收图像 ............................
    [Mr,Nr] = size(demodata1);
    % demodata2 = demodata1(:);
    YY = reshape(demodata1,Mr*Nr,1);%
    part1 = YY(1: s1);
    yy11 = part1;
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%解码 ...........
    yy11 = vitdec(yy11',trel,1,'term','hard');% 解码.

    yy1 = reshape(yy11,[R1,T1]);

    for i = 1: M1
        for j = 1: N1
            zn1(i,j) = num2str(yy1(i,j));
        end;
    end;
    hn1 = bin2dec(zn1);
    gn1 = col2im(hn1, [M,N], [M,N], 'distinct');
    %传输之间的误差 ...................................
    output_image = gn1/255;

    output_image1 = medfilt2(output_image);

    %传输之间的误差 ...................................
    MSE1 = sum(sum((double(f)/255-output_image).^2))/prod(size(f));
    PSNR = 10*log(1/MSE1)/log(10)
    MSE11 = sum(sum((double(f)/255-output_image1).^2))/prod(size(f));
    PSNR1 = 10*log(1/MSE11)/log(10);

end

%原始裁剪 + 压缩扩展 + AWGN ....................
%发射机 .................................................
%数据生成 ...............................................
f = imread('Cameraman.tif');
[M,N] = size(f);
g1 = im2col(f, [M,N], [M,N], 'distinct');
h1 = dec2bin(double(g1));
[M1,N1] = size(h1);
z1 = zeros(M1,N1);
for i = 1: M1
    for j = 1: N1
        z1(i,j) = str2num(h1(i,j));
    end;
end;
[R1,T1] = size(z1);
zz1 = reshape(z1,R1*T1, 1);
% 传输的数据 .......................................
zz = [zz1];

%编码 .......................................................
trel = poly2trellis(7,[171 133]);% 格
data1 = zz;
zz = convenc(data1,trel);
s1 = length(zz);
para = 128;
nd = 6; % 一个循环的信息 OFDM 符号数
ml = 2; % 调制等级：QPSK
sr = 250000; % 符号速率
br = sr.*ml; % 每载波比特率
Ipoint = 8;%过采样数
gilen = 32;
flat = 1;
fd = 600;

dctlen = para;
noc = para;
ofdm_length = para*nd*ml; % 一个循环的总数量

%将图像划分为块 ............................
nloops = ceil((length(zz))/ofdm_length);
new_data = nloops*ofdm_length;
nzeros = new_data - length(zz);
input_data = [zz;zeros(nzeros,1)];
input_data2 = reshape(input_data,ofdm_length,nloops);

%在 FFT_OFDM 上传输 ...............................
for ebno = [0,2,4,6,8,10];

    demodata1 = zeros(ofdm_length,nloops);
    for jj = 1: nloops % 列循环
        serdata1 = input_data2(:,jj)';
        demodata = fft_channel_clipping_companding(serdata1,para,nd,ml,gilen,dctlen,sr,ebno,br);
        demodata1(:,jj) = demodata(:); % ofdm 列的输出
    end

    %接收图像 .......................................
    [Mr,Nr] = size(demodata1);
    % demodata2 = demodata1(:);
    yy = reshape(demodata1,Mr*Nr,1);%
    part1 = yy(1: s1);
    yy11 = part1;

    %解码 ...................................
    yy11 = vitdec(yy11',trel,1,'term','hard');% 解码.

    yy1 = reshape(yy11,[R1,T1]);

    for i = 1: M1
        for j = 1: N1
            zn1(i,j) = num2str(yy1(i,j));
        end;
    end;
    hn1 = bin2dec(zn1);
    gn1 = col2im(hn1, [M,N], [M,N], 'distinct');
    %传输之间的误差 ...................................
    output_image = gn1/255;

    output_image1 = medfilt2(output_image);

    %传输之间的误差 ...................................
    MSE1 = sum(sum((double(f)/255-output_image).^2))/prod(size(f));
    PSNR = 10*log(1/MSE1)/log(10)

    MSE11 = sum(sum((double(f)/255-output_image1).^2))/prod(size(f));
    PSNR1 = 10*log(1/MSE11)/log(10);

end

%在 DCT_OFDM 上传输 ...................................
for ebno = [0,2,4,6,8,10];

    demodata1 = zeros(ofdm_length,nloops);
    for jj = 1: nloops % 列循环
        serdata1 = input_data2(:,jj)';
        demodata = dct_channel_clipping_companding(serdata1,para,nd,ml,gilen,dctlen,sr,ebno,br);
        demodata1(:,jj) = demodata(:); % ofdm 列的输出
    end

    %接收图像 ...................................
    [Mr,Nr] = size(demodata1);
    % demodata2 = demodata1(:);
    yy = reshape(demodata1,Mr*Nr,1);%
    part1 = yy(1: s1);
    yy11 = part1;
    %解码 ...............................................
    yy11 = vitdec(yy11',trel,1,'term','hard');% 解码.

    yy1 = reshape(yy11,[R1,T1]);
    for i = 1: M1
        for j = 1: N1
            zn1(i,j) = num2str(yy1(i,j));
        end;
    end;
    hn1 = bin2dec(zn1);
    gn1 = col2im(hn1, [M,N], [M,N], 'distinct');
    %传输之间的误差 ...............................
    output_image = gn1/255;
    output_image1 = medfilt2(output_image);

    %传输之间的误差 ...............................
    MSE1 = sum(sum((double(f)/255-output_image).^2))/prod(size(f));
    PSNR = 10*log(1/MSE1)/log(10)

    MSE11 = sum(sum((double(f)/255-output_image1).^2))/prod(size(f));
    PSNR1 = 10*log(1/MSE11)/log(10);

end

%在 DWT_OFDM 上传输 ...............................
for ebno = [0,2,4,6,8,10];

    demodata1 = zeros(ofdm_length,nloops);
    for jj = 1: nloops % 列循环
        serdata1 = input_data2(:,jj)';
        demodata = dwt_channel_clipping_companding(serdata1,para,nd,ml,gilen,dctlen,sr,ebno,br);
        demodata1(:,jj) = demodata(:); % ofdm 列的输出
    end

    %接收图像 .....
    [Mr,Nr] = size(demodata1);
    % demodata2 = demodata1(:);
    yy = reshape(demodata1,Mr*Nr,1);%
    part1 = yy(1: s1);
    yy11 = part1;
    %解码 ..................................................
    yy11 = vitdec(yy11',trel,1,'term','hard');% 解码.

    yy1 = reshape(yy11,[R1,T1]);
    for i = 1: M1
        for j = 1: N1
            zn1(i,j) = num2str(yy1(i,j));
        end;
    end;
    hn1 = bin2dec(zn1);
    gn1 = col2im(hn1, [M,N], [M,N], 'distinct');
    %传输之间的误差 .................................
    output_image = gn1/255;

    output_image1 = medfilt2(output_image);

    %传输之间的误差 .................................
    MSE1 = sum(sum((double(f)/255-output_image).^2))/prod(size(f));
    PSNR = 10*log(1/MSE1)/log(10)

    MSE11 = sum(sum((double(f)/255-output_image1).^2))/prod(size(f));
    PSNR1 = 10*log(1/MSE11)/log(10);

end

%无加密图像 + 在估计信道上裁剪 ...................................
%发射机 .......................................
%数据生成 .......................................
f = imread('Cameraman.tif');
[M,N] = size(f);
g1 = im2col(f, [M,N], [M,N], 'distinct');
h1 = dec2bin(double(g1));
[M1,N1] = size(h1);
z1 = zeros(M1,N1);
for i = 1: M1
    for j = 1: N1
