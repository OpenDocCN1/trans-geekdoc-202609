
This is achieved thanks to the A component in the RGBA color scheme: it stands for the opacity or transparency of the color, allowing for color blending via the `α-compositing` algorithm [[Wiki](https://en.wikipedia.org/wiki/Alpha_compositing)]. The letter A in RGBA is named after the `α` in question, and this component is sometimes referred to as the `α` channel. The technique also allows you to easily discriminate between areas of high and low density, determined by the brightness, that is, the cumulated transparency level computed over overlapping dots. In short, it performs density estimation on its own!

For similar applications, see the “glowing plot” in [Fig. 18.5](#Chp018_361-386_B9780443218576000229.xhtml). Also see the fractal GPU-based classification technique described in Chapter [5](#Chp005_83-102_B9780443218576000096.xhtml), and its related video [here](https://mltechniques.com/2022/03/31/very-deep-neural-networks-explained-in-40-seconds/).

Finally, the data points are located on a nonperiodic orbit that over time covers a dense area, see [Fig. 4.4](#Chp004_61-82_B9780443218576000084.xhtml#f0040). So, the data points in Figs. [4.5](#Chp004_61-82_B9780443218576000084.xhtml#f0045) and [4.6](#Chp004_61-82_B9780443218576000084.xhtml#f0050) are sampled from that orbit (actually 3 orbits: red, blue, and yellow), in such a way as to be relatively equally spaced on the orbit. It is possible to obtain perfect spacing using a method similar to the reweighting technique described in Section [6.3.1](#Chp006_103-111_B9780443218576000102.xhtml). Without careful sampling, the points are distributed as in [Fig. 4.7](#Chp004_61-82_B9780443218576000084.xhtml#f0055): the point density is higher where the curvature of the orbit is more pronounced, or when closer to the related hole. It becomes lower on average as the time increases, that is, as more and more video frames are displayed.

The orbits are displayed in [Fig. 4.7](#Chp004_61-82_B9780443218576000084.xhtml#f0055). The related video can be found [here](https://www.youtube.com/watch?v=aub5am1YjIs). The added value provided by the video is that it shows how the points slowly fill a dense area over time. Also note the analogy with the comet video, where the sun plays the role of an attractor, yet comets never cross the sun (at least in the simulation). Here, the hole attached to an orbit plays the role of the sun. But a big difference is that the orbits are nonperiodic.

### Exercise 4.1

*Point classification*. A point in [Fig. 4.6](#Chp004_61-82_B9780443218576000084.xhtml#f0050) has the RGB components (155, 105, 100)![Image](images/B9780443218576000084/si33.png). What is the chance that it belongs to the red, blue, or yellow cluster?

#### Solution

Let `p[r]`, `p[b]`, `p[y]`![Image](images/B9780443218576000084/si34.png) be the probabilities in question. They satisfy

```latex
$M^{T} = \left( \begin{array}{rrr} {255\ } & {0\ } & 0 \\ {0\ } & {0\ } & 255 \\ {255\ } & {255\ } & 0 \\ \end{array} \right)^{T} \cdot \left( \begin{array}{r} p_{\text{r}} \\ p_{\text{b}} \\ p_{\text{y}} \\ \end{array} \right) = \left( \begin{array}{r} 155 \\ 105 \\ 100 \\ \end{array} \right).$
```

![Image](images/B9780443218576000084/si35.png)

The solution `p[r] = 50/255`, `p[b] = 100/255`, `p[y] = 105/255`![Image](images/B9780443218576000084/si36.png) is obtained by solving the above system. The first row in the matrix `M` corresponds to red, the second to blue, and the third to yellow RGB vectors. □

### 4.2.3.2 Six challenging problems

There are few other interesting machine learning problems worth investigating, raised by [Fig. 4.6](#Chp004_61-82_B9780443218576000084.xhtml#f0050). I summarize them in the list below.

- Problem 1: The set of yellow points seems to be bounded. Is that also true for the blue and red dots?
- Problem 2: Assuming the set of yellow points is bounded, what is the shape of its boundary?
- Problem 3: There are holes in the blue and yellow point distributions. Can we characterize these holes?
- Problem 4: On the horizontal axis, some segments have no blue dots, some have no yellow dots. Can we characterize these segments?
- Problem 5: If we continue adding points indefinitely, will the holes eventually shrink to empty sets?
- Problem 6: If we continue adding points indefinitely, will the point distributions cover dense areas?

Keep in mind that the set of points is infinite, but only a finite number of points is shown in the picture. Before going into the mathematical details, I will mention this: if you solve Problem 4, you will probably win the Fields Medal in mathematics [[Wiki](https://en.wikipedia.org/wiki/Fields_Medal)] (the equivalent of the Nobel Prize of mathematics), and a $1 million award for solving one of the seven Millennium Problems [[Wiki](https://www.claymath.org/millennium-problems/riemann-hypothesis)].

Partial solutions to the six problems are discussed in Section [4.2.3.4](#Chp004_61-82_B9780443218576000084.xhtml#s0050).

### 4.2.3.3 Mathematical background: the Riemann hypothesis

What I call data points are values of the Dirichlet eta function `η(σ + it)`![Image](images/B9780443218576000084/si37.png) [[Wiki](https://en.wikipedia.org/wiki/Dirichlet_eta_function)] computed at sampled valued of `t > 0`![Image](images/B9780443218576000084/si38.png), for `m = 3`![Image](images/B9780443218576000084/si39.png) values of `σ`, namely `σ[0] = 0.50`![Image](images/B9780443218576000084/si40.png) corresponding to the red dots, `σ[1] = 0.75`![Image](images/B9780443218576000084/si41.png) corresponding to the blue dots, and `σ[2] = 1.25`![Image](images/B9780443218576000084/si42.png) corresponding to the yellow dots. The notation `σ + it`![Image](images/B9780443218576000084/si43.png) for the complex argument is well established in number theory, and I decided to keep it. There are mathematicians interested in the problem who will read this chapter, and using a different notation would make my presentation awkward and possibly confusing to them.

The `η` function returns a complex value defined by

```latex
$\Re\lbrack\eta(\sigma + it)\rbrack = \sum\limits_{k = 1}^{\infty}{(-1)}^{k + 1} \cdot \frac{\cos(t\log k)}{k^{\sigma}},\Im\lbrack\eta(\sigma + it)\rbrack = \sum\limits_{k = 1}^{\infty}{(-1)}^{k + 1} \cdot \frac{\sin(t\log k)}{k^{\sigma}},$
```

![Image](images/B9780443218576000084/si44.png)(4.1)

where ℜ, ℑ![Image](images/B9780443218576000084/si45.png) represent respectively the real and imaginary parts. For our purpose, no knowledge of complex number theory is required. The real and imaginary parts are just the two components of a 2D vector, with the real part on the horizontal axis (X-axis), and the imaginary part on the vertical axis (Y-axis). The notations used in the Python code in Sections [4.3.2](#Chp004_61-82_B9780443218576000084.xhtml#s0070) and [4.3.3](#Chp004_61-82_B9780443218576000084.xhtml#s0075), for the real and imaginary part of the `η` function, are respectively `etax[n]` and `etay[n]`. Here `n = 0`![Image](images/B9780443218576000084/si46.png) corresponds to `σ = σ[0]`![Image](images/B9780443218576000084/si47.png), `n = 1`![Image](images/B9780443218576000084/si48.png) to `σ = σ[1]`![Image](images/B9780443218576000084/si49.png), and `n = 2`![Image](images/B9780443218576000084/si50.png) to `σ = σ[2]`![Image](images/B9780443218576000084/si51.png). The time argument `t` is a global variable in the Python code, incremented at each iteration, starting with `t = 0`![Image](images/B9780443218576000084/si8.png).
