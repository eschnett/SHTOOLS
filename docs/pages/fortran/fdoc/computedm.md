---
title: ComputeDM (Fortran)
keywords: spherical harmonics software package, spherical harmonic transform, legendre functions, multitaper spectral analysis, fortran, Python, gravity, magnetic field
sidebar: fortran_sidebar
permalink: computedm.html
summary:
tags: [fortran]
toc: false
editdoc: fdoc
---

Compute the space-concentration kernel of a spherical cap.

## Usage

call ComputeDM (`dm`, `lmax`, `m`, `theta0`, `degrees`, `exitstatus`)

## Parameters

`dm` : output, real(dp), dimension (`lmax`+1, `lmax`+1)
:   The space-concentration kernel of angular order `m`.

`lmax` : input, integer(int32)
:   The spherical harmonic bandwidth of the windows.

`m` : input, integer(int32)
:   The angular order of the concentration problem.

`theta0` : input, real(dp)
:   The angular radius of the spherical cap in radians.

`degrees` : input, integer(int32), optional, dimension (`lmax`+1)
:   List of degrees to compute. If degrees(l+1) is 0, do not compute degree l of the kernel.

`exitstatus` : output, optional, integer(int32)
:   If present, instead of executing a STOP when an error is encountered, the variable exitstatus will be returned describing the error. 0 = No errors; 1 = Improper dimensions of input array; 2 = Improper bounds for input variable; 3 = Error allocating memory; 4 = File IO error.

## Description

`ComputeDM` will calculate the space-concentration kernel of angular order `m` for the spherical-cap concentration problem. The eigenfunctions of this matrix correspond to a family of orthogonal windowing functions, and the eigenvalues correspond to the window's concentration factor (i.e., the power of the window within `theta0` divided by the total power of the function). It is assumed that the employed spherical harmonic functions are normalized to the same value for all degrees and angular orders, which is the case for both the geodesy 4-pi and orthonormalized harmonics. This kernel is symmetric and is computed exactly by Gauss-Legendre quadrature. If the optional vector `degrees` is specified, then the matrix will be computed only for elements where `degrees(l+1)` is not zero.

## References

Simons, F.J., F.A. Dahlen, and M.A. Wieczorek, Spatiospectral concentration on a sphere, SIAM Review, 48, 504-536, 2006.

## See also

[computedg82](computedg82.html), [shreturntapers](shreturntapers.html), [shreturntapersm](shreturntapersm.html)
