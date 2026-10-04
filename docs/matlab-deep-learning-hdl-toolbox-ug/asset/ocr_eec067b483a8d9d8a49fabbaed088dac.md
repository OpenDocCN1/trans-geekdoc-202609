# 10 Featured Examples

```
filename = fullfile(pwd, 'ok1.png');
img = imread(filename);
img = resize(img, [he, wi]);
img = mat2ocv(img);

% Extract ROI for preprocessing
[Iori, imgPacked, bbox] = myDNNet_Preprocess(img);

% row-major > column-major conversion
imgPacked2 = zeros([128, 128, 4], 'uint8');
for c = 1:4
  for i = 1:128
    for j = 1:128
      imgPacked2(i,j,c) = imgPacked((i-1)*128 + (j-1) + (c-1)*128 + 1);
  end
end

% Classify detected objects by CNN
scores = zeros(2,4);
for i = 1:num
  [scores(:,i), speed] = HW.predict(single(imgPacked2(:,:,i)), 'Profile', 'on');
```

### Finished writing activations.
### Nun running input activations.

Deep Learning Processor Profiler Performance Results

| | LastFrameLatency(cycles) | LastFrameLatency(seconds) | Total |
|---|---|---|---|
| Network | 1754969 | 0.00798 | 1 |
| conv_1 | 271340 | 0.00123 | |
| maxpool_1 | 87533 | 0.00040 | |
| crosshorn | 125737 | 0.00057 | |
| conv_2 | 149972 | 0.00068 | |
| maxpool_2 | 19657 | 0.00009 | |
| fc_1 | 108568 | 0.00043 | |
| fc_2 | 14928 | 0.00007 |

> * The clock frequency of the DL processor is: 220MHz

```
% Iori = reshape([Iori, [1, he*wi]);
bbox = reshape(bbox, [1,16]);
scores = reshape(scores, [1, 8]);
```

```
% Insert an annotation for postprocessing
out = myDNNet_Postprocess(Iori, num, bbox, wi, he);
```

```
sz = [he wi];
out = ocv2mat(out,sz);
imshow(out)
```

10-38