<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" lang="" xml:lang="">
<body>
<div id="a34cec53" class="cell markdown">
<h1 id="hw1"><span style="font-family: Cambria;">OpenCV Essentials</span></h1>
</div>
<div id="2c3d5026" class="cell markdown">
<h2 id="import-libraries"><span style="font-family: Cambria;">Import
Libraries</span></h2>
</div>
<div id="21638028" class="cell code" data-execution_count="1">
<div class="sourceCode" id="cb1"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb1-1"><a href="#cb1-1" aria-hidden="true" tabindex="-1"></a>pip install opencv<span class="op">-</span>python</span></code></pre></div>
</div>
<div id="9bd19eaf" class="cell code" data-execution_count="2">
<div class="sourceCode" id="cb3"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb3-1"><a href="#cb3-1" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> os</span>
<span id="cb3-2"><a href="#cb3-2" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> cv2</span>
<span id="cb3-3"><a href="#cb3-3" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> numpy <span class="im">as</span> np</span>
<span id="cb3-4"><a href="#cb3-4" aria-hidden="true" tabindex="-1"></a><span class="im">import</span> matplotlib.pyplot <span class="im">as</span> plt</span>
<span id="cb3-5"><a href="#cb3-5" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb3-6"><a href="#cb3-6" aria-hidden="true" tabindex="-1"></a><span class="im">from</span> zipfile <span class="im">import</span> ZipFile</span>
<span id="cb3-7"><a href="#cb3-7" aria-hidden="true" tabindex="-1"></a><span class="im">from</span> urllib.request <span class="im">import</span> urlretrieve</span>
<span id="cb3-8"><a href="#cb3-8" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb3-9"><a href="#cb3-9" aria-hidden="true" tabindex="-1"></a><span class="im">from</span> IPython.display <span class="im">import</span> Image</span>
<span id="cb3-10"><a href="#cb3-10" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb3-11"><a href="#cb3-11" aria-hidden="true" tabindex="-1"></a><span class="op">%</span>matplotlib inline</span></code></pre></div>
</div>
<div id="6a2abff6" class="cell code" data-execution_count="3">
<div class="sourceCode" id="cb4"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb4-1"><a href="#cb4-1" aria-hidden="true" tabindex="-1"></a>Image(filename<span class="op">=</span><span class="st">&quot;images/myimage1.jpg&quot;</span>)</span></code></pre></div>
<div class="output execute_result" data-execution_count="3">
<p><img
src="vertopal_9f5e39cf63d64de291bb761e0e20073b/96de6dfcc9d6cfbcb4d88dbfbc025e2103e6acbc.jpg" /></p>
</div>
</div>
<div id="afd1ec15" class="cell markdown">
<h2
id="reading-images-using-opencv"><span style="font-family: Cambria;">Reading
images using OpenCV</span></h2>
</div>
<div id="b53b19d9" class="cell markdown">
<h3 id="function-syntax-"><font color="green">Function Syntax
</font></h3>
<div class="sourceCode" id="cb5"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb5-1"><a href="#cb5-1" aria-hidden="true" tabindex="-1"></a>retval <span class="op">=</span> cv2.imread( filename[, flags] )</span></code></pre></div>
<p><strong>Flags</strong></p>
<ol>
<li><strong><code>cv2.IMREAD_GRAYSCALE</code></strong> or
<strong><code>0</code></strong>: Loads image in grayscale mode</li>
<li><strong><code>cv2.IMREAD_COLOR</code></strong> or
<strong><code>1</code></strong>: Loads a color image. Any transparency
of image will be neglected. It is the default flag.</li>
<li><strong><code>cv2.IMREAD_UNCHANGED</code></strong> or
<strong><code>-1</code></strong>: Loads image as such including alpha
channel.</li>
</ol>
<h3 id="opencv-documentation"><font color="green">OpenCV
Documentation</font></h3>
<ol>
<li><p><strong><code>Imread</code></strong>:
<a href="https://docs.opencv.org/4.5.1/d4/da8/group__imgcodecs.html#ga288b8b3da0892bd651fce07b3bbd3a56" target="_blank">Documentation
link</a></p></li>
<li><p><strong><code>ImreadModes</code></strong>:
<a href="https://docs.opencv.org/4.5.1/d8/d6a/group__imgcodecs__flags.html#ga61d9b0126a3e57d9277ac48327799c80" target="_blank">Documentation
link</a></p></li>
</ol>
</div>
<div id="a2488b4f" class="cell code" data-execution_count="4"
data-scrolled="true">
<div class="sourceCode" id="cb6"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb6-1"><a href="#cb6-1" aria-hidden="true" tabindex="-1"></a><span class="co"># Read image as gray scale.</span></span>
<span id="cb6-2"><a href="#cb6-2" aria-hidden="true" tabindex="-1"></a>cb_img <span class="op">=</span> cv2.imread(<span class="st">&quot;images/myimage1.jpg&quot;</span>, <span class="dv">0</span>)</span>
<span id="cb6-3"><a href="#cb6-3" aria-hidden="true" tabindex="-1"></a><span class="co"># Print the image data</span></span>
<span id="cb6-4"><a href="#cb6-4" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(cb_img)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>[[187 203 237 ... 227 233 215]
 [158 167 200 ... 217 226 197]
 [144 134 135 ... 213 224 191]
 ...
 [ 54  53  54 ...  40  40  41]
 [ 55  52  53 ...  39  39  40]
 [ 56  53  53 ...  38  39  40]]
</code></pre>
</div>
</div>
<div id="3fb63d17" class="cell code" data-execution_count="28"
data-scrolled="true">
<div class="sourceCode" id="cb8"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb8-1"><a href="#cb8-1" aria-hidden="true" tabindex="-1"></a><span class="co"># print the size  of image</span></span>
<span id="cb8-2"><a href="#cb8-2" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="st">&quot;Image size (H, W) is:&quot;</span>, cb_img.shape)</span>
<span id="cb8-3"><a href="#cb8-3" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb8-4"><a href="#cb8-4" aria-hidden="true" tabindex="-1"></a><span class="co"># print data-type of image</span></span>
<span id="cb8-5"><a href="#cb8-5" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="st">&quot;Data type of image is:&quot;</span>, cb_img.dtype)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>Image size (H, W) is: (1525, 1526)
Data type of image is: uint8
</code></pre>
</div>
</div>
<div id="1c5f9c60" class="cell markdown">
<h2
id="display-images-using-matplotlib"><span style="font-family: Cambria;">Display
Images using Matplotlib</span></h2>
</div>
<div id="ee96e338" class="cell code" data-execution_count="5"
data-scrolled="false">
<div class="sourceCode" id="cb10"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb10-1"><a href="#cb10-1" aria-hidden="true" tabindex="-1"></a>plt.imshow(cb_img, cmap<span class="op">=</span><span class="st">&quot;gray&quot;</span>)</span></code></pre></div>
<div class="output execute_result" data-execution_count="5">
<pre><code>&lt;matplotlib.image.AxesImage at 0x2e781bd7ee0&gt;</code></pre>
</div>
<div class="output display_data">
<p><img
src="vertopal_9f5e39cf63d64de291bb761e0e20073b/2b56c81f9dced51ae6c61c70c7e3199ed560ac23.png" /></p>
</div>
</div>
<div id="db141f3e" class="cell code" data-execution_count="6"
data-scrolled="false">
<div class="sourceCode" id="cb12"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb12-1"><a href="#cb12-1" aria-hidden="true" tabindex="-1"></a>plt.imshow(cb_img)</span></code></pre></div>
<div class="output execute_result" data-execution_count="6">
<pre><code>&lt;matplotlib.image.AxesImage at 0x2e7829adfa0&gt;</code></pre>
</div>
<div class="output display_data">
<p><img
src="vertopal_9f5e39cf63d64de291bb761e0e20073b/dc5681211287f947675a9205b5965d9ccd790425.png" /></p>
</div>
</div>
<div id="5e62292a" class="cell code" data-execution_count="8"
data-scrolled="false">
<div class="sourceCode" id="cb14"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb14-1"><a href="#cb14-1" aria-hidden="true" tabindex="-1"></a><span class="co"># print the size  of image</span></span>
<span id="cb14-2"><a href="#cb14-2" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="st">&quot;matrix size (H, W) is:&quot;</span>, cb_img.shape)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>matrix size (H, W) is: (1525, 1526)
</code></pre>
</div>
</div>
<div id="c6ff938e" class="cell markdown">
<h2
id="np-functions-that-are-usefull-for-calculating-with-elements-in-matrix"><span style="font-family: Cambria;">NP
functions that are usefull for calculating with elements in
matrix</span></h2>
</div>
<div id="83473cb0" class="cell markdown">
<p><span style="font-family: Cambria;"> <b>np.sum:</b>Computes the sum
of array elements over a specified axis.<br><br />
<b>np.mean:</b> Computes the arithmetic mean along the specified axis.
<br> <b>np.max:</b> Computes the maximum of array elements along a
specified axis.<br><br />
<b>np.min:</b> Computes the minimum of array elements along a specified
axis. <br> <b>np.prod:</b> Computes the product of array elements over a
specified axis. <br> <b>np.std:</b> Computes the standard deviation
along the specified axis. <br> <b>np.var:</b> Computes the variance
along the specified axis. <br> <b>np.argmax:</b> Returns the indices of
the maximum values along an axis. <br> <b>np.argmin:</b> Returns the
indices of the minimum values along an axis. <br> <b>np.median:</b>
Computes the median along the specified axis. <br> <b>np.percentile:</b>
Computes the q-th percentile of the data along the specified axis. <br>
<b>np.cumsum:</b> Computes the cumulative sum of array elements along a
specified axis. <br> <b>np.cumprod:</b> Computes the cumulative product
of array elements along a specified axis. <br> <b>np.linalg.norm:</b>
Computes the vector or matrix norm.<br> </span></p>
</div>
<div id="4fba799c" class="cell markdown">
<h2
id="calculating-avreage"><span style="font-family: Cambria;">Calculating
Avreage</span></h2>
</div>
<div id="a167c0bb" class="cell code" data-execution_count="13">
<div class="sourceCode" id="cb16"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb16-1"><a href="#cb16-1" aria-hidden="true" tabindex="-1"></a>average <span class="op">=</span> np.mean(cb_img)</span>
<span id="cb16-2"><a href="#cb16-2" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb16-3"><a href="#cb16-3" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="st">&quot;Average of matrix elements:&quot;</span>, average)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>Average of matrix elements: 91.7139703070279
</code></pre>
</div>
</div>
<div id="e29ea7a7" class="cell markdown">
<h2
id="calculating-variance"><span style="font-family: Cambria;">Calculating
Variance</span></h2>
</div>
<div id="2279ae5a" class="cell code" data-execution_count="14">
<div class="sourceCode" id="cb18"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb18-1"><a href="#cb18-1" aria-hidden="true" tabindex="-1"></a>variance <span class="op">=</span> np.var(cb_img)</span>
<span id="cb18-2"><a href="#cb18-2" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb18-3"><a href="#cb18-3" aria-hidden="true" tabindex="-1"></a><span class="bu">print</span>(<span class="st">&quot;Variance of matrix elements:&quot;</span>, variance)</span></code></pre></div>
<div class="output stream stdout">
<pre><code>Variance of matrix elements: 4259.920145633649
</code></pre>
</div>
</div>
<div id="bce54b26" class="cell markdown">
<h2 id="saving-images"><span style="font-family: Cambria;">Saving
Images</span></h2>
</div>
<div id="8a462f83" class="cell code" data-execution_count="16"
data-scrolled="false">
<div class="sourceCode" id="cb20"><pre
class="sourceCode python"><code class="sourceCode python"><span id="cb20-1"><a href="#cb20-1" aria-hidden="true" tabindex="-1"></a><span class="co"># save the image</span></span>
<span id="cb20-2"><a href="#cb20-2" aria-hidden="true" tabindex="-1"></a>cv2.imwrite(<span class="st">&quot;images/myimage1_SAVED.png&quot;</span>, cb_img )</span>
<span id="cb20-3"><a href="#cb20-3" aria-hidden="true" tabindex="-1"></a></span>
<span id="cb20-4"><a href="#cb20-4" aria-hidden="true" tabindex="-1"></a>Image(filename<span class="op">=</span><span class="st">&#39;images/myimage1_SAVED.png&#39;</span>)</span></code></pre></div>
<div class="output execute_result" data-execution_count="16">
<p><img
src="vertopal_9f5e39cf63d64de291bb761e0e20073b/41094f7ee529a1160c8b81fb66077647b4e42704.png" /></p>
</div>
</div>
<div id="2af9f90c" class="cell markdown">
<h2
id="thanks-for-your-attention-kiarash-rahmani"><span style="font-family: Cambria;">Thanks
for your attention Kiarash Rahmani</span></h2>
</div>
</body>
</html>
