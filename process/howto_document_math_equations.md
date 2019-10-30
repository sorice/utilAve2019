## How to Document Equations in Python

This document was born when, in the spring of 2017, I was programming the *textsim* python package to calculate similarity distances between 2 string objects. My initial objective was to develop this library having in mind to include my own metrics in spicy package, but at the same time to develop the equations in a way that could be used in jupyter notebooks. As an old sphinx doc developer, and recently a Markdown document developer, I decided to study all the ways in which I had used math equations, and finally test all of them in the 2 most important formats to document my library: *RestructuredText* for sphinx & *Markdown* for jupyter notebooks.

In 2019 I check it again and many things change:
_sphinx.ext.pngmath_ was deprecated and substituted by _sphinx.ext.imgmath_. The big deal now is to add the imgmath directives in the conf.py to build the automatic documentation with this option, because needs mandatorily of latex.

Prerequisites:
```bash
apt install textlive-latex-extra
```

__Note:__ In my case the ejecution needed anyfontsize.sty which is included in this package.

### Latex Style

scipy.spatial.distance.jaccard(*u*, *v*)

This is the latex style, which is interpreted by Markdown-Typora Processor. 

```latex
\frac{c_{TF} + c_{FT}}{c_{TT} + c_{FT} + c_{TF}}
```

visualize like:

​			$\frac{c_{TF} + c_{FT}}{c_{TT} + c_{FT} + c_{TF}}$

### Special Characters in plain text Style

Pablo en Texsim

Pablo style, it consist on inserting special characters inside texts.

* Disadvantage: E.g. sums symbols doesn't fit to the equation length, must be adapted by hand.    

                                     2
        euclidean(x,y)= ⎷∑ |x - y |
                          i  i   i

### Markdown-Sphinx Style

Pandas example

Sphinx style recommendation using the tag *:math:*. 

```reStructuredText
.. math::\alpha = 1 / (1 + com)
```

### Fancy ASCII style

**Citation:** scipy.signal.lfilter

* Advantage: it can be visualized without any complexity in every text/html processor.
* Disadvantage: E.g. sums symbols doesn't fit to the equation length, must be adapted by hand.    

                             -1               -nb
                 b[0] + b[1]z  + ... + b[nb] z
         Y(z) = ---------------------------------- X(z)
                             -1               -na
                 a[0] + a[1]z  + ... + a[na] z

### sphinx.ext.pngmath Style

**Citation:** This equation comes from scipy.doc.tutorial.fftpack (line 327), is the equation for the Discrete Cosine Transforms, with normalization = 'orthogonal'.

The *pngmath* sphinx extension generates an embedded PNG with symbols adapted to length equation. See the example below. 

```reStructuredText
.. math::

    y_k = {x_0\over\sqrt{N}} + {1\over\sqrt{N}} \sum_{n=1}^{N-1} x_n \cos\left({\pi n(2k+1) \over 2N}\right) \qquad 0 \le k < N.
```

Visualize as:

​							![Sphinx Matjax Extension example](matjax_png_equation.png)

Same markdown *Tex math* expression google style (using $ character):

​								$y_k = {x_0\over\sqrt{N}} + {1\over\sqrt{N}} \sum_{n=1}^{N-1}x_n \cos({\pi n(2k+1) \over 2N}) \qquad 0 \le k < N. $




### Analysis

* You can use *\frac* instead of *\over*, but in the docstring inside source code the *\frac* tag needs two "\" to be well render by sphinx2 (sphinx3-build not tested yet). E.g. *\\\frac*. 
* Some $\LaTeX$ commands like \sqrt, \over, \sum only needs one "\" to be well render in Lyx, Typora, github, jupyter.
* Some $\LaTeX$ commands used in scipy doc are not in the standard symbol list of 2015, e.g. \qquad, which result is a long space. The same can be done with \hspace, but in my personal effort to document like scipy developers, all equations must be studied carefully.
* scipy and numpy propose sphinx *.. math::* expression. scipy, numpy, sklearn and pandas use sphinx to generate very fancy documentation, with a good information recovery feature (the "search" textbox).
* github can show directly the result of *Tex math* expressions but also PNGs.
* Notebooks can interpret *Tex math* expressions but also PNGs.
* Python consoles as ipython, ipython-qtconsole reflects ugly the *Tex math* expressions. Ipython-Qtconsole can handle PNGs, but not embedded it in a Qtconsole session.

### Conclusions

The best option is to use *Tex math* expressions simplified with *numpy function names* in corresponding cases, and brief explanations about the variables of the equation. See the example below.

$seuclidean_{distance} = np.sum(np.sqrt((A - B)^2 / V))$

*Explanation:* where $A,B$ are the $1D \space vector$ of the sentences, $and$ $V$ is the Inverse Matrix.



**Author: Abel Meneses Abad**

*Date: May 20, 2017*

