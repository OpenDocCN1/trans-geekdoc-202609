
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

## INDEX
### A
- ACI, see Adjacent channel interference
- A/D converter, see Analog-to-digital converter
- Additive white Gaussian noise (AWGN), 54, 60, 104
  - simulation parameters, 133
  - orthogonal frequency division multiplexing, 100
- Adjacent channel interference (ACI), 115
- Advanced Encryption Standard (AES), 1, 21–24, 77, 134
  - AddRoundKey step, 23
  - cipher key, 22
  - Galois field, 22
  - MixColumns step, 23
  - Rijndael algorithm, 21
  - rounds, 22
  - S-box, 22
  - ShiftRows step, 22
  - state, 21
  - subkey, 23, 24
- Adversary, 4, 6
- AES, see Advanced Encryption Standard
- Aliasing cancellation, 97
- AM, see Amplitude modulation
- Amplitude modulation (AM), 91
- Amplitude shift keying (ASK), 91
- Analog-to-digital (A/D) converter, 115
- ASDL, see Asymmetric digital subscriber line
- ASK, see Amplitude shift keying
- Asymmetric digital subscriber line (ASDL), 129
- Asymmetric encryption, 7
- Attack
  - brute-force, 9, 29, 49
  - chosen-ciphertext, 10
  - chosen-plaintext, 9–10
  - ciphertext-only, 9, 43
  - known-plaintext, 9
  - meet-in-the-middle, 14
  - scenarios, 3
- Authentication methods, 5
- Avalanche effect, 37, 74, 81
- AWGN, see Additive white Gaussian noise

### B
- Baker map, 31–32
  - chaotic permutation, 31
  - disadvantage, 32
  - example, 32
  - pixel image, 31
- Band-pass filters, 96
- Bit recirculation image encryption (BRIE), 30
- Black box, 9
- Block ciphers, features of, 6
- Block independency problem, 71
- Blowfish, 16
- BRIE, see Bit recirculation image encryption
- Brute-force attacks, 9, 29, 49
- Butterfly effect, 28
- chaotic key-based algorithm, 30
- characteristics of chaos, 28
- deterministicity, 29
- ergodicity of a chaotic map, 29
- Kolmogorov-flow-based image encryption technique, 30
- properties of chaotic systems, 29
- pseudo-randomness, 28
- research areas, 28
- SCAN language, 30
- subkeys, 31
- symmetric block cipher algorithm, 30
- topological transitivity, 29
- Chaotic cryptography, 1
- Chaotic image encryption with different modes of operation, 57–69
  - chaotic encryption with modes of operation, 57–58
    - block diagram, 59
    - main objective, 57
    - modes of operation, 58
    - implementation issues, 58–60
      - Baker map, 58
      - block size, 58–59
      - secondary key, 58
    - security, 59
    - XOR operations, 58
  - overview, 57
    - grayscale image, 57
    - security, 57
    - Shannon requirements, 57
  - simulation examples and discussion, 60–68
    - additive white Gaussian noise, 60
    - Baker map cryptosystem, 64
    - block sizes tested, 60
    - decrypted images, 62
    - histograms and original image and encrypted image, 66
    - noise immunity, 60, 64

### C
- Caesar cipher, 38, 39
- Carrier frequency offsets (CFOs), 103
  - compensation, 108–109, 170
  - DCT-OFDM system
    - model, 107–108
  - DWT-OFDM system
    - model, 108
  - FFT-OFDM system
    - model, 105–106
  - simulation parameters, 133
- CBC, see Cipher-block chaining
- CCDF, see Complementary CDF
- CDF, see Cumulative distribution function
- CFB, see Cipher feedback
- CFOs, see Carrier frequency offsets
- Chaos, cryptography and, 28–31
  - bit recirculation image encryption, 30
  - brute-force attacks, 29
  - butterfly effect, 28
