# 2.2.1 Histogram of RGB Images in MATLAB

When analyzing RGB images, it is particularly important to be able to display
the color content, characterized as the distribution of the data contained in
each of the different R, G, and B planes. The traditional way of performing
this task would be to find the histogram of each one of the planes, just as if
it were an image of intensity. However, although this process allows us to
find out important characteristics of the color distribution, it is not possible
to adequately observe this distribution so that the contents of the different
planes can be compared. Therefore, it is suggested to perform a function that
allows the histogram of the different planes to be graphed in a concatenated
manner. Program 2.1 shows the configuration of this function.

```
PROGRAM 2.1 THE PROGRAM IN MATLAB
TO PLOT THE HISTOGRAM OF THE R, G, AND
B PLANES IN AN INTERCALATED WAY

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%Function that allows graphing the histograms of
%the different planes R, G and B in a concatenated way
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
function varargout = rgbhist(I)

%It is verified that image I is
%RGB, that is, that it has 3 planes
if (size(I, 3) ~= 3)
error('The image must be RGB')
end

%256 values are set representing
%the allowable data type depth
nBins = 256;
%Find the histograms for each plane R G B
rHist = imhist(I(:, :, 1), nBins);
gHist = imhist(I(:, :, 2), nBins);
bHist = imhist(I(:, :, 3), nBins);
%the graphic object is created
figure
hold on
%Histogram information is displayed.
h(1) = stem(1:256, rHist);
h(2) = stem(1:256 + 1/3, gHist);
h(3) = stem(1:256 + 2/3, bHist);
%A color is established for each of them
%that correspond to the value they represent.
set(h(1), 'color', [1 0 0])
set(h(2), 'color', [0 1 0])
set(h(3), 'color', [0 0 1])
```