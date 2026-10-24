```
```text
% may also be written as 'sym 4'. Some wavelets have
  multiple names,
% 'D1', 'Sym1', and 'Spline 1.1' are aliases of the
  Haar wavelet.
%
% WAVELET(W) displays information about wavelet W and
  plots the
% primal and dual scaling and wavelet functions.
%
% For 2D transforms, prefix W with '2D'. For example,
  '2D S+P (2,2)
% specifies a 2D (tensor) transform with the S+P
  (2,2) wavelet.
% 2D transforms require that X is either MxN or MxNxP
  where M and N
  are divisible by 2^L.
%
% WAVELET(W,L,X,EXT) specifies boundary handling EXT.
  Choices are
% 'sym' Symmetric extension (same as 'wsws')
% 'asym' Antisymmetric extension, whole-point
  antisymmetry
% 'zpd' Zero-padding
% 'per' Periodic extension
% 'sp0' Constant extrapolation
%
% Various symmetric extensions are supported:
% 'wsws' Whole-point symmetry (WS) on both boundaries
% 'hshs' Half-point symmetry (HS) on both boundaries
% 'wshs' WS left boundary, HS right boundary
% 'hsws' HS left boundary, WS right boundary
%
% Antisymmetric boundary handling is used by default,
  EXT = 'asym'.
%
% WAVELET(...,DIM) operates along dimension DIM.
%
% [H1,G1,H2,G2] = WAVELET(W,'filters') returns the
  filters
% associated with wavelet transform W. Each filter is
  represented
% by a cell array where the first cell contains an
  array of
% coefficients and the second cell contains a scalar
  of the leading
```
```